## What is Oasis?

Oasis is a standalone Go service responsible for:

- Verifying that an email domain is corporate or educational
- Sending OTP (One-Time Password) emails to users
- Verifying OTP codes during signup/login

## Major Endpoints
- `POST /verify` - Verify if domain is corporate or college
- `POST /send-otp` - Send OTP to user email
- `POST /verify-otp` - Verify user entered OTP

## Technologies Used
- Go (Golang)
- Redis (for storing short-lived OTP codes)
- SMTP (for sending email)
- Optional: OpenAI API (for mapping domain to company/college names)

## Deployment
- Runs as a separate service alongside Next.js app
- Communicates with Next.js via internal secure network (or HTTPS)

## Related Docs
- [[Wisp System Architecture]]
- [[Email Privacy Strategy]]
- [[Oasis System Decisions]]
