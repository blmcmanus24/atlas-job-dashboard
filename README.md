# Atlas Mudjacking job dashboard

Private repository for the dashboard's Zapier-to-GitHub publisher. jobs.json is a complete table read, not a single event's job.

## Current status

An initial table read has been published through Zapier's authenticated GitHub connection. Automatic updates are not yet active. The existing GoHighLevel dashboard still shows its embedded snapshot.

## Cloud publisher

Create a separate Zap, keeping the existing Markate Scheduled and Completed Zaps:

1. Trigger: Zapier Tables → New or Updated Record, table unfinished_jobs_map.
2. Action: Code by Zapier → Run JavaScript. Enable the @zapier/zapier-sdk package. Select the owner's GitHub connection and any table permissions requested by the editor.
3. Paste PUBLISHER-CODE.mjs, preserving its SDK import and exported main function. It reads every page of the table, then publishes jobs.json through the GitHub connection. No token should be pasted into the code.
4. Run Code in the hosted editor and verify the resulting commit, counts and table-read timestamp. Test a completion and an address change before enabling the Zap.
5. Add a separate reconciliation Zap using a supported scheduled interval and the same Code action. This is needed for deletion events, missed triggers and recovery. Confirm plan runtime/task limits. The publisher is safe to overlap: it reads the GitHub SHA before reading the table and retries the full read on a conflict.

The SDK is currently in beta. Local authenticated execution verifies both table retrieval and GitHub publication, but does not establish hosted Code runtime permissions or activate a Zap.

## Public page data delivery

This repository is private, and the connected GitHub account has the Free plan. GitHub Pages requires a paid plan for private source repositories. Anonymous requests cannot retrieve jobs.json directly from a private repository. Do not put a GitHub token in the dashboard.

Before configuring GHL-PASTE-CONNECTED.html, choose an authorized serving route: a cloud reader with server-side credentials, or explicitly approve a public data-serving repository (including customer data and its history). Neither route is configured here. No DNS change is required for the existing GoHighLevel page at https://go.atlasmudjacking.com/job-dashboard.

## Data behavior

Newest edited record wins per work order. Completed, invoiced, paid and cancelled work is excluded. Zero-dollar warranty work is preserved. Coordinates are used only when the address matches the verified coordinate cache; changed/new addresses remain unpositioned.

## References

https://help.zapier.com/hc/en-us/articles/44955499643917-Use-the-Zapier-SDK-in-Code-steps
https://docs.github.com/en/pages/getting-started-with-github-pages/what-is-github-pages
