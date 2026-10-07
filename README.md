# SentinelAuth API Documentation

Welcome to the official developer documentation repository for **[SentinelAuth](https://sentinelauth.com.au)** — Australia's developer-first Two-Factor Authentication (2FA), Multi-Factor Authentication (MFA), SMS OTP, Email Verification, and TOTP Authenticator platform.

[![Interactive Docs](https://img.shields.io/badge/interactive_docs-sentinelauth.com.au%2Fdocs-purple)](https://sentinelauth.com.au/docs/)
[![OpenAPI 3.0](https://img.shields.io/badge/OpenAPI-3.0.3-green.svg)](./openapi.yaml)
[![Website](https://img.shields.io/badge/website-sentinelauth.com.au-blue)](https://sentinelauth.com.au)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

---

## Interactive Documentation & Sandbox

- **Live Interactive Docs:** [https://sentinelauth.com.au/docs/](https://sentinelauth.com.au/docs/)
- **Live In-Browser API Test Sandbox:** [https://sentinelauth.com.au/dashboard/test-api/](https://sentinelauth.com.au/dashboard/test-api/)
- **Developer API Keys:** [https://sentinelauth.com.au/dashboard/api-keys/](https://sentinelauth.com.au/dashboard/api-keys/)

---

## API Specification

This repository contains the full **OpenAPI 3.0 specification** for the SentinelAuth platform:
- **[`openapi.yaml`](./openapi.yaml)** — Standard OpenAPI specification file compatible with Swagger UI, Postman, Insomnia, and code generators.

---

## Authentication

All requests to SentinelAuth endpoints must include your secret API key in the `Authorization` header:

```http
Authorization: Bearer sk_live_your_api_key_here
Content-Type: application/json
```

---

## Primary Endpoints

### 1. Send OTP (`POST /send-otp`)
Dispatches a 6-digit one-time password via carrier SMS or high-deliverability Email.

```bash
curl -X POST https://sentinelauth.com.au/wp-json/sentinelauth/v1/send-otp \
  -H "Authorization: Bearer YOUR_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "to": "+61412345678",
    "channel": "sms",
    "app_name": "MyCompany"
  }'
```

### 2. Verify OTP (`POST /verify-otp`)
Validates the user-submitted code against the active verification session.

```bash
curl -X POST https://sentinelauth.com.au/wp-json/sentinelauth/v1/verify-otp \
  -H "Authorization: Bearer YOUR_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "verification_id": "ver_sms_...",
    "code": "123456"
  }'
```

### 3. TOTP Factor Enrollment (`POST /totp/enroll`)
Generates an authenticator factor with QR code for Google Authenticator, Microsoft Authenticator, or Authy.

### 4. TOTP Factor Verification (`POST /totp/verify`)
Verifies the rolling 6-digit code generated on the user's mobile authenticator app.

### 5. Account Quota Telemetry (`GET /quota`)
Returns active plan quotas and monthly remaining requests.

---

## Official SDKs & Client Libraries

- **Node.js SDK:** [`github.com/SentinelAuth12/sentinelauth-node-sdk`](https://github.com/SentinelAuth12/sentinelauth-node-sdk)
- **Python SDK:** [`github.com/SentinelAuth12/sentinelauth-python-sdk`](https://github.com/SentinelAuth12/sentinelauth-python-sdk)
- **Integration Examples:** [`github.com/SentinelAuth12/sentinelauth-examples`](https://github.com/SentinelAuth12/sentinelauth-examples)

---

## Support & Security

- **Security & Privacy:** [https://sentinelauth.com.au/privacy-policy/](https://sentinelauth.com.au/privacy-policy/)
- **Contact:** [support@sentinelauth.com.au](mailto:support@sentinelauth.com.au)
- **Report Security Vulnerabilities:** Please email security reports directly to [support@sentinelauth.com.au](mailto:support@sentinelauth.com.au).
