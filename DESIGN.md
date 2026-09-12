# CircleRootTech — Design & Content System

**Read this before writing a single line of any page.** Every page on circleroottech.com
derives from this file. If something here conflicts with what a page currently does, this
file wins and the page is wrong.

Owner: Maribel Saenthavisouk · CircleRootTech LLC · Salt Lake City, UT

---

## 1. What this site is arguing

One claim, and every page serves it:

> **Making software got easy. Making software worth having didn't.**

CircleRootTech is a technology company built from the ground up on one conviction: software
should be **deliberate**, it should be **durable**, and it should be **made for the people who
use it** rather than at their expense.

The site is not a product catalog and it is not a job hunt. It is the argument that this
company applies judgment, and the evidence for it.

---

## 2. Voice rules — non-negotiable

| Do | Never |
|---|---|
| **"I"** — one founder, one operator | **"We"** — there is no we |
| State status honestly, including bad status | Round up. Ever. |
| Name what a product *can't* do | Imply capability that isn't shipped |
| Plain verbs, sentence case | Emoji as section markers |
| Let the evidence carry the claim | Adjective stacks ("warm, simple, trustworthy") |

**Banned phrases** — these are on the current live site and must not survive:

- ❌ "Built by a mom with zero coding experience" / "0 — Prior coding experience"
  *Why: it's a novelty frame. It asks the reader to be impressed despite her, and hands a
  skeptic the exact words to dismiss her with. The company is the accomplishment, not the
  surprise that she managed it.*
- ❌ "Built with purpose, love, and Claude 🧡"
  *Why: reads as "vibe coded" to the exact reader we need to convince otherwise.*
- ❌ "Apps built with purpose, not just code" — vague; says nothing falsifiable.
- ❌ Any "verified by NCMEC and IWF" / "always-on protection" claim. See §7.
- ❌ "Get early access" / "Be first to know" — pre-launch framing. Products are shipping.

**Tone check:** if a sentence would survive being pasted into any other company's site,
rewrite it. Specificity is the whole product.

---

## 3. Color — light base, warm gradient accent

**v3, replacing the v2 all-navy scheme.** Maribel's call: keep the gradient (it's right — it's the
logo), lose the dark background (read as heavy, not "professional and clean") and the display
font (Bricolage Grotesque read as the old site's leftover quirkiness, not what she wants now).
Light page, white/off-white surfaces, dark charcoal text, Inter for headlines. The two dark
"evidence" bands (the build log, the final contact close) stay dark on purpose — see the
band--dark rule below — but the page itself is light again.

```css
--bg:       #FBFAF8;  /* page background                     */
--surface:  #F3F1ED;  /* raised panels — cards, flow box      */
--bg-deep:  #1A1816;  /* dark charcoal — the evidence bands   */

--coral:    #9E271A;  /* corrections only — pulled/rejected   */
--clay:     #9E571A;  /* the primary — links, marks, CTAs     */
--amber:    #8C6517;  /* the one highlight, as text           */
--rust:     #D9603F;  /* depth — "in development" ring only   */
--amber-fill: #F3C15A; /* same hue, vivid — fills/washes only, never text */

--ink:      #1E1B17;  --stone:    #746F66;
--text-2:   #4A453D;  --text-3:   #34302A;

--paper-hi: #F5F1EC;  --on-dark-1:#EDE9E2;  --on-dark-2:#C9C3D6;
--on-dark-3:#B8A98C;  --on-accent:#2B1608;
--rule:     rgba(30,27,23,.12);
```

**Why two versions of some colors exist.** `--coral`/`--clay`/`--amber` are deep enough to work as
*text on the light page* (5–7:1 against `--bg`). The same hues at full saturation (the logo's
actual brightness) fail contrast on white — they only work as solid fills or on the dark bands,
which is what `--amber-fill` and the pastel `#F0938A`/`#F3C15A` pairing inside `.v-fix`/`.v-live`
are for. **Don't reach for the vivid version as page text — it will fail contrast.** If a new
component needs an accent color as text on the light page, use the deep token; if it needs a
color as a solid fill or inside a dark band, the vivid value is fine.

**Four colors, four jobs — unchanged from v2:** coral marks a correction only, clay is the
workhorse (links, CTAs), amber is the one highlight (spend it sparingly — charter dashes,
verdict pills, the headline underline), rust is only the hollow "in development" ring.

**Type — Inter for headlines**, replacing Bricolage Grotesque. Source Serif 4 (body) and
IBM Plex Mono (labels/data) are unchanged.

**Accessibility floor — verified, keep it:** `ink/bg` 16.4:1 · `text-2/bg` 9.1:1 · `stone/bg`
4.8:1 · `clay/bg` 5.25:1 · `coral/bg` 7.3:1 · `amber/bg` 5.05:1 · `on-accent/amber-fill` 10.3:1 ·
`paper-hi/bg-deep` 15.7:1 · `on-dark-2/bg-deep` 10.3:1 · `on-dark-3/bg-deep` 7.7:1. Never
introduce a pairing below 4.5:1 for body text or 3:1 for large display type or UI graphics —
recompute with a real contrast formula, don't eyeball it.

**band--dark budget, unchanged: never more than two per page.** Right now that's the build log
and the final contact close, on every page. If a third dark section starts to feel necessary,
that's a sign to make it a light band instead, not to raise the budget.

---

## 4. Type

| Role | Face | Use |
|---|---|---|
| Display | **Bricolage Grotesque** (700/800) | Headlines only. Tight tracking (−.03em). |
| Body | **Source Serif 4** (400/600) | All prose. |
| Utility | **IBM Plex Mono** (400/500/600) | Labels, eyebrows, data, the ledger, spec sheets. |

The three faces encode the three worlds: the grotesque is the company, the serif is the
sixteen years of writing, the mono is the code. Don't add a fourth.

Headings are sentence case. Eyebrows/kickers are uppercase mono, `.72rem`, `.14em` tracking.

---

## 5. Components in `styles.css`

Reuse these. Do not invent parallel ones.

- `.band` / `.band--dark` — section wrapper. Dark bands are for **evidence and contact only**;
  never more than two per page or the accent stops working.
- `.wrap` — max 1120px, responsive gutter.
- `.split` — 1.1fr / .9fr two-column, collapses at 860px.
- `.thesis` — the one huge headline per page. `.turn` = clay, `em` = amber underline.
- `.kicker` — numbered section eyebrow (`01 · The accomplishment`).
- `.charter` — hanging em-dash list, amber marker. For convictions and program types.
- `.spec` — mono `<dl>` fact sheet. For anything that is genuinely data.
- `.ledger` / `.row` / `.verdict` — the build log. **The signature element.** One per site.
- `.card` / `.grid` — the product grid.
- `.flow` — numbered process steps. Only when order carries meaning.
- `.chip` — links and CTAs.
- `.status` — `--live` (solid clay) / `--review` (solid amber) / `--build` (hollow rust ring).

**Motion:** one orchestrated page-load sequence (`.rise`) and nothing else. `prefers-reduced-motion`
is respected and must stay respected.

**Structure encodes truth.** Numbered markers only where order is real. Don't decorate.

---

## 6. Product status — the source of truth

Every page must agree with this table. **The current live site does not.** Update this table
first, then the pages — never the reverse.

| Product | Type | Status | Notes |
|---|---|---|---|
| CloseOnes | iOS app | **Live** | v1.1.5. Magic-link auth, yearly subscription. |
| Kongvene | iOS app | **Live** | Site: kongvene.com. |
| LaunchMaxx | iOS + Google Play | **In review** | Formerly "LaunchPad". Site: maribella83.github.io/launchmaxx-website. |
| The Grove | app | **In review** | HOA app itself. Strongest revenue potential. |
| Good Call | app | **In development** | Daily scenario game, young adults. Site: goodcallgame.com (live, not yet open). |
| Alongside | app | **Coming soon** | Caregiver companion. |
| WithMe Pet | app | **In development** | Live site wrongly says "Just Launched". |
| The Shielded Path | app | **Pulled — rebuilding** | See §7. Most urgent. |
| **ApplyWorthy** | **web tool, not an app** | **In development** | B2B2C licensing. Seeking design partners. |
| **Grove Hub** | **platform, not an app** | **Site live, not open** | grovehub.io. Consumer/board face of The Grove — separate from the App Store submission. |
| **YouByProxy** | **platform, not an app** | **Site live, not open** | youbyproxy.com. Two-sided relocation marketplace. Deep dive: youbyproxy.html. |

**Count: 8 apps + 1 web tool = 9 products, plus 2 platforms tracked separately** (Grove Hub,
YouByProxy — see §8's Platforms section). If this table and the live site ever disagree, fix
the table first, then the pages.

Facts: LLC registered in Utah, **founded 2024**. Headcount 1. Funding: none, bootstrapped,
year two. Revenue: subscriptions + B2B2C licensing. No ads. No data sold.

Contact: `thecirclerootechllc@gmail.com` · `github.com/maribella83` ·
`linkedin.com/in/maribel-saenthavisouk-1b42bb58`

---

## 7. The Shielded Path — handle with care

**This is the most urgent correction on the internet right now.**

The live site markets this app as *"Under Apple Review"* with *"always-on protection verified
by NCMEC and IWF."* Both are wrong, and the second is the serious one: it is a child-safety
claim for a capability the app could not deliver.

What actually happened: the app was approved and live, but the Safari filtering users were
paying for cannot work on iOS without a Network Extension entitlement Apple wasn't going to
grant. Maribel pulled her own approved app rather than sell a promise she couldn't keep, and
is rebuilding the architecture on DNS.

**Rules:**
- Remove every "verified by", "always-on", and "under review" claim immediately.
- Do not soften what happened. The pull is the strongest thing in the portfolio — it's the
  charter costing her something.
- Do not give a ship date for the rebuild.
- No email capture on the status page. Nothing is being sold.

---

## 8. Site map (target)

```
/                   The thesis, the charter, the build log, the portfolio, the Platforms
                    section (#platforms — YouByProxy, Grove Hub, and a preview card per
                    product site), contact
/applyworthy        Standalone. The cold-outreach destination for workforce-dev orgs.
/apps/              Portfolio index → a page per product, honest status on each
/the-grove.html     The Grove deep dive — problem, features, build status, pricing
/applyworthy.html   ApplyWorthy deep dive — problem, how it works, design-partner pitch
/youbyproxy.html    YouByProxy deep dive — problem, how it works, provider categories, status
/founder            The sixteen years + AI practice + résumé
/privacy /terms     Currently dead links (href="#"). Required for App Store submissions.
```

Every page: `<link rel="stylesheet" href="styles.css">`, shared nav, shared footer.
Footer line: *No ads. No data selling. Priced for access. Ever.*

---

## 9. Before anything ships

- [ ] No banned phrase from §2 survives anywhere
- [ ] Every status matches §6
- [ ] Every NCMEC/IWF/"under review" claim gone from every property (§7)
- [ ] No dead `href="#"` links
- [ ] Every new color derived from the arc, contrast checked
- [ ] Keyboard focus visible on every interactive element
- [ ] Reads correctly at 380px
- [ ] Copyright year current
