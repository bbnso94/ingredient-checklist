# Replication Prompt

Copy and paste this into a new Codex session to recreate this project quickly.

```text
Build and publish a mobile-friendly interactive cooking website for a receipt-based homemade chili mac dinner for three.

Context:
- This should be a static website that can run from GitHub Pages.
- The live URL should be a GitHub Pages URL for the repository.
- The site must work well on a phone while cooking.
- The app should persist progress locally and also sync changes live across devices that currently have the website open.

Receipt source of truth:
- Elbow macaroni, 32 oz
- Swanson broth, 32 oz
- Great Value extra sharp cheddar block, 8 oz
- 80/20 chuck ground beef
- Great Value sour cream
- Great Value diced tomatoes
- Great Value kidney beans
- Great Value tomato sauce
- Great Value tomato paste
- Chili powder
- Ground cumin
- Oregano
- Paprika
- Great Value minced garlic
- Worcestershire sauce
- Onion
- Green onions
- Bell pepper

Recipe adaptation:
- Make beef chili mac for 3 generous servings.
- Use cheddar-only unless the cook already has another melting cheese.
- Use green bell pepper instead of red bell pepper.
- Use diced tomatoes plus tomato sauce instead of crushed tomatoes.
- Use sour cream and green onions as finishing toppings.
- Treat evaporated milk, Monterey Jack, Dijon, cornstarch, chipotle, butter, oil, salt, black pepper, and vinegar or lime as pantry checks or optional upgrades.

Website requirements:
- Use one dependency-free `index.html` with HTML, CSS, and vanilla JavaScript.
- Use semantic, accessible markup with real checkbox labels, keyboard focus styles, large phone-friendly tap targets, and `aria-live` status for progress and timers.
- Use ASCII-safe copy only to avoid broken encoding.
- Keep the first screen useful immediately: title, progress, live sync status, and section navigation.
- Include these sections:
  - Purchased ingredients checklist
  - Pantry and optional upgrades checklist
  - Utensils and kitchenware checklist
  - Prep checklist
  - Timer bank
  - Step-by-step cooking guide
  - Finish, serve, and store
  - Session reset controls

Purchased ingredient checklist:
- Elbow macaroni: use 8 oz.
- Broth: use about 1 cup, keep extra nearby to loosen.
- Extra sharp cheddar: grate it, use most in the pot, save a handful for topping.
- 80/20 chuck ground beef: brown hard and drain excess fat.
- Sour cream: use for serving.
- Diced tomatoes: use the whole can with juices.
- Kidney beans: drain and rinse.
- Tomato sauce: use the whole can.
- Tomato paste: use 2 Tbsp and cook darker.
- Chili powder: use 1 1/2 to 2 Tbsp.
- Ground cumin: use 1 1/2 tsp.
- Oregano: use 1/2 to 1 tsp.
- Paprika: use 1 tsp.
- Minced garlic: use about 1 Tbsp.
- Worcestershire sauce: use 1 to 2 tsp.
- Onion: dice small.
- Green onions: slice for garnish.
- Bell pepper: dice small.

Kitchenware checklist:
- 5 to 6 quart Dutch oven or deep 12 inch skillet
- Medium pasta pot
- Colander
- Chef knife
- Cutting board
- Box grater
- Mixing bowl
- Measuring spoons and cup
- Wooden spoon or heatproof spatula
- Can opener
- Ladle or serving spoon
- Oven mitts and trivet for optional oven or broiler finish

Timers:
- Prep sprint: 15 minutes
- Initial beef sear: 2 minutes
- Break up and brown beef: 4 minutes
- Onion and pepper: 5 minutes
- Garlic and tomato paste: 2 minutes
- Spice bloom: 1 minute
- Chili simmer: 15 minutes
- Pasta: editable minutes, default 7, with note to use package al dente time minus 2 minutes
- Cheese melt: 5 minutes
- Optional oven finish: 7 minutes
- Optional broiler finish: 4 minutes
- Rest before serving: 5 minutes

Cooking guide:
1. Heat the main pot over medium-high. Add oil only if the pan is dry.
2. Add beef in an even layer, season lightly, and sear mostly undisturbed for 2 minutes.
3. Break up beef and brown another 4 minutes. Drain excess fat beyond about 1 Tbsp.
4. Reduce to medium. Cook onion and bell pepper for 5 minutes.
5. Add minced garlic and 2 Tbsp tomato paste. Stir 2 minutes until darker and aromatic.
6. Add chili powder, cumin, paprika, oregano, and optional chipotle. Bloom 1 minute.
7. Add Worcestershire and about 1 cup broth. Scrape browned bits from the pot.
8. Add diced tomatoes with juices, tomato sauce, kidney beans, and salt if available. Simmer uncovered 15 minutes.
9. Boil macaroni separately until 2 minutes shy of package al dente. Reserve 1/2 cup pasta water and drain.
10. Turn chili to low. Add butter and evaporated milk if available; otherwise use broth or pasta water.
11. Fold in pasta, then add grated cheddar gradually over low heat.
12. Loosen with broth or pasta water if tight. Finish with vinegar or lime if available.
13. Optional: top with saved cheese and bake at 450 F or broil until bubbly.
14. Rest 5 minutes, then serve with sour cream and green onions.

State and sync requirements:
- Store all checkbox and timer state in `localStorage`.
- Add live cross-device sync so if one open device checks an item, all other open devices update immediately.
- Use `ntfy.sh` publish and Server-Sent Events for lightweight realtime sync:
  - Publish JSON events to an obscure topic.
  - Subscribe with `EventSource` to `https://ntfy.sh/<topic>/sse?since=all`.
  - Ignore messages from the same client ID.
  - Support events for checkbox changes, timer start/pause/reset, pasta timer minute changes, reset-all, reset-checks, reset-timers, hello, and snapshot.
  - On a new device opening the page, publish `hello`; other active devices reply with a state snapshot.
  - If sync fails, keep the app usable with local `localStorage` only.
- Show a visible `Live sync` status line.
- Add a warning in documentation that the sync topic is public-by-name and not for private information.

Timer behavior:
- Each timer has Start, Pause/Resume, and Reset.
- Timers can run independently.
- Timer completion should show visible status and try a short Web Audio beep after user interaction.
- Running timer state should survive refresh by storing `endAt`, `remaining`, `running`, and `done`.

Deployment:
- Publish the finished `index.html` to GitHub Pages.
- Include a README that explains the receipt-based cooking app, live URL, local persistence, and live sync behavior.
- Verify the public GitHub Pages URL serves the updated page.

Acceptance checks:
- The page loads as a static site.
- No non-ASCII or mojibake characters.
- Inline JavaScript parses.
- All receipt items appear in the purchased ingredients list.
- Pantry-only items are separated from receipt-confirmed items.
- Checkboxes persist locally and sync across open devices.
- Timers start, pause/resume, reset, complete, persist locally, and sync actions across devices.
- Mobile layout has readable text, large controls, and no overlapping UI.
```
