# TKOH Wellness

Static GitHub Pages frontend for TKOH Wellness. The deployed artifact is
allowlisted to the public homepage assets; private dashboards and clinical
fixtures are intentionally not part of this repository or deployment.

## Local preview

Serve the repository root with any static file server, for example:

```text
python -m http.server 8000
```

Then open `http://localhost:8000/`.

## Deployment

The `Deploy to GitHub Pages` workflow builds an allowlisted `_site` directory
and publishes it on pushes to `main`. The custom domain is configured by
`CNAME` (`tkoh.me`).

## Data and security boundary

This repository intentionally contains frontend-only code. The supplied
The public prototype stores only a theme preference in the browser. Sign-in,
registration, dashboard access, bookings, and private data are disabled; no
credential is accepted and no clinical fixture data is shipped. This is an
intentional security boundary, not authentication. GitHub Pages cannot run a
private API, securely validate passwords, issue protected sessions, or protect
health records. Connect the UI to a separately hosted backend before enabling
accounts, with server-side authentication, authorization, encrypted transport
and storage, secure `HttpOnly`/`Secure`/`SameSite` session cookies, audit
logging, consent, retention controls, rate limiting, backups, monitoring, and
compliance review.

The page includes a best-effort CSP and referrer policy meta tag, but GitHub
Pages does not let repository files set authoritative HTTP response headers.
For production security headers (`Content-Security-Policy`,
`X-Content-Type-Options`, `Permissions-Policy`, and frame protection), place
the site behind a proxy/CDN or use a host that supports custom headers. Inline
handlers remain in this prototype, so the CSP intentionally documents the
current boundary rather than claiming a strict production policy.

Environment files, local databases, build output, archives, and editor files
are excluded by `.gitignore`. Do not put secrets in HTML, CSS, JavaScript, or
repository configuration. Use `.env.example` only as a documentation template
for backend/deployment integrations.
