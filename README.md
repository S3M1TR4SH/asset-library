# asset-library

Curated CC0 game assets. See `catalog.json` for stable ids and `LICENSES.md` for attributions.

## Genre packs

`catalog.json` (v0.4.0) has a `packs` object with a starter set for `puzzle`, `merge`, `idle`, `runner`, `arcade`, and `shared`. Each pack lists asset ids: sprites, a background, UI (buttons, a panel, icons, a coin), two fonts, core SFX (tap, success, fail, coin, level up, game over), a short Kenney jingle, and loopable background music. Every asset also has a `genres` array.

Background beds are `music.<genre>.1`, `music.<genre>.2` where a second loop exists, and `music.menu.1` on every pack. The Kenney jingles are still the short stingers (about 1–2 seconds).

Kenney does not publish a seamless CC0 music loop. The jingles are short stingers from Music Jingles (about 1–2 seconds), mono OGG and MP3.

To list the files for one pack:

```bash
jq -r --arg genre puzzle '
  . as $cat
  | $cat.packs[$genre].ids[] as $id
  | $cat.assets[]
  | select(.id == $id)
  | .path, (.formats.mp3 // empty)
' catalog.json | sort -u
```

`path` is the file to load (OGG for audio). `formats.mp3` is the alternate. Original `License.txt` files sit next to each source folder and are not catalog ids.

## Attribution

Games must show a credit when a catalog entry has `attribution_required` set to true. That flag is for CC-BY 3.0 and CC-BY 4.0 works. Show the entry's `attribution` string where players can read credits, including the title, author, license name, and license URL. An Incompetech credit looks like: "Title" Kevin MacLeod (incompetech.com) Licensed under Creative Commons: By Attribution 4.0 License http://creativecommons.org/licenses/by/4.0/

CC0 entries set `attribution_required` to false. The `attribution` text is still recorded, and showing it is optional. The v0.4.0 background tracks are CC0, so they do not require a credit.
