# Fulfillment Hub

A small web app that replaces XYZ's spreadsheets and printed papers. One file, no backend, no build.

- **Office view:** order board, alerts, priority deadlines, issues list.
- **Warehouse view:** one big task at a time for phone or tablet.


> **About the screenshots.** They were taken after I pressed "+15 min" a few times (demo time 16:04 to 16:06), so more orders show as late than at the start. The walkthrough numbers below describe the **start state (15:12)**.

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
2. Upload `index.html`, `README.md` and the `screenshots` folder to the repository root.
3. Go to Settings → Pages.
4. Under "Build and deployment", choose "Deploy from a branch".
5. Select the `main` branch and the `/ (root)` folder, then Save.
6. Wait one to two minutes. The link appears at the top of the Pages screen.
7. Open the link in a private window to check it is public.

## Screenshots

### Office view

The four tiles answer "what is on fire?" straight away. "Needs attention" lists the worst orders first, and the board below shows all six stages with priority orders pinned to the top.

<img width="1400" height="717" alt="01-office-overview" src="https://github.com/user-attachments/assets/70e15c85-4d6b-4135-afc9-0fb4316c2f02" />

Scrolling down shows the rest of the board and the Issues panel, where anyone can log, filter and resolve a problem.

<img width="1400" height="711" alt="02-office-board-and-issues" src="https://github.com/user-attachments/assets/77636fc9-7f1f-4030-a06f-7a115a87999e" />

After a problem is reported from the Warehouse (or added here), the "Open issues" tile goes up and the issue appears in the list.

<img width="1400" height="675" alt="03-office-open-issues" src="https://github.com/user-attachments/assets/516cbf31-7c11-4318-9653-09f5d7beb8ae" />

### Warehouse view

One task at a time, big shelf codes, plain words. This is a Pick task: shelf first, then item.

<img width="1400" height="662" alt="04-warehouse-pick" src="https://github.com/user-attachments/assets/8ab5cfee-3166-4573-83a0-36296c89e384" />

At packing, the worker taps (or types) the code on the item in their hand. Look-alike variants are listed together on purpose.

<img width="1400" height="674" alt="05-warehouse-pack" src="https://github.com/user-attachments/assets/452cb312-b207-4556-9eda-aeb7779f70bb" />

If the code is wrong (here Black M instead of Navy M), the whole screen turns red, shows Expected vs. You scanned, and an issue is logged for the office.

<img width="1400" height="696" alt="06-wrong-item-stop" src="https://github.com/user-attachments/assets/c38f2d7b-20e3-49db-9b1a-d1968a71bb09" />

With the right codes, the order moves on to the final packing step.

<img width="1400" height="670" alt="07-pack-complete" src="https://github.com/user-attachments/assets/20490286-7153-46ce-abf0-43b64fff76ce" />

Then the worker is told exactly where to put the box and when the courier comes.
<img width="1400" height="677" alt="08-stage-lane" src="https://github.com/user-attachments/assets/8149e823-023b-491d-bfe0-ba6798966180" />

## Demo walkthrough

The demo clock starts at 15:12. Pickups are SwiftShip 14:00, QuickBox 16:00, EcoPost 18:00.

1. **Office view.** The tiles show 4 priority orders at risk, 3 delayed, 1 blocked and 1 open issue. Click a tile to filter the board.
2. **Delay alerts.** "Needs attention" lists ORD-1023 (staged, SwiftShip pickup missed) and ORD-1019 (stuck in Packing for 70 minutes).
3. **Blocked.** ORD-1012 is blocked because Runner Shoes White 9 is out of stock everywhere.
4. **Close to cutoff.** ORD-1007, ORD-1015 and ORD-1018 are priority orders shipping by 15:30, with a countdown.
5. **Warehouse view.** The first task is Move stock for ORD-1007. The rain jacket is only in Warehouse 2.
6. Tap "Done" → "Start picking" → "I have everything".
7. **Wrong-item catch.** At packing, tap a look-alike code (for example TEE-BLK-M instead of TEE-NVY-M, or JKT-OLV-M instead of JKT-OLV-L). The red STOP screen shows Expected vs. You scanned, and an issue is logged automatically.
8. Try again with the right codes. Do the same for the other item, then "Box is packed" and "Box is on the lane".
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
- The "+15 min" button and the "Courier collected" button are small demo and flow helpers that the brief did not list.
- Time limits (30/20/30/30 min per stage, half for priority) are settings at the top of the script.
