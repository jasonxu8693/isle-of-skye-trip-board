# Isle of Skye Trip Board

Gamified group planning board for the July 2026 Isle of Skye trip. Single self-contained `index.html`, GitHub Pages-ready.

Built with the `trip-board-builder` skill from the Notion itinerary.

## Live sync

Shared sync is **enabled** via a Google Apps Script web app backed by one Google Sheet
(`apps-script/Code.gs`). The whole board state is stored as JSON in a single cell.
`REMOTE_API_URL` in `index.html` points at the deployed `/exec` endpoint; the board
pulls on load + every 25s and pushes on every change.

**Limitation:** writes are **last-write-wins**. Fine for a ~6-person trip — but if two
people save at the same second, the later save overwrites the earlier one.

To re-deploy the script (e.g. after editing `Code.gs`): open the bound Sheet → Extensions
→ Apps Script → Deploy → Manage deployments → edit → new version. The `/exec` URL stays
the same, so no change to `index.html` is needed.
