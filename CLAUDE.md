# Unit 1508 Furniture Planner

Single-file app (`index.html`), no build step. Netlify site `unit-1508-planner` deploys from `main` (publish root).
Live: https://unit-1508-planner.netlify.app

## Standing rule: keep the app in sync with the apartment
The app must always reflect the latest state of the apartment. The source of truth is the claude.ai project doc
`claude/unit-1508-apartment-tracker.md` (project "Home and House Planning").

Whenever that tracker changes (an item is bought, delivered, placed, moved, returned or ruled out), update this app in the same turn:
1. Edit the `APT` object in `index.html`:
   - `items`: owned/delivered pieces at real sizes and their actual (or planned) positions
   - `inventory`: every tracked item with its status
   - `label` and `note`
   - **bump `version`** so phones holding an unedited older copy load the new layout on next open
2. Add new owned pieces to the "Our pieces" preset group, and planned ones to "Planned / considering".
3. Check that nothing shows a red or amber fit warning (emulated iPhone, Playwright), then commit and push to `main`.
4. Confirm the Netlify deploy went live.

## Coordinates
Inches, origin at the unit's top-left outside corner. Living room left (exterior) wall is x=6, window wall y≈388,
bedroom-shared wall x=153.5. Bedroom floor is x 158.5 to 283, y 157 to 355.5. Rotation 90 swaps width onto the y axis.
