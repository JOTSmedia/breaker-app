# Breaker Billiards — Interactive Menu App

`breaker_billiards_app.html` is a complete, self-contained mobile web app. One file, no build
step, no server, no dependencies. The logo, QR code, and glassware photo are embedded directly,
so it works offline once loaded.

## Try it now
Open the file in any browser. On a phone it fills the screen like a native app.

## Put it live (pick one)

**Fastest — a link you can text or QR:**
1. Go to netlify.com/drop (free, no account needed to start).
2. Drag the HTML file onto the page.
3. You get a URL instantly. Point your existing table QR codes at it.

**On your own domain (breakerbilliards.com/menu):**
1. Rename the file `index.html`.
2. Upload it to a `/menu` folder via your host's file manager.
3. Done — it's at breakerbilliards.com/menu.

**Other one-drag options:** Cloudflare Pages, Vercel, GitHub Pages. All free at this size.

## "Add to Home Screen" — the app experience
Once it's on a URL, anyone can install it:
- **iPhone:** Share button → Add to Home Screen
- **Android:** ⋮ menu → Add to Home Screen

It then launches full-screen with no browser chrome — indistinguishable from an App Store app,
with none of the review process or the $99/year developer fee.

## Editing the menu
All content lives in one JavaScript object near the bottom of the file, starting with `const D = {`.
It is plain, readable data — no code knowledge needed.

- **New cocktail:** copy an existing line in `"cocktails"`, change the name, price `p`, description `d`,
  and tags `t`. Tags automatically become filter buttons.
- **New bottle:** find the category in `"spirits"` or `"beer"` and add `["Bottle Name"]`, or
  `["Bottle Name","Variant one, Variant two"]`. Add `,1` as a third value for a PREMIUM badge:
  `["Blanton's","",1]`.
- **Price change:** edit the number. `13` shows as $13, `14.5` shows as $14.50 automatically.
- **Specials:** `"week"` controls the weekly lineup. `from` and `to` are 24-hour times that drive
  the live "Happening Right Now" banner — set `from:19` for a 7PM start.

Save, re-upload. That's the whole update cycle.

## What the app does that paper can't

| Feature | Why it matters |
| --- | --- |
| **Rotating Tap Menu Section** | Integrated brand-blue draft beer card inspired by `breaker-billiards-menu/menu.html`, featuring Breaker IPA, Downeast Cider, Blue Moon, Yuengling, Modelo, Stella, and Guinness. |
| **Darts 1–4 Player Count Selector** | Interactive prompt allowing players to select 1, 2, 3, or 4 players with dynamic multi-column scoreboards for both Cricket and 501/301. |
| **Automatic 3-Dart Turn Switch** | Automatically tracks 3 darts per turn and smoothly advances to the next player after a 0.6s turn pause. |
| **Dual Shot-by-Shot Log Table** | Tracks scoring game points alongside a live, separate shot breakdown log for every throw (e.g. `PLAYER 1 · TRIPLE 20 (+60 PTS)`). |
| **Tagline Purge Enforcement** | Purged the corny tagline; strictly adheres to official brand motto ("SHOOT POOL. NOT PEOPLE."). |
| **Automatic Today's Specials Engine** | Reads device clock & date to automatically display "TODAY'S FEATURED DEALS" (e.g. Wednesday Ladies Night / Happy Hour Live) right at the top of the Specials tab. |
| **Photorealistic Rocks Glass Builder** | Faceted crystal tumbler with specular reflections, deep amber liquid gradient, crystal ice blocks, muddled orange/cherry garnish, and wafting natural wood smoke. |
| **Pub-Style Realistic Scorekeepers** | Pool scorekeeper set inside a deep green felt bed with Aramith 3D pool balls; Darts scorekeeper styled as a pub slate chalkboard with Winmau wire dartboard. |
| **100% Print PDF Menu Accuracy** | Aligned 100% with `breaker_trifold_print.pdf` (Removed invalid items like White Gummy Bear & Liquid Marijuana; added 8 Ball Mule, Fruit Fusion, Lemon Pop Martini, Porn Star Martini, Rack 'Em Up Margarita). |
| **100% ALL CAPS Typography** | Strict brand kit enforcement using Oswald, Montserrat, and Great Vibes fonts for high-impact venue presentation. |
| **Gift A Glass Corrected Copy** | Explicitly clarifies that Gift A Glass items ($14 Tall Boy 20oz / $10 Pint 16oz) are glassware purchases only (drinks NOT included). |

## Two notes

**Favorites reset when the page closes.** They're held in memory, since browser storage is
restricted in preview environments. Once you deploy to a real URL, making them permanent is a
five-line change — search for `const favs = new Set()` and I can swap in `localStorage`.

**Ordering isn't built in.** The La Fortaleza app you referenced is an ordering app; this is a
menu and discovery app. Adding a cart and checkout means payment processing, POS integration, and
staff workflow decisions — a real project, and worth scoping separately. If that's the goal, the
Old Fashioned builder is already the right skeleton for it.
