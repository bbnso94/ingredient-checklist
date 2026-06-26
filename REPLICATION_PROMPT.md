# Replication Prompt

Copy and paste this into a new Codex session to recreate this project quickly.

```text
Build and publish a mobile-friendly interactive cooking website for the selected best recipe for 3 people at night: Smoky Chipotle Chihuahua Chili Mac With Lime.

Context:
- This should be a static website that can run from GitHub Pages.
- The live URL should be a GitHub Pages URL for the repository.
- The site must work well on a phone while cooking.
- The app should persist progress locally and also sync changes live across devices that currently have the website open.
- Use one dependency-free `index.html` with HTML, CSS, and vanilla JavaScript.
- Use semantic, accessible markup with real checkbox labels, keyboard focus styles, large phone-friendly tap targets, and `aria-live` status for progress and timers.
- Use ASCII-safe copy only to avoid broken encoding.

Recipe decision:
- The best dish is smoky chipotle chili mac with a Chihuahua-cheese queso finish and lime.
- The full recipe is scaled down to 3 generous night-of servings.
- The cheese method matters: toss Chihuahua cheese with cornstarch, warm evaporated milk with butter, then melt cheese gently over low heat.

3-person ingredient backbone:
- Elbow macaroni: 8 oz.
- 80 percent chuck ground beef: about 12 oz.
- Onion: 1 medium, diced.
- Bell pepper: 1/2 to 1, diced.
- Green onions: 2 to 3, whites and greens separated.
- Minced garlic: 2 tsp.
- Chili powder: 1 Tbsp.
- Ground cumin: 1 tsp.
- Paprika: 1/2 tsp.
- Dried oregano: 1/2 tsp.
- Black pepper: 1/2 tsp plus more to taste.
- Tomato paste: 1 Tbsp.
- Chipotle peppers in adobo: 1 pepper, finely chopped.
- Adobo sauce: 1 tsp.
- Worcestershire sauce: 1 tsp.
- Diced tomatoes: 1/2 can with juices.
- Tomato sauce: 1/2 can, about 4 oz.
- Kidney beans: 1/2 can, drained and rinsed.
- Broth: 1/2 cup, plus extra nearby.
- Chihuahua cheese: 8 oz shredded.
- Cornstarch: 1 1/2 tsp.
- Evaporated milk: 5 to 6 oz.
- Butter: 1 Tbsp.
- Sour cream: 2 Tbsp plus more for serving.
- Lime: juice of 1/2 lime, plus wedges.
- Kosher salt: to taste.

Website sections:
- Main recipe ingredients checklist
- Pantry, garnish, and heat-control checklist
- Utensils and kitchenware checklist
- Prep checklist
- Timer bank
- Step-by-step cooking guide
- Finish, serve, and store
- Session reset controls

Kitchenware checklist:
- Medium-large pasta pot
- Dutch oven or large heavy pot
- Medium saucepan for queso
- Colander
- Chef knife
- Cutting board
- Large bowl for cheese and cornstarch
- Measuring spoons and cups
- Wooden spoon or heatproof spatula
- Whisk
- Can opener
- Heatproof cup or mug for reserved pasta water
- Optional instant-read thermometer
- Shallow storage containers

Timers:
- Prep sprint: 20 minutes
- Pasta: editable minutes, default 8, with note to use package time minus 2 minutes
- Initial beef sear: 3 minutes
- Break up and brown beef: 6 minutes
- Onion, pepper, and scallion whites: 5 minutes
- Garlic: 30 seconds
- Spice bloom: 45 seconds
- Tomato paste darkening: 90 seconds
- Chili simmer: 12 minutes
- Warm milk and butter: 3 minutes
- Melt Chihuahua cheese: 6 minutes
- Fold pasta and queso: 4 minutes
- Rest before serving: 5 minutes
- Leftover cooling checkpoint: 2 hours

Cooking guide:
1. Boil 8 oz elbow macaroni in salted water until about 2 minutes short of full doneness. Reserve at least 1/2 cup pasta water, then drain.
2. Heat Dutch oven or heavy pot over medium-high and add 2 tsp peanut oil.
3. Add about 12 oz ground chuck in an even layer. Season lightly with salt and black pepper. Sear mostly undisturbed.
4. Break beef into small pieces and brown deeply. Leave about 1 Tbsp fat in the pot and drain the rest.
5. Add onion, bell pepper, and green onion whites. Cook until softened and beginning to color.
6. Add 2 tsp minced garlic and cook briefly.
7. Add chili powder, cumin, paprika, oregano, and black pepper. Bloom in the fat until fragrant.
8. Add 1 Tbsp tomato paste and cook until slightly darker.
9. Stir in chopped chipotle, adobo, Worcestershire, 1/2 can diced tomatoes, 1/2 can tomato sauce, 1/2 can kidney beans, and 1/2 cup broth. Simmer until thickened but loose.
10. In a saucepan, warm 5 to 6 oz evaporated milk with 1 Tbsp butter until steaming.
11. Reduce heat to low. Add cornstarch-coated Chihuahua cheese by handfuls, whisking until smooth.
12. Stir 2 Tbsp sour cream and juice of 1/2 lime into the queso.
13. Add drained macaroni to the chili pot. Fold in two-thirds to three-quarters of the queso.
14. Loosen with pasta water if needed. Taste and adjust salt, pepper, lime, chipotle, and texture.
15. Rest 5 minutes, then serve topped with remaining queso, green onion greens, sour cream, black pepper, and lime wedges.

State and sync requirements:
- Store all checkbox and timer state in `localStorage`.
- Use a recipe-specific storage key so old versions do not pollute this one.
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
- Include a README that explains the recipe, live URL, local persistence, and live sync behavior.
- Verify the public GitHub Pages URL serves the updated page.

Acceptance checks:
- The page loads as a static site.
- No non-ASCII or mojibake characters.
- Inline JavaScript parses.
- All 3-person ingredients appear in the ingredient list.
- Checkboxes persist locally and sync across open devices.
- Timers start, pause/resume, reset, complete, persist locally, and sync actions across devices.
- Mobile layout has readable text, large controls, and no overlapping UI.
```
