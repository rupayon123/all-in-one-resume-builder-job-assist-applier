# Privacy And Security Checklist

Use this checklist before merging features that touch resumes, job history, account storage, extension data, exports, or AI drafting.

## Sensitive Data Boundaries

- Do not commit real resumes, phone numbers, addresses, emails, API keys, service-role keys, or private job records.
- Use fake applicant data in screenshots, tests, fixtures, and issue reports.
- Keep production secrets in Vercel project settings or local `.env.local`, not in the repository.
- Redact prompt and response examples before sharing debugging output.

## Account And Storage

- Confirm Supabase row-level security is enabled for user-owned tables.
- Verify every user-owned query scopes records to the authenticated user.
- Avoid writing access tokens, refresh tokens, or service-role credentials to client storage.
- Check that demo mode cannot accidentally write into production data.

## AI Drafting

- Send the minimum resume and job text needed for the requested draft.
- Make provider configuration explicit through environment variables.
- Keep a deterministic fallback path for local demo mode.
- Avoid logging full prompts, resumes, or generated cover letters in server logs.

## Exports And Extension

- Confirm PDF and DOCX export routes validate input size and required fields.
- Confirm generated files are returned to the user without long-lived public links unless intentionally added.
- Review Chrome extension permissions before each release.
- Keep the extension app URL configurable and documented.

## Pre-Merge Checks

- Run `npm run typecheck`.
- Run `npm run test`.
- Run `npm run build`.
- Review changed files for accidental secrets or private applicant data.
- Update README or deployment docs when setup, environment variables, or privacy expectations change.
