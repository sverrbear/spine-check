# Spine Check

A single-file tool for peer-rating brand spines in a workshop. No backend, no accounts, no data leaves anyone's browser.

Each spine has five components: **Who, Outcome, Mechanism, Quality, Reject**. Everyone scores every spine's five components 1 to 5 — their own included — and can leave one written note per spine.

The eight spines from the August 2026 Smitten session are already committed as `spines.json`, so the plain URL loads them with nothing to type in.

## Put it online (2 minutes)

1. Create a public repo on GitHub, e.g. `spine-check`.
2. Upload `index.html` to the root.
3. Settings → Pages → Source: `Deploy from a branch` → Branch: `main`, folder: `/ (root)` → Save.
4. Wait about a minute. Your URL is `https://<your-username>.github.io/spine-check/`.

## Running the session

1. Drop the plain URL in Slack. The spines load from `spines.json` — no setup step needed.
2. Everyone opens it, picks which spine is theirs and types their name, rates all 8, clicks **Finish**, and pastes the code back to you.
3. You open **Results**, paste all the codes into the box, and hit **Add codes**.

To run it with a different set of spines: go to **Set up**, type them in, then either click **Make the rating link** and send that, or click **Download spines.json** and commit that file over the existing one.

## What the results show

- Overall ranking by mean score across all five components, plus a **By component** view that ranks all eight spines against each other on one component at a time.
- An **Ask the results** box: type `top who`, `bottom mechanism`, `biggest disagreement`, or a spine number, and it answers.
- Per person: a score per component, the standard deviation, and a `split room` flag when raters disagree by more than 1.1.
- The weakest component across the whole room, which usually says more about the brief than about any individual.
- Every written note, anonymous by default, with a toggle to reveal who wrote what.
- CSV export of every individual rating.

## Notes

- Spines are numbered, not named, so the room rates the writing rather than the writer. The rater's own name rides along in their code, which is how the facilitator knows who has submitted and who left which note.
- Codes are base64 JSON. Anyone who has a code can decode it — including the rater's name and every score they gave — so this is not anonymous against a determined reader. It is anonymous enough for a room that is trying to be honest.
- Submissions and drafts are kept in the browser's local storage. Clearing site data wipes them. Export the CSV if you want to keep the results.
- Re-pasting a code from someone who already submitted overwrites their earlier one.
