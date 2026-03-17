# Challenger Brand Directory

This file documents the structure, rules, and creative brief for contributing to `challenger.html` — a directory of challenger brand concepts generated using the ACB Challenger Brand Framework.

## What this is

The Challenger Brand Directory applies the ACB framework to 50+ markets, generating four challenger brand archetypes per market. Each archetype is a concrete brand concept with a name, tagline, positioning statement, and three strategic moves.

The live site is built as a single HTML file with all data embedded. Fonts (FTRegola) are base64-encoded inline.

---

## The Framework

Two axes define the four archetypes:

**Vertical axis**
- **Redefine** — change which dimensions matter in the market
- **Iterate** — improve within the existing competitive dimensions

**Horizontal axis**
- **Counter** — go back to basics, strip down, be contrarian
- **Push** — innovate, introduce new ideas, break new ground

**The four archetypes:**

| Archetype | Position | Core idea |
|---|---|---|
| **Misfit** | Counter + Redefine | The antidote. Does the opposite of what everyone else does. Celebrates what the market ignores. |
| **Disruptor** | Push + Redefine | Changes the rules. Redefines what matters. When others talk specs, talks style. |
| **Realkeeper** | Counter + Iterate | Back to basics. Strips away bloat. The OG version of the category, done with care. |
| **Innovator** | Push + Iterate | Wins by the existing rules, but outperforms everyone. Faster, better, more precise. |

---

## Identifying norms

Before developing archetypes, identify 4–5 norms for the market. Norms are the dimensions established brands compete on — what everyone does, what is considered "good", which direction everyone is going.

**For physical/consumer markets**, look at:
- What is the dominant format or product type?
- What credentials or signals do brands use to claim quality?
- What is the visual/aesthetic orthodoxy?
- What occasion or customer identity does the category serve?
- What do all brands have in common that no one questions?

**For software/digital markets**, look at:
- What is the dominant UX paradigm or interface model?
- What pricing and business model does everyone use?
- Who is the assumed user and how is the product sold to them?
- What features define "enterprise readiness" or credibility?
- What does the category assume about how users work?

Each norm should be written as a short dimension name + one sentence describing what established players actually do on that dimension.

---

## Naming rules

Brand names should be:
- **Creative and specific** — not generic descriptors
- **Markenfähig** — feels like a real brand, not a concept label
- **Never "The [Archetype]"** — e.g. never "The Misfit" or "The Innovator"
- **Occasionally German** if it fits naturally and sounds good (e.g. Eisenstube, Protokoll) — but not forced
- **Short** — one or two words preferred
- **Evocative** — the name should hint at the positioning without explaining it

Good examples: Amble, Catwalk, Barebone, Lastform, Nocebo, Groundwork, Signalfire, Lager Club, Fermentist, Eisenstube, Protokoll, Stillface, Sensorium

Bad examples: The Minimalist, Counter Brand, Redefine Co, Basic Option

---

## Data structure

Each market entry in the `DEMOS` object follows this exact structure:

```javascript
'market-key': {
  label: 'Display name',          // shown in pills
  market: "Full Market Name",     // shown as heading
  marketSummary: "2 sentences: what the market is and what defines competition in it.",
  norms: [
    { dimension: "Short name", description: "One sentence: what established players do on this dimension." },
    // 4–5 norms total
  ],
  archetypes: {
    misfit: {
      name: "Brand Name",
      tagline: "Short punchy tagline, 8–12 words.",
      positioning: "2–3 sentences: specific positioning for this market, what this challenger would stand for.",
      moves: [
        "Concrete strategic move 1",
        "Concrete strategic move 2",
        "Concrete strategic move 3"
      ]
    },
    disruptor: { /* same structure */ },
    realkeeper: { /* same structure */ },
    innovator: { /* same structure */ }
  }
}
```

---

## Categories

Current categories and their keys:

| Category | Label in HTML |
|---|---|
| `'Leisure and Hospitality'` | Leisure and Hospitality |
| `'Food and Beverage'` | Food and Beverage |
| `'Beauty and Home'` | Beauty and Home |
| `'Fashion and Apparel'` | Fashion and Apparel |
| `'Software and Content'` | Software and Content |

To add a market to a category, add its key to the `markets` array in the `CATEGORIES` array. **Always keep markets sorted alphabetically within each category.**

---

## How to add a new market

1. Add the market data object to `DEMOS` following the structure above
2. Add the market key to the correct category in `CATEGORIES`
3. Sort the category's markets array alphabetically by label
4. Validate the JS is still valid (no syntax errors)

**Prompt template for adding a market:**
```
Add "[Market Name]" to the [Category] category in challenger.html.
Key: 'market-key'
Label: 'Market name'

Follow the exact data structure in challenger.md. Analyze the norms carefully — for software markets use software-specific norm dimensions (UX paradigm, pricing model, assumed user, feature logic). Then develop all four archetypes with creative, brand-ready names.

Sort the category alphabetically after adding.
```

---

## Quality checklist

Before committing a new market, check:

- [ ] 4–5 norms, each with a short dimension name and one descriptive sentence
- [ ] All four archetypes present (misfit, disruptor, realkeeper, innovator)
- [ ] Brand names are creative, not generic or archetype-labelled
- [ ] Taglines are 8–12 words
- [ ] Positioning is 2–3 sentences, market-specific, not abstract
- [ ] Each archetype has exactly 3 moves
- [ ] Moves are concrete and actionable, not vague principles
- [ ] Market added to correct category and sorted alphabetically
- [ ] No JS syntax errors (check with `node -e "eval(require('fs').readFileSync('challenger.html','utf8').match(/const DEMOS=(\{[\s\S]*?\});/)[1])"`)

---

## Validation command

Run this to check the DEMOS object parses correctly:

```bash
node -e "
const fs = require('fs');
const content = fs.readFileSync('challenger.html', 'utf8');
const start = content.indexOf('const DEMOS={') + 'const DEMOS='.length;
const end = content.indexOf('\nfunction esc(');
const demosStr = content.slice(start, end).trim().replace(/;$/, '');
try {
  eval('var x = ' + demosStr);
  console.log('Valid. Markets:', Object.keys(x).length);
} catch(e) {
  console.log('Error:', e.message);
}
"
```
