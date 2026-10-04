# Atlas Mudjacking dashboard

GitHub + Zapier route, with on-demand refresh for the existing GoHighLevel page.

The repository and its customer job data/history are PUBLIC with the owner's explicit authorization. jobs.json is a verified complete Zapier Tables read: 54 unfinished jobs, 52 positions at the last verified publication.

The publisher Zap is configured and end-to-end verified: Catch Hook → full Zapier table read → GitHub publication → matching public API response. The published GoHighLevel page still needs its Custom Javascript/HTML code replaced and published.

See GHL-GITHUB-REFRESH-INSTRUCTIONS.md for the exact setup. PUBLISHER-CODE.mjs belongs in a Code by Zapier JavaScript step with its SDK package enabled. Map request_id from the Catch Hook trigger. GHL-PASTE-GITHUB-REFRESH.html is the activated, paste-ready page code. Replace the existing dashboard Custom Javascript/HTML element with its entire contents and publish that page. Then press Refresh table to load current jobs.

No Render service, additional hosting account, DNS changes or modifications to existing Markate Zaps are part of this route. No credentials are embedded in this repository.
