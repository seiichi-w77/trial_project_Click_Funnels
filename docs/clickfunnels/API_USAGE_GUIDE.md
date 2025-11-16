# ClickFunnels 2.0 API 使用ガイド

このガイドは、ClickFunnels 2.0 APIを使用するための実践的なリファレンスです。

## 📚 目次

- [クイックスタート](#クイックスタート)
- [認証](#認証)
- [基本的なAPI呼び出し](#基本的なapi呼び出し)
- [主要なユースケース](#主要なユースケース)
- [エラーハンドリング](#エラーハンドリング)
- [ベストプラクティス](#ベストプラクティス)

---

## クイックスタート

### 1. API Keyを取得

1. ClickFunnelsにログイン
2. **Teams List > Your Team > Team Settings** に移動
3. **Developer Portal** を開く
4. **Add new platform application** をクリック
5. API Access Tokenをコピー

### 2. 最初のAPI呼び出し

```bash
curl 'https://accounts.myclickfunnels.com/api/v2/teams' \
  --header 'Authorization: Bearer YOUR_API_ACCESS_TOKEN' \
  --header 'User-Agent: YourAppYourOrg'
```

---

## 認証

### 必須ヘッダー

すべてのAPI呼び出しに以下のヘッダーが必要です:

```
Authorization: Bearer YOUR_API_ACCESS_TOKEN
User-Agent: YourAppYourOrg
```

### 認証方式

#### 1. Bearer Token (API Key)
個人利用・内部統合向け

```bash
export CLICKFUNNELS_API_KEY="your_api_key_here"

curl "https://accounts.myclickfunnels.com/api/v2/teams" \
  -H "Authorization: Bearer $CLICKFUNNELS_API_KEY" \
  -H "User-Agent: MyApp"
```

#### 2. OAuth 2.0
サードパーティ統合向け

**Authorization URL:**
```
https://accounts.myclickfunnels.com/oauth/authorize?
  client_id=YOUR_CLIENT_ID&
  grant_type=authorization_code&
  redirect_uri=https://your-server.com/callback&
  response_type=code&
  new_installation=true
```

**Token Exchange:**
```bash
curl -X POST "https://accounts.myclickfunnels.com/oauth/token" \
  -H "Content-Type: application/json" \
  -H "User-Agent: MyApp" \
  -d '{
    "code": "AUTHORIZATION_CODE",
    "client_id": "YOUR_CLIENT_ID",
    "client_secret": "YOUR_CLIENT_SECRET",
    "grant_type": "authorization_code",
    "redirect_uri": "https://your-server.com/callback"
  }'
```

**Response:**
```json
{
  "access_token": "XXXXX",
  "token_type": "Bearer",
  "scope": "admin read",
  "team_id": 1234,
  "workspace_id": 4567,
  "workspace_url": "https://myworkspace.myclickfunnels.com"
}
```

**重要:** ClickFunnels OAuth tokenは**有効期限なし** (Refresh token不要)

#### 3. SSO (JWT)
Customer Center用

```ruby
require "jwt"

payload = {
  sub: "user@example.com:yourworkspace.myclickfunnels.com",
  nbf: Time.now.to_i,
  exp: Time.now.to_i + 3600,  # 1時間後
  iat: Time.now.to_i,
  redirect_to: "https://yourworkspace.myclickfunnels.com/customers/orders"
}

jwt_token = JWT.encode(payload, ENV["JWT_SECRET"], "HS256")

sso_url = "https://yourworkspace.myclickfunnels.com/sso?" +
          "identifier=#{URI.encode_www_form_component('user@example.com')}" +
          "&strategy=email" +
          "&token=#{jwt_token}"
```

---

## 基本的なAPI呼び出し

### ベースURL

- **Accounts:** `https://accounts.myclickfunnels.com/api/v2`
- **Workspace:** `https://{workspace-subdomain}.myclickfunnels.com/api/v2`

### Step 1: Teamsを取得

```bash
curl 'https://accounts.myclickfunnels.com/api/v2/teams' \
  -H 'Authorization: Bearer YOUR_TOKEN' \
  -H 'User-Agent: MyApp'
```

**Response:**
```json
[
  {
    "id": 3,
    "public_id": "JNzNaa",
    "name": "My Team"
  }
]
```

### Step 2: Workspacesを取得

```bash
curl 'https://accounts.myclickfunnels.com/api/v2/teams/3/workspaces' \
  -H 'Authorization: Bearer YOUR_TOKEN' \
  -H 'User-Agent: MyApp'
```

**Response:**
```json
[
  {
    "id": 42,
    "public_id": "ABC123",
    "team_id": 3,
    "name": "My Workspace",
    "subdomain": "myworkspace"
  }
]
```

### Step 3: Workspace Dataを取得

**重要:** Workspace dataには**workspace subdomain**を使用

```bash
curl 'https://myworkspace.myclickfunnels.com/api/v2/workspaces/42/contacts' \
  -H 'Authorization: Bearer YOUR_TOKEN' \
  -H 'User-Agent: MyApp'
```

---

## 主要なユースケース

### Contacts管理

#### Contactを作成

```bash
curl -X POST 'https://myworkspace.myclickfunnels.com/api/v2/workspaces/42/contacts' \
  -H 'Authorization: Bearer YOUR_TOKEN' \
  -H 'User-Agent: MyApp' \
  -H 'Content-Type: application/json' \
  -d '{
    "contact": {
      "email_address": "customer@example.com",
      "first_name": "John",
      "last_name": "Doe",
      "phone_number": "+1234567890"
    }
  }'
```

#### Contactsをフィルタリング

```bash
# 単一条件
curl 'https://myworkspace.myclickfunnels.com/api/v2/workspaces/42/contacts?filter[email_address]=customer@example.com' \
  -H 'Authorization: Bearer YOUR_TOKEN' \
  -H 'User-Agent: MyApp'

# 複数条件 (OR)
curl 'https://myworkspace.myclickfunnels.com/api/v2/workspaces/42/contacts?filter[email_address]=user1@example.com,user2@example.com' \
  -H 'Authorization: Bearer YOUR_TOKEN' \
  -H 'User-Agent: MyApp'

# AND条件
curl 'https://myworkspace.myclickfunnels.com/api/v2/workspaces/42/contacts?filter[email_address]=user@example.com&filter[id]=123' \
  -H 'Authorization: Bearer YOUR_TOKEN' \
  -H 'User-Agent: MyApp'
```

### Orders管理

#### Orderを作成

```bash
curl -X POST 'https://myworkspace.myclickfunnels.com/api/v2/workspaces/42/orders' \
  -H 'Authorization: Bearer YOUR_TOKEN' \
  -H 'User-Agent: MyApp' \
  -H 'Content-Type: application/json' \
  -d '{
    "order": {
      "contact_id": 33,
      "payment_processor": "external",
      "service_status": "active",
      "live_mode": false
    }
  }'
```

#### Invoiceを作成してpaid状態に

```bash
curl -X POST 'https://myworkspace.myclickfunnels.com/api/v2/orders/invoices' \
  -H 'Authorization: Bearer YOUR_TOKEN' \
  -H 'User-Agent: MyApp' \
  -H 'Content-Type: application/json' \
  -d '{
    "orders_invoice": {
      "order_id": 123,
      "status": "paid",
      "line_items": [
        {
          "variant_id": 456,
          "quantity": 1,
          "price": "99.00"
        }
      ]
    }
  }'
```

**効果:**
- Order confirmation email送信
- Course/Community/Assetへのアクセス付与
- Webhook `orders/invoice.paid` 発火

### Products管理

#### Productを作成

```bash
curl -X POST 'https://myworkspace.myclickfunnels.com/api/v2/workspaces/42/products' \
  -H 'Authorization: Bearer YOUR_TOKEN' \
  -H 'User-Agent: MyApp' \
  -H 'Content-Type: application/json' \
  -d '{
    "product": {
      "name": "Premium Course",
      "variant_properties": [
        { "name": "Tier" }
      ]
    }
  }'
```

**Response:**
```json
{
  "id": 12345,
  "name": "Premium Course",
  "default_variant_id": 67890,
  "variant_properties": [
    { "id": 100, "name": "Tier" }
  ]
}
```

#### Variantを作成

```bash
curl -X POST 'https://myworkspace.myclickfunnels.com/api/v2/products/12345/variants' \
  -H 'Authorization: Bearer YOUR_TOKEN' \
  -H 'User-Agent: MyApp' \
  -H 'Content-Type: application/json' \
  -d '{
    "products_variant": {
      "product_id": 12345,
      "properties_values": [
        { "property_id": 100, "value": "Gold" }
      ],
      "fulfillment_location_ids": [5555]
    }
  }'
```

#### Priceを作成

```bash
curl -X POST 'https://myworkspace.myclickfunnels.com/api/v2/products/prices' \
  -H 'Authorization: Bearer YOUR_TOKEN' \
  -H 'User-Agent: MyApp' \
  -H 'Content-Type: application/json' \
  -d '{
    "products_price": {
      "variant_id": 67890,
      "amount": "99.00",
      "currency": "USD",
      "duration": "one_time"
    }
  }'
```

### Webhooks

#### Webhook Endpointを作成

```bash
curl -X POST 'https://myworkspace.myclickfunnels.com/api/v2/workspaces/42/webhooks/outgoing/endpoints' \
  -H 'Authorization: Bearer YOUR_TOKEN' \
  -H 'User-Agent: MyApp' \
  -H 'Content-Type: application/json' \
  -d '{
    "webhooks_outgoing_endpoint": {
      "url": "https://your-server.com/webhooks/clickfunnels",
      "event_type_ids": [1, 5, 10]
    }
  }'
```

**Response:**
```json
{
  "id": 2,
  "public_id": "QqYxtu",
  "webhook_secret": "839d0d645bedefbaf76e3269d1b1141ef07683c179cc3bb0aee9348c90517a7",
  "url": "https://your-server.com/webhooks/clickfunnels"
}
```

**重要:** `webhook_secret`は**一度だけ表示**されます。必ず保存してください。

#### Webhook署名検証 (Ruby)

```ruby
def verify_webhook(payload, signature, timestamp, secret)
  tolerance = 600  # 10分
  now = Time.now.to_i

  return false if (now - timestamp.to_i).abs > tolerance

  signature_payload = "#{timestamp}.#{payload}"
  expected_signature = OpenSSL::HMAC.hexdigest("SHA256", secret, signature_payload)

  ActiveSupport::SecurityUtils.secure_compare(expected_signature, signature)
end

# Controllerで使用
before_action :verify_authenticity

def verify_authenticity
  signature = request.headers["X-Webhook-ClickFunnels-Signature"]
  timestamp = request.headers["X-Webhook-ClickFunnels-Timestamp"]
  payload = request.raw_post

  unless verify_webhook(payload, signature, timestamp, ENV["WEBHOOK_SECRET"])
    render json: { error: "Unauthorized" }, status: :unauthorized
  end
end
```

### Pagination

ClickFunnels APIは**カーソルベース**ページネーション (最大20件/page):

```bash
# 最初のページ
curl 'https://myworkspace.myclickfunnels.com/api/v2/workspaces/42/contacts' \
  -H 'Authorization: Bearer YOUR_TOKEN' \
  -H 'User-Agent: MyApp'

# 次のページ (last IDを使用)
curl 'https://myworkspace.myclickfunnels.com/api/v2/workspaces/42/contacts?after=55' \
  -H 'Authorization: Bearer YOUR_TOKEN' \
  -H 'User-Agent: MyApp'
```

**Response Headers:**
```
Pagination-Next: 75
Link: <https://...?after=75>; rel="next"
```

---

## エラーハンドリング

### HTTPステータスコード

| Code | Status | 意味 |
|------|--------|------|
| 200 | OK | 成功 |
| 201 | Created | リソース作成成功 |
| 204 | No Content | 成功 (レスポンスなし) |
| 400 | Bad Request | リクエスト形式エラー |
| 401 | Unauthorized | 認証エラー (Tokenが無効/不足) |
| 403 | Forbidden | 権限不足 |
| 404 | Not Found | リソースが存在しない |
| 409 | Conflict | 状態の競合 |
| 422 | Unprocessable Entity | バリデーションエラー |
| 429 | Too Many Requests | レート制限超過 |
| 5xx | Server Error | サーバーエラー (サポートに連絡) |

### エラーレスポンス例

```json
{
  "errors": [
    {
      "message": "Email address is invalid",
      "field": "email_address"
    }
  ]
}
```

### Retry Logic (Webhooks)

| Attempt | Wait Time |
|---------|-----------|
| 0 | 1秒 |
| 1 | 15秒 |
| 2 | 1分 |
| 3 | 5分 |
| 4 | 15分 |
| 5 | 1時間 |
| 6 | 12時間 |
| 7 | 24時間 |

---

## ベストプラクティス

### 1. 環境変数でCredentialsを管理

```bash
# .env
CLICKFUNNELS_API_KEY=your_api_key
CLICKFUNNELS_WEBHOOK_SECRET=your_webhook_secret
JWT_SECRET=your_jwt_secret
```

```bash
# .gitignore
.env
```

### 2. User-Agentを常に指定

```bash
# Good
-H 'User-Agent: MyApp/1.0'

# Bad (エラーになります)
# User-Agentヘッダーなし
```

### 3. Workspace SubdomainとAccounts Subdomainを区別

```bash
# Accounts subdomain - Team/Workspace management
https://accounts.myclickfunnels.com/api/v2/teams
https://accounts.myclickfunnels.com/api/v2/workspaces

# Workspace subdomain - Workspace data
https://myworkspace.myclickfunnels.com/api/v2/workspaces/42/contacts
https://myworkspace.myclickfunnels.com/api/v2/workspaces/42/orders
```

### 4. idとpublic_idを正しく使い分け

- **Request body:** `id` を使用
- **URL path:** `public_id` も使用可能

```bash
# OK
POST /api/v2/orders { "contact_id": 33 }

# NG
POST /api/v2/orders { "contact_id": "ABC123" }  # public_idはNG
```

### 5. レート制限を考慮

- 動的レート制限 (具体的な数値は非公開)
- 特別なニーズがある場合はサポートに連絡
- 429エラーが出たら exponential backoff

### 6. Webhook署名を必ず検証

```ruby
# Constant-time comparison使用
ActiveSupport::SecurityUtils.secure_compare(expected, actual)

# タイムスタンプ検証 (600秒)
(Time.now.to_i - timestamp.to_i).abs <= 600
```

### 7. Test Modeを活用

```json
{
  "order": {
    "live_mode": false  // Test order
  }
}
```

Test orderはアナリティクスに影響しません。

### 8. OAuth Redirect URIは完全一致が必須

```
# OK
https://your-server.com/callback

# NG (末尾スラッシュで失敗)
https://your-server.com/callback/
```

**推奨:** `redirect_uri`をURIエンコード

### 9. Product Workflow

```
1. Create Fulfillment Location (初回のみ)
2. Create Product → default_variant_id取得
3. (Optional) Create additional Variants
4. Create Prices (各Variantごと)
5. Create Order (variant_id使用)
```

**重要:** `variant_id` (not `product_id`) を使用

### 10. Webhook Event順序は保証されない

> "ClickFunnels webhook events can arrive out of order."

**対策:**
- `created_at` timestampで順序を判定
- Idempotent処理を実装
- 必要に応じて `Webhooks::Outgoing::Event` APIで再取得

---

## 📚 さらに詳しく

- **完全なAPI Catalog:** [API_CATALOG.md](./API_CATALOG.md)
- **Getting Started:** [getting-started/](./getting-started/)
- **REST API基礎:** [rest-api/](./rest-api/)
- **Selling:** [selling/](./selling/)
- **Webhooks:** [webhooks/](./webhooks/)
- **公式ドキュメント:** https://developers.myclickfunnels.com/docs/intro

---

**Last Updated:** 2025-11-16
**Miyabi Framework:** Autonomous Documentation System
