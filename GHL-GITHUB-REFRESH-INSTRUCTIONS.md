# Activated GoHighLevel Refresh — GitHub + Zapier

The new publisher Zap is configured, published and end-to-end verified. A real Catch Hook request produced a matching GitHub publication with 54 unfinished jobs and 52 positions. Verification time: October 4, 2026, 12:18 p.m. Chicago time. The existing Markate Zaps are unchanged.

## Finish the GoHighLevel page

1. Open the existing job-dashboard page in HighLevel's builder.
2. In its existing Custom Javascript/HTML element, replace ALL old contents with ALL contents of GHL-PASTE-GITHUB-REFRESH.html. Do not append a second copy.
3. Save and publish that page.
4. Open https://go.atlasmudjacking.com/job-dashboard and press Refresh table. Allow the Zap to read the full table and publish; the page confirms only a matching request identifier.

The paste file has no embedded job snapshot and loads jobs on demand. Before the first Refresh it shows an empty map with PRESS REFRESH. No continuous background polling is used. Credentials are not embedded. Customer data is publicly readable with the owner's explicit approval.

The service path is Webhooks by Zapier Catch Hook → Code by Zapier with SDK → complete table read → public GitHub jobs.json → GoHighLevel button confirmation. GitHub's raw URL was observed returning old cached data, so the page uses the public file API with the raw JSON media type.

## Limits and errors

GitHub limits unauthenticated file API reads to 60 per hour per IP. While waiting for publication, the page checks at most once per 15 seconds for three minutes. A source error, request limit, delayed Zap or missing publication retains the last successful data and reports that fresh data was not confirmed. Public webhook acknowledgements alone do not prove a table read succeeded. The page's last good data stays only in memory.

Existing GoHighLevel page publication has not yet been verified after installing this activated file. No DNS changes, new hosting account or Render service are involved.
