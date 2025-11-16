# ClickFunnels サポートマニュアル全集

ClickFunnels公式サポートサイト (https://support.myclickfunnels.com/) から245記事を完全スクレイピングしたドキュメント集です。

## 📚 収録内容

**全245記事** - ClickFunnelsのあらゆる機能を網羅

### 主要カテゴリー

1. **Getting Started (入門)**
   - ClickFunnels概要
   - チーム・ワークスペース管理
   - 初期セットアップ

2. **Funnels (ファネル)**
   - ファネル作成・管理
   - ステップ追加・編集
   - A/Bスプリットテスト
   - アナリティクス

3. **Products (製品)**
   - 製品作成・管理
   - 在庫管理
   - サブスクリプション設定

4. **Payments (決済)**
   - Payments AI
   - Stripe連携
   - PayPal連携
   - NMI決済ゲートウェイ
   - テストモード・サンドボックス

5. **Email (メール)**
   - メールエディタ
   - メールテンプレート
   - ブロードキャスト
   - システムメール

6. **Domains (ドメイン)**
   - ドメイン接続（自動・手動）
   - サブドメイン設定
   - DNSプロバイダー対応

7. **Site (サイト)**
   - Webサイト構築
   - ページエディタ
   - ランディングページ

8. **Store (ストア)**
   - ストアフロント作成
   - カート・チェックアウトカスタマイズ
   - コレクション管理
   - アップセル設定

9. **Courses (コース)**
   - コース作成
   - モジュール・レッスン管理
   - 修了証明書
   - コースメール自動化

10. **Affiliate Center (アフィリエイト)**
    - アフィリエイトプログラム設定
    - コミッション管理
    - Tier 1/2コミッション

11. **Workflows & Automation (ワークフロー・自動化)**
    - ワークフロー作成
    - クイックアクション
    - Survey Workflows

12. **Appointments (予約)**
    - 予約カレンダー
    - イベントタイプ設定
    - カレンダー連携

13. **Community (コミュニティ)**
    - コミュニティ作成
    - グループ・トピック管理
    - モデレーションツール

14. **Opportunities (営業機会)**
    - パイプライン管理
    - ステージ管理
    - 営業機会追跡

15. **MessageHub (メッセージハブ)**
    - チャットアプリケーション
    - インボックス管理
    - チャット設定

16. **Analytics (分析)**
    - ライブビュー
    - レポート
    - ファネルアナリティクス

17. **Customers & Contacts (顧客・コンタクト)**
    - コンタクト管理
    - カスタマーセンター
    - タグ管理

18. **Discounts (割引)**
    - クーポン作成
    - 割引適用
    - サブスクリプション割引

19. **Shipping (配送)**
    - 配送設定

20. **Tax (税金)**
    - 消費税・VAT・GST設定

21. **Short Links (短縮リンク)**
    - 短縮URL作成・管理

22. **Workspace Settings (ワークスペース設定)**
    - 通貨設定
    - 決済ゲートウェイ設定
    - チームメンバー管理

23. **Integrations (連携)**
    - サードパーティアプリ連携
    - Webhooks
    - Voomlyビデオ連携

24. **Advanced Features (高度な機能)**
    - カスタムコード
    - Frameworks
    - Conversion Boosters
    - Countdown Funnels

## 🔍 使い方

### ファイル命名規則

各記事は元のURLパスに基づいて命名されています：

```
https://support.myclickfunnels.com/docs/getting-started-with-clickfunnels
  ↓
getting-started-with-clickfunnels.md
```

### ファイル構造

各Markdownファイルは以下の構造になっています：

```markdown
# [記事タイトル]

**Source:** [元のURL]

---

[記事本文]
```

### 検索方法

**方法1: ファイル名で検索**
```bash
ls docs/clickfunnels-support/ | grep "funnel"
```

**方法2: 内容で検索**
```bash
grep -r "Stripe" docs/clickfunnels-support/
```

**方法3: Claudeに質問**
```
docs/clickfunnels-support/ 内でドメイン接続の方法を教えてください
```

## 📊 統計情報

- **総記事数**: 245記事
- **スクレイピング日時**: 2025年11月16日
- **ソース**: https://support.myclickfunnels.com/
- **形式**: Markdown (.md)
- **エンコーディング**: UTF-8

## 🛠️ スクレイピング方法

Playwright + Chromiumを使用してJavaScriptレンダリング後のコンテンツを取得：

```python
from playwright.sync_api import sync_playwright
import json
import os
import re
import time

# 全URLを読み込み
with open('/tmp/all_support_urls.json', 'r') as f:
    urls = json.load(f)

# Playwright起動
with sync_playwright() as p:
    browser = p.chromium.launch(headless=True)
    page = browser.new_page()

    for url in urls:
        # ページ読み込み
        page.goto(url, wait_until="load", timeout=30000)
        time.sleep(1)

        # タイトル抽出
        title_elem = page.query_selector('h1, .article-title, [class*="title"]')
        title = title_elem.inner_text() if title_elem else url.split('/')[-1]

        # コンテンツ抽出
        content_elem = page.query_selector('article, .article-body, .content, main')
        content = content_elem.inner_text() if content_elem else page.inner_text('body')

        # Markdown保存
        filename = sanitize_filename(url)
        filepath = f'/tmp/clickfunnels_support/{filename}'

        with open(filepath, 'w', encoding='utf-8') as f:
            f.write(f"# {title}\n\n")
            f.write(f"**Source:** {url}\n\n")
            f.write(f"---\n\n")
            f.write(content)

    browser.close()
```

## 📖 関連ドキュメント

- [ClickFunnels API ドキュメント](../clickfunnels/) - API統合ガイド
- [API カタログ](../clickfunnels/API_CATALOG.md) - 全エンドポイント一覧
- [API 使用ガイド](../clickfunnels/API_USAGE_GUIDE.md) - 実践的な使い方

## 🔗 公式リソース

- **公式サポートサイト**: https://support.myclickfunnels.com/
- **ClickFunnels**: https://www.clickfunnels.com/
- **API開発者向けドキュメント**: https://developers.myclickfunnels.com/

## ⚠️ 注意事項

- この資料は2025年11月16日時点の情報です
- 最新情報は公式サポートサイトをご確認ください
- 商用利用時はClickFunnelsの利用規約をご確認ください

---

**スクレイピング実施**: Miyabi Framework - Issue #28
**実行環境**: Playwright 1.x + Chromium + Python 3.9
**プロジェクト**: trial_project_Click_Funnels
