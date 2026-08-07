# Spine Check

A single-file tool for peer-rating brand spines in a workshop. No backend, no accounts, no data leaves anyone's browser.

Each spine has five components: **Who, Outcome, Mechanism, Quality, Reject**. Everyone scores everyone else's five components 1 to 5 and can leave one written note per person.

## Put it online (2 minutes)

1. Create a public repo on GitHub, e.g. `spine-check`.
2. Upload `index.html` to the root.
3. Settings → Pages → Source: `Deploy from a branch` → Branch: `main`, folder: `/ (root)` → Save.
4. Wait about a minute. Your URL is `https://<your-username>.github.io/spine-check/`.

## Running the session

1. Open the URL, go to **Set up**, type in all 8 names and spines.
2. Click **Make the rating link**, copy it, drop it in Slack.
3. Everyone opens it, picks their name, rates the other 7, clicks **Finish**, and pastes the code back to you.
4. You open **Results**, paste all the codes into the box, and hit **Add codes**.

If the link looks too long for Slack, click **Download spines.json** on the setup screen and commit that file next to `index.html`. The app loads it automatically, so the plain URL works on its own.

## What the results show

- Overall ranking by mean score across all five components.
- Per person: a score per component, the standard deviation, and a `split room` flag when raters disagree by more than 1.1.
- The weakest component across the whole room, which usually says more about the brief than about any individual.
- Every written note, anonymous by default, with a toggle to reveal who wrote what.
- CSV export of every individual rating.

## Notes

- Codes are base64 JSON. Anyone who has a code can decode it, so this is not anonymous against a determined reader. It is anonymous enough for a room that is trying to be honest.
- Submissions and drafts are kept in the browser's local storage. Clearing site data wipes them. Export the CSV if you want to keep the results.
- Re-pasting a code from someone who already submitted overwrites their earlier one.
