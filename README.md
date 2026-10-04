# Atlas Mudjacking dashboard

GitHub + Zapier route, with on-demand refresh for the existing GoHighLevel page.

The repository and its customer job data/history are PUBLIC with the owner's explicit authorization. jobs.json is a verified complete Zapier Tables read: 54 unfinished jobs, 52 positions at the last verified publication.

Current state: the repository is readable, but the new publisher Zap has not yet been created. On-demand source refresh is NOT active on the published GoHighLevel page.

See GHL-GITHUB-REFRESH-INSTRUCTIONS.md for the exact setup. PUBLISHER-CODE.mjs belongs in a Code by Zapier JavaScript step with its SDK package enabled. Map request_id from the Catch Hook trigger. GHL-PASTE-GITHUB-REFRESH-PREPARED.html is deliberately disabled until that hook URL is configured and the actual refresh handshake is verified. Do not paste it expecting a live Refresh button yet.

No Render service, additional hosting account, DNS changes or modifications to existing Markate Zaps are part of this route. No credentials are embedded in this repository.
