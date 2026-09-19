# Changelog

All notable changes to the Malawi privileged admin backend are recorded here.
Format follows [Keep a Changelog](https://keepachangelog.com/en/1.1.0/); versioning
follows [Semantic Versioning](https://semver.org/) (MAJOR.MINOR.PATCH).

The version number shown here matches the `<meta name="app-version">` tag in
`index.html` and the `v{version}` badge in the page's footer.

## [0.1.0] — 2026-09-18

### Added
- First build for Malawi: the same admin app as zwispqosp v0.6.1 (Supabase Auth +
  RLS with role-scoped read/write via `has_write_access(site)`/`is_admin()`,
  Google sign-in, passkeys, RBAC role badge + break-glass toggle, provider
  analytics, ISP licensing CRM, moderation, translation review, drill-down
  Explorer, inline benchmark report, all six formatted exports), defaulting to
  `currentSite = "mw"`.
- Connects to the same shared Supabase project as zwispqosp/bwispqosp/saispqosp/
  zaispqosp/moispqosp (multi-tenant via the `site` column) — no separate database
  or migration for this repo; see zwispqosp's SETUP.md/SCHEMA.md for the backend
  itself.
- `PROVIDER_DIRECTORY.mw`, `SITE_LABELS.mw` and `MISSING_LANGS.mw` populated (this
  was also added to zwispqosp, bwispqosp, saispqosp, zaispqosp and moispqosp in the
  same change, so all six admin app copies stay in sync) — needed since Supabase
  only has the report tables, not a `providers` table.
- Brand footer/logo matching zwispqosd/zwispqosp from day one.
