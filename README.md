# azaan-hisn

Hisn al-Muslim (حصن المسلم) translations used by the **Azaan** prayer app.

[hisnmuslim.com](https://hisnmuslim.com) publishes Arabic and English through its
JSON API (`/api/{ar,en}/…`). Its other translations exist only as website pages
(`/i/{lang}/{n}`). This repository holds those translations converted into the
**same JSON format as the official API**, so the app can download them per
language.

| Folder | Language |
|---|---|
| `bn` | বাংলা (Bengali) |
| `es` | Español (Spanish) |
| `fa` | فارسی (Persian) |
| `ha` | Hausa |
| `hi` | हिन्दी (Hindi) |
| `id` | Bahasa Indonesia (also used for Malay) |
| `pt` | Português (Portuguese) |
| `so` | Soomaali (Somali) |
| `sw` | Kiswahili (Swahili) |
| `th` | ไทย (Thai) |
| `zh` | 中文 (Chinese) |

## Structure

- `<lang>/husn_<lang>.json`: the chapter index (`ID`, `TITLE`, `AUDIO_URL`, `TEXT`).
  `TEXT` is relative (`<id>.json`).
- `<lang>/<id>.json`: the duas of one chapter (`ID`, `ARABIC_TEXT`,
  `TRANSLATED_TEXT`, `REPEAT`, `AUDIO`).

The Arabic text, repeat counts and audio links come from the official English
API record with the same dua ID. Only the translation comes from the website.
A dua that has no translation on the website keeps the English text.

## Serving

The app reads a fixed tag through jsDelivr, so files already cached in the app
never change underneath it:

```
https://cdn.jsdelivr.net/gh/mohamed-yahia-mahmoud/azaan-hisn@v1/<lang>/husn_<lang>.json
```

To publish changes, push a new tag (`v2`, …) and update
`HisnLanguages.translationsBaseUrl` in the app.

## Regenerating

The exporter lives in the Azaan app repository at `tool/hisn_export.py`:

```
python3 tool/hisn_export.py --out <this-repo>
```

All content belongs to its original authors and translators at hisnmuslim.com.
It is shared here unchanged, for free, ad-free da'wah use.
