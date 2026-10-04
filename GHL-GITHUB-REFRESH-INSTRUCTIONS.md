# Prepared GoHighLevel Refresh — GitHub + Zapier only

Status: PREPARED, NOT ACTIVE. No Render service or new hosting account is used. Existing working Markate Zaps and the private repository are unchanged in visibility.

## Artifact

GHL-PASTE-GITHUB-REFRESH-PREPARED.html is the full Custom Javascript/HTML element replacement. It contains no customer jobs, coordinates or credentials. Its Refresh button is intentionally disabled until activation. Do not replace the current working page expecting live updates yet; this version would display no jobs until configured.

Concrete intended data address:
https://raw.githubusercontent.com/blmcmanus24/atlas-job-dashboard/main/jobs.json

That address currently cannot be read anonymously because its repository is PRIVATE. The file name and Zapier connection ID do not grant access.

## Exact approval needed for this route

To use this address with the ordinary public GoHighLevel page, approve making blmcmanus24/atlas-job-dashboard publicly readable. This exposes customer job data, saved snapshots, address/coordinate source material, and repository history—not merely the latest jobs.json. No visibility change has been made. Alternative public delivery repositories are not created or assumed authorized.

If customer data must stay private, this prepared route cannot be activated as-is. Zapier's supported private alternative is a separately opened managed-user Forms table/kanban; restricted Forms cannot be embedded and do not provide this custom map runtime. The already-working local map is another private option.

## Publisher setup after approval

Create one NEW publisher Zap; preserve Markate Scheduled and Completed:
1. Trigger: Webhooks by Zapier → Catch Hook. Copy its exact hook URL.
2. Code by Zapier → Run JavaScript. Enable the Zapier SDK package and the owner's GitHub connection. Paste PUBLISHER-CODE.mjs.
3. Add input field request_id mapped to the Catch Hook request_id. This connects a browser refresh request to its specific completed publication. Do not map a fixed test value in production.
4. Test in the hosted Code runtime: complete table read, GitHub write, and output commit/counts. Verify table permissions, plan runtime and webhook CORS from the GHL origin. The publisher has been verified locally with real service data, but this hosted Zap does not yet exist.
5. Publish the new Zap.
6. After public visibility is authorized and anonymous JSON retrieval succeeds, generate activated markup with package-github-refresh.py --enable-public --hook VERIFIED_HOOK_URL. Reverify from the real GHL page before saying refresh is active.
7. Paste that ACTIVATED result into the existing dashboard's Custom Javascript/HTML element and publish only that page. No DNS changes are required.

## On-demand behavior

No page-load pull or continuous polling. A click POSTs a random request_id to the webhook, then checks GitHub for up to three minutes. Only a returned publicationRequestId matching that request confirms fresh table data. GitHub caching or a Zap error can prevent confirmation; the page reports that honestly and keeps the last good data. Completed/invoiced jobs are filtered by the full-table publisher. The webhook acknowledgement alone never means a table refresh succeeded.

## Verification

Markup syntax checked. Client tests pass for disabled/no-network state and simulated trigger-to-matching-publication state. This is NOT end-to-end hosted verification. Current published GHL page remains its embedded snapshot. Local on-demand Mac dashboard remains usable.

References:
https://help.zapier.com/hc/en-us/articles/8496288690317-Trigger-Zap-workflows-from-webhooks
https://help.zapier.com/hc/en-us/articles/44955499643917-Use-the-Zapier-SDK-in-Code-steps
https://help.zapier.com/hc/en-us/articles/19103331339789-Share-and-embed-Zapier-Forms-pages
https://docs.github.com/en/apps/oauth-apps/building-oauth-apps/authorizing-oauth-apps
