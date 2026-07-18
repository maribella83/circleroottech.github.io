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

## 3. Color — one warm arc

Not a set of picks. A **rule**: every color lives on the arc **hue 38°–60°**, and position on
the arc is a function of lightness — *the darker the tone, the redder; the lighter, the more
golden.* The accent sits one step past the top. Nothing is off-family.

```css
--ink:      #2C160F;  /* L.23  H38  — text, dark bands   */
--rust:     #79371B;  /* L.42  H42  — depth              */
--clay:     #A1491E;  /* L.51  H44  — the primary        */
--stone:    #725B51;  /* L.49  H45  — secondary text     */
--paper:    #F1DFD5;  /* L.92  H51  — the base           */
--paper-hi: #F9F0EB;  /* L.96  H51  — raised surfaces    */
--amber:    #EB9341;  /* L.74  H60  — the one highlight  */

--text-2:   #573A30;  --text-3:   #4B2C21;   /* body tones on light */
--on-dark-1:#E4D4CB;  --on-dark-2:#CEB9AE;   /* body tones on ink   */
--on-dark-3:#A38D83;  --on-accent:#341A02;
--rule:     rgba(44,22,15,.16);
```

**Adding a color?** Don't pick one. Choose a lightness, read the hue off the arc
(`H = 38 + (L − 0.23) × 20`), and set chroma to match its neighbors. Then check contrast.

**Accessibility floor — already verified, keep it:** every text pairing passes WCAG AA.
`ink/paper` 13.2:1 · `stone/paper` 4.9:1 · `clay/paper` 4.7:1 · `on-accent/amber` 6.8:1.
Never introduce a pairing below 4.5:1 for body text or 3:1 for large display type.

**Spend boldness in one place.** Amber is the *only* highlight, used in small doses: verdict
pills, charter dashes, the headline underline. If amber is on screen three times in one
viewport, cut two.

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
| LaunchMaxx | iOS + Google Play | **In review** | Formerly "LaunchPad" — rename everywhere. |
| The Grove | app | **In development** | HOA. Strongest revenue potential. |
| Kongvene | app | **In development** | Mahjong circles. Not on the live site at all. |
| Alongside | app | **In development** | Caregiver companion. |
| WithMe Pet | app | **In development** | Live site wrongly says "Just Launched". |
| The Shielded Path | app | **Pulled — rebuilding** | See §7. Most urgent. |
| **ApplyWorthy** | **web tool, not an app** | **In development** | B2B2C licensing. Seeking design partners. |

**Count: 7 apps + 1 web tool = 8 products.** The live site says five. The résumé says six.
Both are stale.

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
/                   The thesis, the charter, the build log, the portfolio, contact
/applyworthy        Standalone. The cold-outreach destination for workforce-dev orgs.
/apps/              Portfolio index → a page per product, honest status on each
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
