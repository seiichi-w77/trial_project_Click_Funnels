# ClickFunnels Webhook Signature Verification Documentation

## Overview

ClickFunnels implements HMAC-based signature verification for webhook security. Both parties—ClickFunnels and your application—must share a secret to validate incoming webhook events.

## Obtaining the Webhook Secret

### Via User Interface
Navigate to **Workspace Settings > Webhooks > Webhook Endpoint** to retrieve your secret from the dashboard.

### Via API
When creating a `Webhooks::Outgoing::Endpoint`, the API response includes a `webhook_secret` field:

```json
{
  "id": 2,
  "public_id": "QqYxtu",
  "webhook_secret": "839d0d645bedefbaf76e3269d1b1141ef07683c179cc3bb0aee9348c90517a7"
}
```

**Important:** "The API only displays the `webhook_secret` once after it is created." Store this value securely as an environment variable.

## HMAC Verification Process

### Headers Required
- `X-Webhook-ClickFunnels-Signature`: The computed HMAC value
- `X-Webhook-ClickFunnels-Timestamp`: Unix timestamp of the event

### Verification Algorithm

1. **Timestamp Validation**: Verify the timestamp isn't older than 600 seconds (default tolerance)
2. **Signature Computation**: Create payload string as `"${timestamp}.${payload}"`
3. **HMAC Generation**: Calculate SHA256 HMAC using your shared secret
4. **Comparison**: Use constant-time comparison to prevent timing attacks

## Code Examples

### Ruby Implementation

```ruby
def verify(payload, signature, timestamp, secret)
  tolerance_seconds = 600
  timestamp_int = timestamp.to_i
  now = Time.now.to_i

  if (now - timestamp_int).abs > tolerance_seconds
    return false # Webhook too old or future timestamp
  end

  signature_payload = "#{timestamp}.#{payload}"
  expected_signature = OpenSSL::HMAC.hexdigest("SHA256", secret, signature_payload)

  expected_signature == signature
end
```

### Rails Controller Pattern

```ruby
class IncomingWebhooks
  def self.verify(payload, signature, timestamp, secret)
    return false if payload.blank? || signature.blank? || timestamp.blank?

    tolerance = 600
    timestamp_int = timestamp.to_i
    now = Time.now.to_i

    return false if (now - timestamp_int).abs > tolerance

    signature_payload = "#{timestamp}.#{payload}"
    expected_signature = OpenSSL::HMAC.hexdigest("SHA256", secret, signature_payload)

    # Use constant-time comparison
    ActiveSupport::SecurityUtils.secure_compare(expected_signature, signature)
  end

  def self.verify_request(request, secret)
    signature = request.headers["X-Webhook-ClickFunnels-Signature"]
    timestamp = request.headers["X-Webhook-ClickFunnels-Timestamp"]
    payload = request.raw_post

    verify(payload, signature, timestamp, secret)
  end
end
```

### Controller Filter

```ruby
before_action :verify_authenticity, only: [:create]

def verify_authenticity
  unless IncomingWebhooks.verify_request(request, ENV["CLICKFUNNELS_WEBHOOK_SECRET"])
    render json: { error: "Not found" }, status: :not_found
  end
end
```

### JavaScript (Pending)
Official JavaScript/Node.js implementation marked as "TBD" in documentation.

## Security Best Practices

1. **Environment Variables**: Store webhook secrets in secure environment variables, never hardcode
2. **Timing Attack Prevention**: Use constant-time comparison functions (e.g., `ActiveSupport::SecurityUtils.secure_compare`)
3. **Timestamp Validation**: Enforce the 600-second tolerance window
4. **Raw Payload**: Process the request body as raw string before JSON parsing
5. **Error Handling**: Respond with appropriate HTTP status codes (401/403) for verification failures

## Testing Your Implementation

1. Create a webhook endpoint in ClickFunnels
2. Send test events to [webhook.site](https://webhook.site)
3. Extract headers and payload from captured requests
4. Validate against your verification function

## Expiration and Replay Protection

The 600-second default expiration window protects against replay attacks by rejecting timestamps outside this range. This prevents attackers from intercepting and resending old webhook events.

---

**Source:** https://developers.myclickfunnels.com/docs/signature-verification
**Scraped:** 2025-11-16
