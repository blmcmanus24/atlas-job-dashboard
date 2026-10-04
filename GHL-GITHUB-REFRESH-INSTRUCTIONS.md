# Prepared GoHighLevel Refresh — GitHub + Zapier only

Status: PREPARED, NOT ACTIVE. No Render service or new hosting account is used. Existing working Markate Zaps are unchanged. The repository is now PUBLIC with explicit user approval.

## Artifact

GHL-PASTE-GITHUB-REFRESH-PREPARED.html is the full Custom Javascript/HTML element replacement. It contains no customer jobs, coordinates or credentials. Its Refresh button is intentionally disabled until activation. Do not replace the current working page expecting live updates yet; this version would display no jobs until configured.

Concrete intended data address:
https://api.github.com/repos/blmcmanus24/atlas-job-dashboard/contents/jobs.json

The public file API is read with Accept: application/vnd.github.raw+json. It was verified anonymously: HTTP 200, 54 unfinished jobs and 52 positions. The repository, customer data and saved history were made public with explicit user approval. No further visibility approval or GitHub authorization is required.

The only setup blocker is the NEW publisher Zap and its Catch Hook URL. The available Zapier management actions can find or toggle existing Zaps but cannot create one.

## Publisher setup

Create one NEW publisher Zap; preserve Markate Scheduled and Completed:
1. Trigger: Webhooks by Zapier → Catch Hook. Copy its exact hook URL.
2. Code by Zapier → Run JavaScript. Enable the Zapier SDK package and the owner's GitHub connection. Paste PUBLISHER-CODE.mjs.
3. Add input field request_id mapped to the Catch Hook request_id. This connects a browser refresh request to its specific completed publication. Do not map a fixed test value in production.
4. Test in the hosted Code runtime: complete table read, GitHub write, and output commit/counts. Verify table permissions, plan runtime and webhook CORS from the GHL origin. The publisher has been verified locally with real service data, but this hosted Zap does not yet exist.
5. Publish the new Zap.
6. Anonymous JSON retrieval is already verified. Once the hosted publisher is working, generate activated markup with package-github-refresh.py --enable-public --hook VERIFIED_HOOK_URL. Reverify from the real GHL page before saying refresh is active.
7. Paste that ACTIVATED result into the existing dashboard's Custom Javascript/HTML element and publish only that page. No DNS changes are required.

## On-demand behavior

No page-load pull or continuous polling. A click POSTs a random request_id to the webhook, then checks GitHub for up to three minutes. Only a returned publicationRequestId matching that request confirms fresh table data. The API returned the real matching identifier in an authenticated-table → GitHub-public-API integration check. Raw GitHub URLs were observed returning cached data, so this code uses the public file API instead. It checks at most every 15 seconds while awaiting a publication. GitHub limits unauthenticated API requests to 60 per hour per IP; repeated refreshes or shared networks can reach that limit. No token is embedded to bypass it. GitHub caching or a Zap error can prevent confirmation; the page reports that honestly and keeps the last good data. Completed/invoiced jobs are filtered by the full-table publisher. The webhook acknowledgement alone never means a table refresh succeeded.

## Verification

Markup syntax checked. Client tests pass for disabled/no-network state and simulated trigger-to-matching-publication state. This is NOT end-to-end hosted verification. Current published GHL page remains its embedded snapshot. The new prepared artifact is intentionally disabled until the webhook URL is supplied. Local on-demand Mac dashboard remains usable.

References:
https://help.zapier.com/hc/en-us/articles/8496288690317-Trigger-Zap-workflows-from-webhooks
https://help.zapier.com/hc/en-us/articles/44955499643917-Use-the-Zapier-SDK-in-Code-steps
https://help.zapier.com/hc/en-us/articles/19103331339789-Share-and-embed-Zapier-Forms-pages
https://docs.github.com/en/apps/oauth-apps/building-oauth-apps/authorizing-oauth-apps
