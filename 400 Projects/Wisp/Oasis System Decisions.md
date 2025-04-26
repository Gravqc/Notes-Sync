## Why Separate Service?

- Transparency: Open source for user trust
- Security: Sensitive operations (email verification) separated from main app
- Scalability: Can be scaled independently from the frontend
- Language Performance: Go chosen for high concurrency, low memory usage

## Why Redis?

- Short-lived, fast in-memory storage
- Ideal for temporary OTP code storage with TTL (5 mins)

## Why OpenAI API for Domain Mapping?

- To get human-readable organization names from domains
- Only used once per domain, then cached in MongoDB
- Provides higher quality results compared to manual mappings

## Email Handling

- Emails sent through SMTP (configurable provider)
- No raw email logs kept
- Rate limiting recommended at load balancer/API gateway level

## Future Improvements

- Move domain mapping from local JSON to centralized MongoDB
- Encrypt sensitive traffic if separated into public cloud

## Related Docs
- [[Oasis Service Overview]]
- [[Wisp System Architecture]]
- [[Security Best Practices]]
