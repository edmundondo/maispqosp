# Changelog

All notable changes to the Malawi privileged admin backend are recorded here.
Format follows [Keep a Changelog](https://keepachangelog.com/en/1.1.0/); versioning
follows [Semantic Versioning](https://semver.org/) (MAJOR.MINOR.PATCH).

The version number shown here matches the `<meta name="app-version">` tag in
`index.html` and the `v{version}` badge in the page's footer.

## [0.2.0] — 2026-09-23

### Added
- **Pipeline health card on Overview.** Per table, for the selected site: when the last real
  public submission arrived, counts for the last 24h / 7 days, and distinct devices (7d), with a
  🟢/🟡/🔴/⚪ freshness flag. Added because a silent backend rejection (below) looked exactly like
  "no testers yet" on this dashboard.
- `supabase-antispam-migration.sql` lives in `zwispqosp` (shared project, one migration for all six sites).

### Fixed
- A panel whose backend fetch failed (e.g. an expired login → `JWT expired`) stayed on
  "Loading…" forever because the error was only logged to the console. It now shows the real
  error in the panel, with a sign-in-again hint for auth errors.
- Root cause of missing tester results, fixed in the shared database (migration
  `add_device_id_antispam_and_open_lang_codes`): the public sites send a `device_id` column that
  didn't exist, so every public insert was rejected. Also opened `translations.lang` to any
  2–4 letter code and added the per-device rate-limit trigger the demo sites' comments promised.

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
