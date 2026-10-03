# Fulfillment Hub

A small web app that replaces XYZ's spreadsheets and printed papers. One file, no backend, no build.

- **Office view:** order board, alerts, priority deadlines, issues list.
- **Warehouse view:** one big task at a time for phone or tablet.

## Problems I chose, and why

| Problem | What I built | Why |
|---|---|---|
| P1 Can't see order status | Kanban board with six stages, time in stage, green/amber/red | Everything else depends on seeing the whole picture |
| P2 Delays unnoticed | Stage time limits and automatic "Needs attention" alerts | Cheap to build, big payoff |
| P3 Priority orders missed | Ship-by = courier pickup minus 30 min, countdown, always pinned first | Same-day orders are where money and reputation are lost |
| P4 Stock can't be found | Stock check at pick time: Warehouse 2 only creates a "Move stock" task; nowhere makes it "Blocked: no stock" | Stops pickers walking to empty shelves |
| P5 Wrong item shipped | Packing check against the SKU, with a red "WRONG ITEM, STOP" screen | A wrong shipment costs a refund, shipping both ways and a bad review |
| P6+P7 Lost boxes / forgotten problems | Issues list and an automatic "Staged but pickup missed" alert | One shared place instead of memory and chat |

## What I left out

Real courier or marketplace integrations, returns, inbound receiving, authentication. I judged that these matter less than fixing the daily flow, and each one would need real systems to test against.

## Run locally

Double-click `index.html`. It works offline and has no external dependencies.

## Deploy on GitHub Pages

1. Create a new public repository on GitHub.
2. Upload `index.html` and `README.md` to the repository root.
3. Go to Settings → Pages.
4. Under "Build and deployment", choose "Deploy from a branch".
5. Select the `main` branch and the `/ (root)` folder, then Save.
6. Wait one to two minutes. The link appears at the top of the Pages screen.
7. Open the link in a private window to check it is public.

## Demo walkthrough

The demo clock starts at 15:12. Pickups are SwiftShip 14:00, QuickBox 16:00, EcoPost 18:00.

1. **Office view.** The tiles show 4 priority orders at risk, 3 delayed, 1 blocked and 1 open issue. Click a tile to filter the board.
2. **Delay alerts.** "Needs attention" lists ORD-1023 (staged, SwiftShip pickup missed) and ORD-1019 (stuck in Packing for 70 minutes).
3. **Blocked.** ORD-1012 is blocked because Runner Shoes White 9 is out of stock everywhere.
4. **Close to cutoff.** ORD-1007, ORD-1015 and ORD-1018 are priority orders shipping by 15:30, with a countdown.
5. **Warehouse view.** The first task is Move stock for ORD-1007. The rain jacket is only in Warehouse 2.
6. Tap "Done" → "Start picking" → "I have everything".
7. **Wrong-item catch.** At packing, tap JKT-OLV-M instead of JKT-OLV-L. The red STOP screen shows Expected vs. You scanned, and an issue is logged automatically.
8. Try again with the right codes. Do the same for the Navy tee, then "Box is packed" and "Box is on the lane".
9. **Report a problem.** Tap "Report a problem" and one type, 2 taps in all.
10. **Back to Office.** Open ORD-1007, mark it "Courier collected", and see the new issue in the Issues panel.
11. Press "+15 min" to watch ambers turn red. "Reset demo data" restores everything.

## What I'd do next

- Real barcode scanning instead of tapping codes.
- Courier and marketplace integrations (labels, tracking, order import).
- A database and logins, so Office and Warehouse share live data.
- Reserve stock per order so two orders can't claim the same units.
- Inbound receiving and returns.
- Per-person task assignment and a daily report.

## Notes

- All state is in memory. Refreshing the page resets the demo.
- The "+15 min" button and the "Courier collected" button are small demo and flow helpers.
- Time limits (30/20/30/30 min per stage, half for priority) are settings at the top of the script.
