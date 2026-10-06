# VOCAB CLASH - App identity repair (2026-10-06)

This is the complete VocabClash-App-Ready package with an identity repair.
It does not change gameplay, the 40,000-question bank, UI styling, icons, or learning storage.

## Cause

The previous ARCO and VOCAB manifests both used `"id": "./"`.
Manifest id is resolved against the ORIGIN of start_url, not the manifest directory.
On one GitHub Pages origin, both therefore identified the site root as the same app.
The old VOCAB logo-check.html incorrectly resolved id against the manifest URL and missed this collision.

## Fix

- VOCAB: `"id": "/vocab-clash"` (keep this stable in later releases).
- ARCO: `"id": "/arco"` (repair the ARCO manifest separately).
- Keep `start_url` and `scope` as `./` when the manifest lives beside index.html.
- An id is an identity, not a file to fetch. Do not create or rename folders to match it.
- The manifest link gets a new cache version. The actual icon paths remain unchanged.
- logo-check.html now uses the correct id resolution and verifies the expected identity.

## Publish and recover

1. Open BOTH original websites in the same browser profile and export available learning backups.
   Keep backups private, outside the public GitHub repositories.
2. Upload this package to the VOCAB publishing directory, replacing same-name files.
   Do not upload it into the ARCO directory. Preserve CNAME, README.md and .github settings.
3. Repair the ARCO manifest separately. A small patch for ARCO-v2.5.0-Logo-Ready is supplied.
   If the ARCO site has a newer/different manifest, edit ONLY its id to /arco instead of replacing icons/settings.
4. Wait until the hosted files are updated. Open each site's logo-check.html and check identity.
   Return to the real homepage before installing; never install the check page or local preview HTML.
5. Open edge://apps. After backups, uninstall ONLY the confused ARCO/VOCAB app entries.
   Leave the option to delete app history/site data UNCHECKED. Do not clear all site data.
6. Open the two separate published HTTPS homepages in normal Edge tabs and install them separately.
   edge://apps should contain separate entries. Verify each launches the correct website.
7. Import backups only if the saved data is absent. Keep using the same site origin/browser profile.

Updating files cannot automatically rename or remove an already-confused installed app.
If both site URLs point to the same actual homepage, separate the deployments too; distinct ids do not fix file overwrites.
No service worker, cache purge, or database migration is introduced by this patch.
Changing app id does NOT provide separate security/storage origins.

## Verification boundary

See ID-FIX-TEST-REPORT.md. No actual Microsoft Edge installation or user's public website has been verified here.
The previous APP-CHECKS.json and APP-TEST-REPORT.md are historical baseline records, not new identity verification.

## References

- https://www.w3.org/TR/appmanifest/#id-member
- https://developer.mozilla.org/en-US/docs/Web/Progressive_web_apps/Manifest/Reference/id
- https://support.microsoft.com/en-us/edge/install-manage-or-uninstall-apps-in-microsoft-edge
