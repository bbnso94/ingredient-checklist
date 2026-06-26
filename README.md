# Smoky Chipotle Chihuahua Chili Mac Cook Mode

Interactive cooking companion for the selected best recipe for 3 people at
night: smoky chipotle chili mac with a Chihuahua-cheese queso finish and lime.

Live site:

https://bbnso94.github.io/ingredient-checklist/

## What It Includes

- 3-person ingredient checklist scaled from the chosen recipe
- Pantry, garnish, and heat-control checklist
- Utensils and kitchenware checklist for pasta, chili, and queso stations
- Detailed prep checklist
- Step-by-step cooking guide
- Independent timers for prep, pasta, beef browning, aromatics, garlic, spice bloom, tomato paste, simmering, queso, folding, resting, and leftover cooling
- Local browser persistence through `localStorage`
- Live cross-device sync through a shared ntfy topic while devices are open on the page
- A copy/paste replication prompt in `REPLICATION_PROMPT.md`

## Recipe Basis

The app now uses the Chihuahua queso recipe decision as the backbone, scaled for
3 generous servings:

- 8 oz elbow macaroni
- about 12 oz 80 percent chuck ground beef
- onion, bell pepper, green onion whites, garlic
- chili powder, cumin, paprika, oregano, black pepper, kosher salt
- tomato paste, diced tomatoes, tomato sauce, kidney beans, broth, Worcestershire
- 1 chipotle pepper plus 1 tsp adobo for balanced smoky heat
- 8 oz shredded Chihuahua cheese, 1 1/2 tsp cornstarch, 5 to 6 oz evaporated milk, 1 Tbsp butter, 2 Tbsp sour cream, and lime

## Files

- `index.html`: the full static cooking app
- `REPLICATION_PROMPT.md`: a full prompt to recreate this project quickly
- `.github/workflows/pages.yml`: GitHub Pages deployment workflow for this repo

## Persistence And Sync

Checklist and timer state are stored in the browser on the current device.

- Refreshing keeps progress.
- The page includes reset controls for all progress, checklists only, or timers only.
- Open devices sync checklist and timer actions through `ntfy.sh`.
- If live sync is unavailable, progress still saves locally on that device.
- The sync topic is public-by-name, so do not put private information into the checklist.
