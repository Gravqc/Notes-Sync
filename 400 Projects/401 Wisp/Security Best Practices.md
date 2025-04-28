## General
- HTTPS enforced for all communication
- JWT tokens inside HttpOnly cookies
- Never expose raw email outside /send-otp flow

## Database
- Emails hashed before storage
- Sensitive user fields hidden via DTO mapping
- Minimal JWT payload (no sensitive data)

## Redis
- OTP stored under hashed email keys
- Short TTL for OTPs (~5 mins)
- No raw email keys in Redis

## Related Docs
- [[Wisp System Architecture]]
- [[Email Privacy Strategy]]
- [[Authentication Design]]
