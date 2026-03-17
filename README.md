# Challenger Brand Directory

A living directory of challenger brand concepts across 40+ markets, built on the ACB Challenger Brand Framework.

**[→ View the live directory](https://acolorbright.github.io/challenger-brand-directory/challenger.html)**

---

## What it is

The Challenger Brand Directory applies the ACB framework to consumer and software markets, generating four challenger brand archetypes per market — each with a name, tagline, positioning statement, and three strategic moves.

It's a single self-contained HTML file (`challenger.html`) with all data embedded inline. No build step, no dependencies.

---

## The framework

Two axes define four archetypes:

|  | **Counter** (back to basics) | **Push** (break new ground) |
|---|---|---|
| **Redefine** (change what matters) | Misfit | Disruptor |
| **Iterate** (improve within existing rules) | Realkeeper | Innovator |

**Misfit** — The antidote. Does the opposite of what the market expects.
**Disruptor** — Changes the rules. Redefines what dimensions matter.
**Realkeeper** — Strips away bloat. The OG version of the category, done right.
**Innovator** — Wins by the existing rules, but outperforms everyone.

---

## Current markets (43)

| Category | Markets |
|---|---|
| Leisure & Hospitality | Burger Restaurant, Cinema, Coffee Shop, Fine Dining, Fitness Studio, Lunch Bistro, Luxury Travel, Pizzeria, Wine Bar |
| Food & Beverage | Chewing Gum, Craft Beer, Hydration Drinks, Longevity Supplements, Natural Wine, Non-Alcoholic Beer, Olive Oil, Protein Bars, Soda, Tea |
| Beauty & Home | Hair, Home Fragrance, Make-up, Men's Skincare, Nails, Niche Fragrances, Premium Skincare, Scented Candles, Sun Care, Tableware, Towels |
| Fashion & Apparel | Activewear, Backpacks, Jewelry, Leather Goods, Men's Underwear, Running Apparel, Running Shoes, Socks, Sunglasses, Swimwear |
| Software & Content | Accounting, Corporate Learning, CRM, HR Management, Legal Tech, Messaging, Mobile Games, Music Production, Music Streaming, Presentation, To-do List, Video Generation, Video Streaming |

---

## Adding a new market

See [`challenger.md`](./challenger.md) for the full contribution guide, including:
- Framework logic and archetype definitions
- Norm identification methodology
- Data structure reference
- Naming rules and quality checklist
- Validation command

**Quick-start prompt for Claude:**
```
Add "[Market Name]" to the [Category] category in challenger.html.
Key: 'market-key'
Label: 'Market name'

Follow the exact data structure in challenger.md. Analyze the norms carefully — for software markets use software-specific norm dimensions (UX paradigm, pricing model, assumed user, feature logic). Then develop all four archetypes with creative, brand-ready names.

Sort the category alphabetically after adding.
```

---

## Project structure

```
challenger-brand-directory/
├── challenger.html   # The live directory (single file, open in browser)
├── challenger.md     # Contribution guide and framework documentation
└── README.md         # This file
```

---

## Contributing

1. Read [`challenger.md`](./challenger.md) before contributing
2. Add market data following the exact structure defined there
3. Run the validation command to check for JS syntax errors
4. Keep markets sorted alphabetically within their category
5. Submit a PR with one market per commit

---

A Color Bright — Brand and Product Design Studio
