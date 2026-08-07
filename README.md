# Happy Landing — Website

Premium soft play & ball pit hire, plus baby travel gear hire. Perth WA.

**Live:** https://kingsley-digital.github.io/weston-kingsley-co/

Single-file static site — no build step, no framework, no dependencies beyond Google Fonts. Edit `index.html` directly and commit; the live site updates within a minute.

---

## Files

| File | What it is |
|---|---|
| `index.html` | The entire site — all five pages, styles and scripts |
| `hero-ballpit.jpg` | Homepage hero — child in a neutral ball pit, overhead |
| `kx23-angled.jpg` | Soft play visualisation — angled view |
| `kx23-front.jpg` | Soft play visualisation — front view |
| `kx23-plan.jpg` | Soft play visualisation — overhead plan |
| `travel-gear.jpg` | Travel Gear page banner |
| `about-family.jpg` | About page image |
| `social-share.jpg` | 1200×630 link preview card (Facebook/Instagram) |

All files sit at the repo root. Filenames are case-sensitive — rename one and the image breaks.

`weston-kingsley.jpg` is no longer referenced and can be deleted.

---

## Naming history

Three names, in order: **Weston & Kingsley Co.** → **Soft Landing Co.** → **Happy Landing**.

Soft Landing was dropped because `softlanding.com.au` belongs to Soft Landing, a long-established national mattress-recycling social enterprise that also operates in WA. The category adjacency (foam, bedding) and their search dominance made it a poor foundation.

**Consequences to tidy up:**
- The repo name and Pages URL still say `weston-kingsley-co`. Renaming the repo is safe (GitHub redirects) but changes the live URL — best done at the same time as pointing a custom domain at it, so it's one change not two.
- "Soft Landing Co." is registered with ASIC but unused. Register **Happy Landing** under the same ABN (~$44 for 3 years) and let the old one lapse. **The ABN does not change** — it belongs to the partnership entity, not the trading name.

---

## Business structure (for reference)

Family partnership — both partners, general (not limited). ABN and partnership TFN obtained via abr.gov.au. ANZSIC activity: *Hire of personal or household goods*. Not GST-registered (under the $75k threshold).

---

## Status: live but pre-launch

The site is publicly reachable. It is **not** ready to take real bookings.

**Deliberately absent, and must stay absent until true:**
- All prices and bonds show **TBA** — don't publish figures until equipment cost and insurance are settled
- No "Fully Insured" claim anywhere — only add it once the policy is active
- No customer testimonials — only genuine, attributed reviews

**Still to do:**
- [ ] Register "Happy Landing" with ASIC under the existing ABN
- [ ] IP Australia trade mark search on "Happy Landing"
- [ ] Domain purchased — `happylanding.com.au` (confirm before publishing the email address anywhere)
- [ ] Business email created — Zoho's free tier is enough to start
- [ ] OTTOP: confirm KX23 itemised parts list, neutral colourway, transport/disassembly, lead time (~6–8 weeks). Contact: office@ottop.com.au
- [ ] Public liability insurance quoted and active (mention outdoor/marquee use)
- [ ] Hire agreement drafted (bonds, weather clause, late-return grace period)
- [ ] Formspree connected
- [ ] Business bank account in the partnership's name

---

## Placeholders in the code

| What | Where | Action |
|---|---|---|
| `YOUR_FORM_ID` | `<form action="...">` on the Enquire page | Sign up at [formspree.io](https://formspree.io) (free, 50/month) and paste the real ID. Until then the form shows visitors an email fallback rather than failing silently. |
| `hello@happylanding.com.au` | `CONTACT_EMAIL` at the top of the `<script>` block | Change in that one place; it updates the footer, form errors and no-JS fallback |
| `og:image` | `<head>` | Relative path. Once the domain is live, make it an absolute `https://` URL and add `og:url` |

---

## Images that need replacing

**The three `kx23-*.jpg` files are AI-generated visualisations, not photographs.** The caption under the gallery says so and must stay until real photos replace them.

Check every item in those renders against OTTOP's itemised parts list before taking a booking. They depict a bouncy castle, tunnel, foam blocks and ride-on animals. **The current plan is soft play only — no bouncy castle** — so at minimum the castle needs to come out of those images, or the images need replacing. Advertising equipment you don't supply is misleading conduct under Australian Consumer Law.

OTTOP send photos and videos of each order before it ships — those will give you accurate images of your actual set weeks ahead of delivery. Ask for permission to use them.

**`hero-ballpit.jpg` and `travel-gear.jpg` are also generated.** They work as mood images and make no specific product claim — the hero's ball pit is round while the KX23's is square, and the travel shot isn't the actual Joolz or BabyBjörn. Fine as atmosphere; replace with real photos once the gear is in hand. Don't move the hero image onto the Soft Play page, where it would sit beside the real specs.

---

## Editing on iPad

1. Repo → **Code** tab → tap `index.html`
2. Tap the **pencil** icon
3. Edit → scroll down → **Commit changes**

For images: **Add file → Upload files**. Uploading a file with an existing name overwrites it.

**Gotchas learned the hard way:**
- Safari appends `(1)`, `-1` etc. to repeat downloads. A file named `index-1.html` won't be served as the homepage. Clear old downloads from Files before re-downloading.
- Browsers cache aggressively. If a change doesn't appear, add `?v=2` to the URL to force a fresh fetch before assuming the upload failed.
- Facebook caches link previews. After changing `og:image`, run the URL through Facebook's Sharing Debugger and hit "Scrape Again".
- If Pages ever serves this README instead of the site, the usual causes are a missing `index.html` or a Jekyll build. Adding an empty `.nojekyll` file to the repo root fixes the second.

---

## Tech notes

- Fonts: Fraunces (display) + Inter (body) via Google Fonts. The social card was generated with substitute fonts (Caladea) — close, not exact. Rebuild in Canva with the real fonts if you want it pixel-perfect.
- Mobile nav is an anchored dropdown, not `position:fixed` — deliberate, avoids a rendering bug in some in-app browsers
- `<meta name="color-scheme" content="light">` stops OS dark mode auto-inverting the site. **Don't remove it.**
- Navigation is JS-driven; a `<noscript>` fallback gives non-JS visitors a contact path
- Form includes a `_gotcha` honeypot for spam
- Accessibility: labels linked to inputs, keyboard-navigable cards, ARIA on the menu toggle, `scope` on table headers
