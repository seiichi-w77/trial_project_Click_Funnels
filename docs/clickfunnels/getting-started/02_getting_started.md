# ClickFunnels 2.0 API Getting Started Guide

## Prerequisites

- Active ClickFunnels team account with admin access
- Secure storage capability for API credentials

## Setup Steps

### 1. Create a Platform Application

Navigate to your team settings via the main dashboard:
- Select **Teams List > Your Team > Team Settings**
- Go to **Developer Portal**
- Click **Add new platform application**
- Complete the required information fields
- Click **Create platform application**

You can maintain multiple platform applications for different use cases, such as periodic API polling or OAuth-based user integrations.

### 2. Obtain Your API Access Token

After creating your platform application, copy the API access token from the Developer Portal. Multiple access tokens per application allow you to distribute different keys to team members securely.

⚠️ **Security Note:** "API access tokens can be seen by all team admins" and should be stored securely. Avoid public exposure and consider sharing via secure methods like One Time Secret when necessary.

## Authentication Process

### Required Headers

All API requests require two headers:

```
Authorization: Bearer YOUR_API_ACCESS_TOKEN
User-Agent: YourAppYourOrg
```

The User-Agent header with a distinct identifier is mandatory per security rules.

## First API Call Examples

### Step 1: Retrieve Team Information

**Endpoint:** `https://accounts.myclickfunnels.com/api/v2/teams`

```bash
curl 'https://accounts.myclickfunnels.com/api/v2/teams' \
  --header 'Authorization: Bearer VZeIl6IkzMQCdfSBQdvjSb7-KLllCKrE390QMKcmC6M' \
  --header 'User-Agent: YourAppYourOrg'
```

**Response Example:**
```json
[
  {
    "id": 3,
    "public_id": "JNzNaa",
    "name": "Team Name"
  }
]
```

### Step 2: List Workspaces

**Endpoint:** `https://accounts.myclickfunnels.com/api/v2/teams/{team_id}/workspaces`

```bash
curl 'https://accounts.myclickfunnels.com/api/v2/teams/3/workspaces' \
  --header 'Authorization: Bearer VZeIl6IkzMQCdfSBQdvjSb7-KLllCKrE390QMKcmC6M' \
  --header 'User-Agent: YourAppYourOrg'
```

**Response Example:**
```json
[
  {
    "id": 42,
    "public_id": "workspace_public_id",
    "team_id": 3,
    "name": "Workspace Name"
  }
]
```

### Step 3: Query Workspace Data

**Endpoint:** `https://{workspace_subdomain}.myclickfunnels.com/api/v2/workspaces/{workspace_id}/contacts`

```bash
curl 'https://workspacesubdomain.myclickfunnels.com/api/v2/workspaces/42/contacts' \
  --header 'Authorization: Bearer VZeIl6IkzMQCdfSBQdvjSb7-KLllCKrE390QMKcmC6M' \
  --header 'User-Agent: YourAppYourOrg'
```

**Response Example:**
```json
[
  {
    "id": 33,
    "email": "contact@example.com"
  }
]
```

## Key IDs to Gather

Extract these identifiers from your ClickFunnels UI or API responses:

| ID Type | Source |
|---------|--------|
| **Team ID** | Team settings URL: `accounts.myclickfunnels.com/account/teams/{TEAM_ID}` |
| **Workspace ID** | Workspace dashboard: `{subdomain}.myclickfunnels.com/account/workspaces/{WORKSPACE_ID}` |
| **Workspace Subdomain** | Found in workspace dashboard URL |
| **Resource IDs** | Returned in API responses; use raw `id` fields for POST payloads (avoid `public_id`) |

## Important Distinctions

- Use the **accounts subdomain** for non-workspace-specific calls (teams, workspaces)
- Use the **workspace subdomain** for workspace data operations
- Use raw `id` values in request bodies; `public_id` works only in URLs

## Next Steps

- Explore the [API Reference](https://cf2.readme.io/reference) documentation
- Review endpoint-specific guides: Teams, Authentication, Rate Limiting, and more
- Visit the [Discussion Forum](https://cf2.readme.io/discuss) for community support

---

**Source:** https://developers.myclickfunnels.com/docs/getting-started
**Scraped:** 2025-11-16
