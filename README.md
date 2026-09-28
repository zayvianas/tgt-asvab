# TGT ASVAB Prep — static site

Plain static files. No build step, no dependencies.

## Files
- index.html ............ hub page linking to both decks
- words.html ............ Word Deck, 250 vocabulary cards
- formulas.html ......... Formula Deck, 61 math and word-problem cards
- manifest.webmanifest .. makes it installable to a phone home screen
- sw.js ................. service worker, so it works offline after first load
- vercel.json ........... clean URLs + no-cache on the service worker
- icon-*.png ............ app icons

## Deploy to Vercel (fastest path, from your computer)
1. Unzip this folder.
2. In Terminal: `cd` into the folder.
3. Run: `npx vercel login` (opens your browser, one click)
4. Run: `npx vercel --prod`
   Accept the defaults. When it asks the project name, use something like `tgt-asvab`.
5. It prints a live URL. That's the site.

## Point asvab.learnwithtgt.com at it
In the Vercel project: Settings → Domains → Add → type `asvab.learnwithtgt.com`.
Vercel then shows one DNS record to create where learnwithtgt.com's DNS lives:
- Type: CNAME
- Name: asvab
- Value: cname.vercel-dns.com
Save it, and the domain goes live once DNS propagates (usually minutes).

## Updating later
Replace the files and run `npx vercel --prod` again from the same folder.
The service worker cache is versioned in sw.js — bump "tgt-asvab-v1" to v2 when you
change the decks, so returning phones pick up the new version.
