# Spine Check

A single-file tool for peer-rating brand spines in a workshop. No backend, no database, no accounts. Submissions are just JSON files.

Each spine has five components: **Who, Outcome, Mechanism, Quality, Reject**. Everyone scores every spine's five components 1 to 5 — their own included — and can leave one written note per spine.

The eight spines from the August 2026 Smitten session are already committed as `spines.json`, so the plain URL loads them with nothing to type in.

## Put it online (2 minutes)

1. Create a public repo on GitHub, e.g. `spine-check`.
2. Upload `index.html` to the root.
3. Settings → Pages → Source: `Deploy from a branch` → Branch: `main`, folder: `/ (root)` → Save.
4. Wait about a minute. Your URL is `https://<your-username>.github.io/spine-check/`.

## Running the session

1. Drop the plain URL in Slack. The spines load from `spines.json` — no setup step needed.
2. Everyone opens it, picks which spine is theirs and types their name, rates all 8, hits **Finish**, then **Download my ratings**. They get a file named after their spine and themselves, like `spine-03-bjorn.json`.
3. They drop that file back in the Slack thread.
4. You open **Results** and drag the files anywhere onto the page — all eight at once is fine.

**To make the results page stand on its own**, commit those files into `subs/` instead of dragging them. Results is nothing but the charts: it watches that folder and re-renders itself about once a minute, so you can leave it on the projector and each spine fills in as its file lands. Anyone with the URL sees the same thing, and it survives a cleared browser.

Everything else — the drop zone, **Reload from repo**, **Clear all**, the code box — is tucked behind **Add files** in the status strip.

To run it with a different set of spines: go to **Set up**, type them in, then either click **Make the rating link** and send that, or click **Download spines.json** and commit that file over the existing one.

The refresh is a minute rather than a second because the unauthenticated GitHub API allows 60 requests an hour per IP, and a conditional request that comes back `304 Not Modified` still costs one against it. The page reads its remaining budget off each response and sleeps until the window resets if it gets close, so leaving the tab open all afternoon is safe. Hit **Reload from repo** if you don't want to wait for the next tick.

### Why there is a step 3

A page served from GitHub Pages is static. For a rater's browser to write straight into the repo it would need a GitHub token, and a token in a public page is both readable by everyone and auto-revoked by GitHub's secret scanning within minutes of being pushed. So the file makes one hop through Slack. Everything after that is automatic.

## What the results show

- Overall ranking by mean score across all five components, plus a **By component** view that ranks all eight spines against each other on one component at a time.
- An **Ask the results** box: type `top who`, `bottom mechanism`, `biggest disagreement`, or a spine number, and it answers.
- Per person: a score per component, the standard deviation, and a `split room` flag when raters disagree by more than 1.1.
- The weakest component across the whole room, which usually says more about the brief than about any individual.
- Every written note, anonymous by default, with a toggle to reveal who wrote what.
- CSV export of every individual rating.

## Notes

- Spines are numbered, not named, so the room rates the writing rather than the writer. The rater's own name rides along in their file, which is how the facilitator knows who has submitted and who left which note.
- A submission is plain readable JSON — name, every score, every note. Committing `subs/` to a public repo publishes all of it. Keep the room's expectations honest about that, or hold the files somewhere private and drag them in instead.
- Submissions and drafts are also cached in the browser's local storage, so a half-finished rating survives a refresh. Clearing site data wipes that; `subs/` and the CSV export are what actually persist.
- One file per spine number wins. A second file for the same number — a re-rate, a corrected name — replaces the first, whether it arrives by drop, by repo, or by code.
- The code box is still there under **Paste codes instead**, for anyone who can't upload a file.
