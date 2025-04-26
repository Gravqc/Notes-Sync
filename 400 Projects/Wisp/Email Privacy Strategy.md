## Why?
- Email = PII (Personal Identifiable Information)
- Full privacy needed for Blind-style application

## Strategy
- Hash all emails using SHA-256
- Store hashed emails inside MongoDB
- Store hashed email keys in Redis for OTP with expiry time
- Lookup users by hashing incoming email first
- Never store or expose raw email after OTP flow

## OTP Handling
- Real email sent ONLY to Oasis during `/send-otp`
- Rest of the system only handles hashed emails
- Redis keys for OTP also use hashed email

## Related Docs
- [[Wisp System Architecture]]
- [[Authentication Design]]
- [[Security Best Practices]]
