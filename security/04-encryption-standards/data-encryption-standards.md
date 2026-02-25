# TrustBridge Data Encryption Standard

## 1. Purpose

This document defines encryption requirements for protecting data within the TrustBridge platform.  
The objective is to ensure confidentiality, integrity, and secure processing of digital identity and transaction information.

## 2. Scope

This standard applies to:

- Frontend applications
- Backend API services
- Supabase database
- Supabase storage buckets
- Confirmation token system
- Authentication services

## 3. Data Classification

### Public Data
- Marketing information
- Non-sensitive UI content

### Internal Data
- Application logs
- Operational metrics

### Sensitive Data
- User profiles
- Transaction records
- Trust scores

### Highly Sensitive Data
- Authentication tokens
- Confirmation links
- Secret keys
- Environment variables

## 4. Encryption in Transit

Requirements:

- All communication must use HTTPS.
- TLS 1.2 or higher required.
- HTTP connections are prohibited.
- API requests must be encrypted end-to-end.

## 5. Encryption at Rest

Requirements:

- Database encryption handled by Supabase infrastructure.
- Sensitive tokens must be hashed before storage.
- Secrets must never be stored in plaintext.

Approved Method:
- SHA256 hashing for confirmation tokens.

## 6. Approved Cryptographic Standards

| Purpose | Method |
|---|---|
| Token Signing | JWT (HS256) |
| Hashing | SHA256 |
| Random Generation | crypto.randomBytes |
| Password Security | Supabase Auth (bcrypt) |

## 7. Key Management

Security Keys must:

- Be stored in environment variables (.env)
- Never be committed to GitHub repositories
- Be accessible only by backend services
- Be rotated periodically

Restricted Keys:
- SUPABASE_SERVICE_ROLE_KEY
- JWT_SECRET


## 8. Prohibited Practices

The following are strictly prohibited:

- Hardcoding secrets in source code
- Sending secret keys to frontend applications
- Storing plaintext passwords
- Using unencrypted API endpoints

## 9. Compliance

All TrustBridge development must comply with this encryption standard before MVP deployment.
