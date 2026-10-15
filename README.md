# Mona Bella Jewelry: Arabic name necklace preview

A prototype for **Mona Bella Jewelry** (@monabella_jewelry, monabellajewelry.com, a Shopify store, Canada).
She has a preview tool for regular name necklaces, but it shows only one font. On Instagram she asked for one
that shows a customer's name in different Arabic calligraphy fonts. A call was planned for Monday 2026-10-12.

- `arabic-name-preview.html`: one self-contained page (HTML, CSS, JS, Google Fonts). No build step, no backend.
- Published preview (private, share it from the page's Share menu): https://claude.ai/artifact/5sBwPGr8PwSVEDdHehnscB
  To update it, publish this file with that URL.

## What it does

- Type a name in English or Arabic. English names are looked up in a list of about 150 common names and words.
  When a name has more than one spelling, the customer picks one. Names that aren't on the list get a rough
  guess based on the sound and a note that the calligrapher confirms the spelling. There's an Arabic letter keyboard.
- Live canvas preview: the name as a metal pendant on a cable chain. Gold, silver or rose gold finish; small,
  medium or large size; black velvet or linen background. Product only, no people.
- The same name in 15 calligraphy styles (Diwani, Ruqʿah, Nastaʿlīq, Naskh, Kufi, Fatimid Kufi and more).
  Tap one to put it on the necklace.
- "Copy order details" copies name, spelling, style, finish, size and chain length (14/16/18/20 in) for her
  product page's "Add custom details" box.

## Free and Pro (added 2026-10-12)

The page opens as the **free version**. A "Pro features" button in the header opens a panel that lists
what Pro adds, with a Free vs Pro table and a "Try Pro in this preview" button. Locked options carry a
small "Pro" tag, and tapping one opens the panel at that feature.

- **Free:** name preview (English list, rough guess, Arabic keyboard), 5 styles (Diwani, Ruqʿah,
  Nastaʿlīq, Naskh, Kufi), 3 finishes, 3 sizes, 4 chain lengths, black velvet background, copy order details.
- **Pro, working in this preview:** the other 10 styles, charms on the chain (heart, crescent moon, star,
  turquoise heart), rosary style chains (white pearls, gold beads, turquoise beads), linen background.
- **Pro, listed only (built when it goes on her store):** add to cart with the details attached, smart
  spelling for any name, her calligrapher's own styles, a preview picture saved with each order, the names
  and styles customers try most.

Which features are free and which are Pro is set in the `STYLES` list (`pro` flag) and the
`data-pro` attributes on the option buttons.

## Hosting (free): GitHub Pages

**Live (noindex) at https://msrshahrukh100.github.io/monabella-jewelry/ since 2026-10-15.** The repo is
public for that. No subdomain for now (owner's choice); steps 3 and 4 below are for later.

`.github/workflows/pages.yml` publishes `arabic-name-preview.html` as `index.html` on every push to `main`.
No cost, no server.

1. The repo is `msrshahrukh100/monabella-jewelry` (private). Make it public for free Pages:
   `gh repo edit msrshahrukh100/monabella-jewelry --visibility public --accept-visibility-change-consequences`
2. Settings > Pages > Source: **GitHub Actions**. The site is then at
   `https://msrshahrukh100.github.io/monabella-jewelry/`.
3. Subdomain `monabella.scribblewithai.com` (temporary): in Squarespace Domains > scribblewithai.com > DNS,
   add a CNAME record `monabella -> msrshahrukh100.github.io`. Then repo Settings > Pages > Custom domain
   `monabella.scribblewithai.com`, and tick "Enforce HTTPS". Also verify scribblewithai.com under GitHub
   account Settings > Pages (a TXT record), so no other GitHub account can claim the subdomain.
   The workflow adds `<meta name="robots" content="noindex, nofollow">` to the published copy, so it
   stays out of search results.
4. Taking it down: delete the `monabella` CNAME in Squarespace **first**, then remove the custom domain
   and turn Pages off.

GitHub Pages on a free GitHub plan needs a **public** repo (private repos need GitHub Pro). If the repo
should stay private, use Cloudflare Pages instead (also free, works with private repos): connect the repo,
no build command, and add a `_redirects` file with `/ /arabic-name-preview.html 200`, or rename the file to `index.html`.

## Next steps (to settle with her)

- Put it on Shopify: a Custom Liquid block in her theme (quick) or a private app with a theme app block
  (recommended). Send the choices as line item properties so they show on the order.
- Her current single-font widget is probably a third-party app. Hide or replace it.
- Swap in her calligrapher's own styles if she has font files.
- Price per style needs product variants. Saving the preview image with the order needs a small backend.
