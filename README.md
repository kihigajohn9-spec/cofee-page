# Pwani Roasters – Responsive Landing Page

A responsive landing page for a fictional coffee subscription, built with plain HTML, CSS and JavaScript. No frameworks, no build step.

**Live page:** https://claude.ai/artifact/3HkEKRMKTWFDZ7yARcyvUz

## Features

- **Responsive design:** fluid type, CSS grid that collapses to one column below 820px, mobile-first touch targets
- **Navigation menu:** sticky header, smooth scrolling, active link highlighting, hamburger menu on mobile (closes on link tap or Escape)
- **Call-to-action buttons:** hero CTAs, plan summary CTA and email signup
- **Interactive UI:** live plan builder (roast, bag size, delivery frequency) with instant price, FAQ accordion, email validation
- **Animations:** hero load-in, rising steam, price bump on change, menu and FAQ transitions
- **Accessibility:** visible keyboard focus, labelled controls, `aria-live` price updates, `prefers-reduced-motion` respected
- **Theming:** light and dark themes follow the system setting

## Task workflow mapping

| Step | Where it lives |
|---|---|
| 1. Design the layout | Section order in `index.html`, tokens in `tokens.css` |
| 2. Responsive sections | `sections.css`, mobile rules in `@media (max-width:820px)` |
| 3. Navigation and CTAs | `<header>`, `.btn` styles, `nav.js` |
| 4. Basic animations | Hero, steam and price keyframes, menu and FAQ transitions |
| 5. Mobile optimisation | Viewport meta, safe-area insets, hamburger menu, full-width buttons |

## Project structure

```
pwani-roasters/
├── index.html          Page markup: header, hero, how, plan, faq, join, footer
├── css/
│   ├── tokens.css      Colours, light/dark themes, fonts
│   ├── base.css        Reset, typography, focus styles, .wrap, section spacing
│   ├── components.css  Buttons, nav, hamburger, option pills, summary card, FAQ, form
│   └── sections.css    Hero and animations, steps, builder, signup, footer, media queries
├── js/
│   ├── nav.js          Header shadow, mobile menu, active link (IntersectionObserver)
│   ├── plan.js         Price = bag size price × (1 − delivery discount)
│   └── signup.js       Email validation and status message
└── assets/             Favicon and images (optional)
```

The published version combines all CSS into one `<style>` block and all JS into one `<script>` block inside a single `index.html`. The code is identical, so splitting it into the structure above is a cut-and-paste job.

## Plan pricing (placeholder values)

| Bag size | Price (TZS) |
|---|---|
| 250 g | 24,000 |
| 500 g | 44,000 |
| 1 kg | 80,000 |

| Delivery | Discount |
|---|---|
| Every week | 10% |
| Every 2 weeks | 5% |
| Monthly | 0% |

To change prices or discounts, edit the `base` and `disc` objects at the top of the plan builder code (`plan.js`).

## Run locally

1. Put the files in a folder (or use the single `index.html`).
2. Open `index.html` in any modern browser.

Optional local server:

```bash
python3 -m http.server 8000
# then open http://localhost:8000
```

## Customising

- **Colours and fonts:** change the variables in `:root` (`tokens.css`). Dark theme values are in the `prefers-color-scheme: dark` block.
- **Copy:** edit text directly in `index.html`.
- **Breakpoint:** the mobile layout starts at `820px`, set in the media query in `sections.css`.
- **Signup:** `signup.js` only validates and shows a message. To collect emails for real, send the value to your backend or an email service where the success message is set.

## Browser support

Current versions of Chrome, Edge, Firefox and Safari, on desktop and mobile.

## Notes

- Brand name, copy and prices are fictional placeholders.
- The coffee cup is built with CSS only, so there are no image dependencies.
