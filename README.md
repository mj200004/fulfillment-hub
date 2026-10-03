AI USAGE NOTE: Fulfillment Hub

Tools used
I used Claude (Anthropic) as my main AI tool. I gave it the full brief and asked it to
plan, then write the single-file web app (HTML, CSS and vanilla JavaScript), the
README, the video outline and a checklist. I used it like a fast junior engineer: I
set the scope and reviewed what came back.

Where I disagreed with or changed the AI
1. [EDIT TO MATCH WHAT HAPPENED] The AI first suggested a backend with a database and
   user accounts. I removed it. The brief asked for a simple app that opens with a
   double-click and works on GitHub Pages, and a database would add set-up work
   without helping the warehouse staff. I kept everything in memory and listed a
   backend under "what I'd do next".
2. [EDIT TO MATCH WHAT HAPPENED] The AI's first Warehouse screen looked like a
   dashboard with several lists and filters. Warehouse staff are not comfortable
   with technology, so I changed it to one task at a time, large buttons, plain
   words, and colour used only for urgency.

How I verified the output
- I opened the file by double-clicking it and also on a hosted GitHub Pages link.
- I followed one priority order from Move stock through Pick, Pack, Stage and
  Shipped, and checked that each stage change showed up on the Office board.
- I tested the wrong-item screen with the look-alike variants (Black M vs Navy M).
- I checked the sample cases: blocked order, Warehouse-2-only item, delayed order,
  missed pickup and the pre-existing issue.
- I tested on a phone-sized window and checked the text was readable.
- I read through the code for anything that stored data outside the page.
