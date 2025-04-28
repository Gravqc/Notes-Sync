## Flow
1. User enters email ➔ Verify domain (Oasis)
2. Send OTP to email ➔ Oasis sends
3. Verify OTP ➔ Create user (if new)
4. Set password
5. Successful login ➔ Issue JWT session cookie

## Session Management
- JWT signed with server secret
- JWT stored inside HttpOnly, Secure, SameSite cookie
- Token contains:
  - hashedEmail
  - domain
  - orgType
  - isVerified
- No raw email exposed anywhere in backend or frontend after OTP verification

## Related Docs
- [[Wisp System Architecture]]
- [[Email Privacy Strategy]]
