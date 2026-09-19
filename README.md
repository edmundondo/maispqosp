# maispqosp

Private backend for the Malawi ISP Tracker (public site: maispqosd, live at
edmundondo.github.io/maispqosd).

This is the same admin app as [zwispqosp](https://github.com/edmundondo/zwispqosp),
pointed at the `mw` site by default — one shared Supabase project serves Zimbabwe,
Botswana, South Africa, Zambia, Mozambique and Malawi via a `site` column, so there
is no separate database or migration to run here. See `zwispqosp`'s SCHEMA.md and
SETUP.md for the full table breakdown, RLS policy notes and backend setup steps;
none of that is Malawi-specific. Actual Supabase credentials live only in the
Supabase dashboard — never in this repo.

Contains all six formatted export options (PDF report, ISP/QoS/Status/Speed CSV,
EPUB) for whichever site is selected in the app, gated by Supabase Auth + RLS via
role-scoped access (`has_write_access(site)` for writes, `is_admin()` for read),
not a hardcoded service-role key.

See `CHANGELOG.md` for version history.
