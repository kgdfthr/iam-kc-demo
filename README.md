This is an experimental project for exploring **IAM (Identity & Access Management) patterns**
using:

- **Traefik** (reverse proxy & routing)
- **Keycloak** (identity provider)
- **oauth2-proxy** (auth gateway that protects services using OAuth2/OIDC via Keycloak)

---

## Prerequisites

Make sure you have the following installed:

- docker
- mkcert

---

## Local DNS Setup

Add the demo domain to your `/etc/hosts` file:

```
127.0.0.1 iam-kc.demo
```

This allows Traefik to route traffic locally using hostname-based rules.

## Local TLS Certificates (mkcert)

This project uses locally trusted TLS certificates generated with mkcert.

### 1. Install the local CA
```
mkcert -install
```

### 2. Generate certificates
```
mkcert \
  -key-file configs/traefik/certs/local.key \
  -cert-file configs/traefik/certs/local.crt \
  "*.iam-kc.demo" iam-kc.demo
```

Certificates will be created at:
```
configs/traefik/certs/
├── local.crt
└── local.key
```

## Running the Project
Start all services:
```
 docker compose up -d
```
