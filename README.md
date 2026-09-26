# TKOH Wellness

Static GitHub Pages frontend for TKOH Wellness.

## Local preview

Serve the repository root with any static file server, for example:

```text
python -m http.server 8000
```

Then open `http://localhost:8000/`.

## Deployment

The `Deploy to GitHub Pages` workflow publishes the repository on pushes to
`main`. The custom domain is configured by `CNAME` (`tkoh.me`).

## Data and security boundary

This repository intentionally contains frontend-only code. The supplied
prototype stores theme and demo session state in the browser and uses mock
authentication; it must not be used to store real patient, therapist, or
credential data. GitHub Pages cannot run a private API, securely validate
passwords, or protect health records. Connect the UI to a separately hosted
backend before production use, with server-side authentication, authorization,
encryption, audit logging, consent, retention controls, and compliance review.

Environment files, local databases, build output, archives, and editor files
are excluded by `.gitignore`. Do not put secrets in HTML, CSS, JavaScript, or
repository configuration. Use `.env.example` only as a documentation template
for backend/deployment integrations.
