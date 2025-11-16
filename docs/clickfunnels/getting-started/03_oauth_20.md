# OAuth 2.0 Documentation for ClickFunnels

## Overview

ClickFunnels provides OAuth 2.0 integration enabling platforms to connect customer accounts and deliver extended services. Common use cases involve e-commerce expansion, data analytics, and affiliate management.

## Setup Requirements

### Platform Application Configuration

1. Create a platform application through ClickFunnels
2. Enable the Public Applications feature for your application
3. Access `client_id` and `client_secret` credentials from the developer portal (located in Team Settings)
4. Configure your Redirect URI in the developer portal

**Key Recommendation:** Use separate platform applications for different purposes to maintain clean separation of concerns.

## Authorization Flow

### Step 1: Authorization Request

**Authorization Endpoint:**
```
https://accounts.myclickfunnels.com/oauth/authorize
```

**Full Authorization URL Example:**
```
https://accounts.myclickfunnels.com/oauth/authorize?client_id=YOUR_CLIENT_ID&grant_type=authorization_code&redirect_uri=https://your-server.com/clickfunnels/oauth_callback&response_type=code&new_installation=true
```

**Required Parameters:**
- `client_id`: Your platform application's Client ID
- `grant_type`: Must be `authorization_code`
- `redirect_uri`: Must exactly match configured URI (no trailing slashes or variations)
- `response_type`: Must be `code`
- `new_installation`: Must be `true`

**Important:** "Any slight deviation, like a trailing slash or a newline inside of ClickFunnels" will cause authorization failures. Consider URI-encoding the redirect_uri parameter.

### Step 2: User Authorization

After clicking the authorization link, users:
1. Log into ClickFunnels
2. Select their workspace
3. Review and approve permissions on the authorization consent screen
4. Get redirected to your `redirect_uri` with an authorization code

**Redirect Format:**
```
https://your-server.com/clickfunnels/oauth_callback?code=YYPnKJEvoV60yKq7I1b0gApWOnlYczPLmBpu_8oQlwY
```

## Token Exchange

### Step 3: Token Endpoint Request

**Token Endpoint:**
```
https://accounts.myclickfunnels.com/oauth/token
```

**Request Example:**
```bash
curl -X POST "https://accounts.myclickfunnels.com/oauth/token" \
  -H "Content-Type: application/json" \
  -H "User-Agent: YourAppYourOrg" \
  -d '{
    "code": "YYPnKJEvoV60yKq7I1b0gApWOnlYczPLmBpu_8oQlwY",
    "client_id": "7qRRTSF020jfLFKSJjksdfKJSDF",
    "client_secret": "M5QP32092SDLKFJkdsf0239jdDF",
    "grant_type": "authorization_code",
    "redirect_uri": "https://your-server.com/clickfunnels/oauth_callback"
  }'
```

### Successful Token Response

```json
{
  "access_token": "XXXXXYYYYYYYZZZZZZZ",
  "token_type": "Bearer",
  "expires_in": 7200,
  "scope": "admin read",
  "created_at": 1707498467,
  "team_id": 1234,
  "team_name": "John Doe's Team",
  "workspace_id": 4567,
  "workspace_name": "Clickfunneller",
  "workspace_url": "https://clickfunneller.myclickfunnels.com"
}
```

## Token Management

### Access Token Usage

- **Type:** Bearer token for API authentication
- **Scope:** "admin read" provides full workspace data access
- **Expiration:** "Tokens do not expire, so there is no refresh token system in place"
- **Prefix Requirement:** All workspace-specific API calls must use the `workspace_url` value

### Important Token Details

The `expires_in` field is informational only and does not affect actual token validity. No refresh token mechanism exists—store credentials securely for ongoing access.

## Security Considerations

1. **Client Secret Protection:** Never expose `client_secret` in client-side code
2. **Redirect URI Validation:** Ensure exact matching to prevent authorization bypass
3. **Code Exchange:** Exchange authorization codes immediately and only once
4. **Workspace Prefixing:** Use `workspace_url` for all requests to ensure "compatibility of your API calls and security updates"

## Scopes

No explicit scope specification is required. The default authorization grants comprehensive workspace access with "admin read" permissions.

---

**Source:** https://developers.myclickfunnels.com/docs/oauth-20
**Scraped:** 2025-11-16

**Note:** The provided documentation does not include refresh token processes, as tokens do not expire in this implementation. For additional integration details, see the Getting Started and SSO documentation guides.
