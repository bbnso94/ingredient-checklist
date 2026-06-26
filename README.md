# Receipt-Based Chili Mac Cook Mode

Interactive cooking companion for homemade chili mac for three, adapted to the
actual Walmart receipt ingredients.

Live site:

https://bbnso94.github.io/ingredient-checklist/

## What It Includes

- Purchased ingredient checklist from the receipt
- Pantry and optional upgrade checklist
- Utensils and kitchenware checklist
- Prep checklist
- Step-by-step cooking guide
- Independent timers for prep, browning, simmering, pasta, cheese melt, optional oven finish, optional broiler finish, and rest
- Local browser persistence through `localStorage`

## Recipe Basis

The app uses the receipt as the source of truth and adapts the recommended beef
chili mac method around what was actually purchased:

- Cheddar-only unless another melting cheese is already available
- Green bell pepper instead of red bell pepper
- Diced tomatoes plus tomato sauce instead of crushed tomatoes
- Sour cream and green onions for finishing
- Pantry checks for evaporated milk, Dijon, cornstarch, chipotle, butter, oil,
  salt, pepper, and vinegar or lime

## Files

- `index.html`: the full static cooking app
- `.github/workflows/pages.yml`: GitHub Pages deployment workflow for this repo

## Persistence

Checklist and timer state are stored in the browser on the current device.

- Refreshing keeps progress.
- The page includes reset controls for all progress, checklists only, or timers only.
- Progress does not sync across different phones or computers.
