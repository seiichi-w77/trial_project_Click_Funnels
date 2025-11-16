# ClickFunnels SSO Documentation

## Overview

Single Sign-On (SSO) allows seamless authentication of ClickFunnels contacts via JWT tokens, enabling users created in your platform to access the ClickFunnels customer center without password authentication.

## Setup Process

### Step 1: Obtain JWT Secret Key

Access your ClickFunnels account settings and retrieve the JWT secret key from Site & Blog > Customer Center settings. This key is essential for token generation.

### Step 2: Create Contact

Establish a contact within your ClickFunnels workspace that will be authenticated through SSO.

### Step 3: Generate JWT Token

Using your preferred programming language, create a JWT token with the following payload structure:

**Required Payload Parameters:**

- `sub` (subject): Format must be `CONTACT_EMAIL:WORKSPACE_DOMAIN.myclickfunnels.com`
- `nbf` (not before): Current Unix timestamp
- `exp` (expiration): Token expiration time (Unix timestamp)
- `iat` (issued at): Current Unix timestamp

**Optional Parameter:**

- `redirect_to`: URL where users are redirected post-login (e.g., customer orders page)

### Ruby Implementation Example

```ruby
require "jwt"

customer_email = "user@example.com"
workspace_domain = "yourworkspace.myclickfunnels.com"

payload = {
  sub: "#{customer_email}:#{workspace_domain}",
  nbf: Time.now.to_i,
  exp: Time.now.to_i + 3600,
  iat: Time.now.to_i,
  redirect_to: "https://#{workspace_domain}/customers/profiles/qKOLEpy/orders"
}

jwt_secret_key = "YOUR_JWT_SECRET_KEY"
algorithm = "HS256"

jwt_token = JWT.encode(payload, jwt_secret_key, algorithm)
```

## Building the SSO URL

Construct the authentication URL using three required query parameters:

```
https://YOUR_WORKSPACE.myclickfunnels.com/sso?identifier=USER_EMAIL&strategy=email&token=JWT_TOKEN
```

**Query Parameters:**

1. **identifier**: Contact's email address (must be URL-encoded)
2. **strategy**: Static value `email`
3. **token**: Generated JWT token

### URL Encoding Requirement

Special characters in email addresses require URL encoding. For example, `user+test@clickfunnels.com` becomes `user%2Btest%40clickfunnels.com` in the identifier parameter.

## Custom Domain Considerations

⚠️ **Important**: If custom domains are configured for your workspace, "ensure you use a custom domain and not your default workspace domain" when generating SSO links. The canonical ClickFunnels domain ceases functioning for SSO purposes once custom domains are activated.

## Security Requirements

- Verify token construction matches the JWT secret stored in account settings
- Implement reasonable token expiration times (typically 3600 seconds)
- URL-encode the identifier parameter in final URLs
- Use HS256 algorithm for token generation

## Troubleshooting Steps

1. Validate token correctness using jwt.io or similar tools
2. Confirm JWT secret matches account settings
3. Verify identifier is properly URL-encoded with special characters
4. If using custom domains, ensure SSO links reference the custom domain, not the default ClickFunnels domain
5. Validate payload structure and required fields

## Workflow

Once the SSO URL is generated, share it with users via email, platform link, or other distribution methods. Users clicking the link are automatically authenticated without requiring manual login credentials.

---

**Source:** https://developers.myclickfunnels.com/docs/sso
**Scraped:** 2025-11-16
