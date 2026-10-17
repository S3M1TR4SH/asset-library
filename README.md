# asset-library

Curated CC0 game assets (Kenney). See `catalog.json` for stable ids and `LICENSES.md` for attributions.

## Genre packs

`catalog.json` (v0.3.0) has a `packs` object with a starter set for `puzzle`, `merge`, `idle`, `runner`, `arcade`, and `shared`. Each pack lists asset ids: sprites, a background, UI (buttons, a panel, icons, a coin), two fonts, core SFX (tap, success, fail, coin, level up, game over), and a short music jingle. Every asset also has a `genres` array.

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
