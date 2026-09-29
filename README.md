# LumaLauncher - Community Translations

This is the home of all LumaLauncher translations. **Anyone can add a language** by opening a
pull request - once it's merged, every LumaLauncher user sees it in **Settings -> Language**
automatically ( the launcher pulls this repository at runtime ).

Only `en/` (English) is bundled inside the launcher itself as the offline fallback and official language. Everything
else lives here.

> **Note:** Ukrainian (`uk/`) is already being actively developed by the team. Please do not open pull requests
> for Ukrainian — they will not be accepted.

## Repository layout

```text
languages/
  en/ <- the reference/example language, never translate this one
    lang.json <- all translatable strings
    en.webp <- its flag
  fr/ <- example of a community language
    lang.json
    fr.webp
```

## Adding or updating a language

1. **Fork** this repository.
2. **Copy the `en/` folder** and rename it to your language code ( e.g. `fr/` -> `languages/fr/` ).
3. **Translate every string** in `languages/fr/lang.json`. Keep placeholders like `{count}`,
   `{name}`, `{time}`, `{version}` exactly as they are - just move them to the natural
   position for your language.
4. **Fill in the `meta` block** at the top:

   ```json
   {
     "meta": {
       "name": "French",
       "nativeName": "Français",
       "shortName": "fr"
     }
   }
   ```

   | Field        | Description                          | Example     |
   | ------------ | ------------------------------------ | ----------- |
   | `name`       | Language name in English             | `"French"`  |
   | `nativeName` | Language name in the language itself | `"Français"`|
   | `shortName`  | Language code matching the flag file | `"fr"`      |

5. **Add a flag** `languages/fr/fr.webp` next to `lang.json`. Flags render at 20×15 px with
   `object-fit: cover` - any reasonable aspect-ratio image works ( flagcdn.com `w40` files are a
   good source ).
6. **Open a pull request**. See `.github/PULL_REQUEST_TEMPLATE.md` for the expected format.

## Structure of `lang.json`

`lang.json` is organized into categories so you can translate one screen at a time. All values
are strings. Key names tell you exactly where the string appears in the app
( e.g. `settings_window_mode` is the "Window mode" label in Settings ).

| Category          | What it covers                                                              |
| ----------------- | --------------------------------------------------------------------------- |
| `nav`             | Sidebar navigation labels (Home, Skins, Instances, Screenshots, Settings).  |
| `home`            | Main screen: greeting, instance creation/import, groups, trending.          |
| `instances`       | Instance cards: play/stop/delete, cloud sync, desktop shortcuts, worlds.    |
| `screenshots`     | Screenshots viewer and the photo editor (crop, rotate, draw, brightness..).  |
| `content`         | Files inside an instance: mods, resourcepacks, shaderpacks, worlds..         |
| `browser`         | Content browser (Modrinth): search, filters, install flow, dependencies.    |
| `create_instance` | Instance creation wizard: version, loader, loader version.                 |
| `java`            | Java runtime download: providers, versions, memory, custom Java.            |
| `skins`           | Skin presets: model (classic/slim), capes, username, local presets.         |
| `login`           | LumaAuth & Microsoft sign-in/sign-up, password reset, device-code linking, email verification. |
| `accounts`        | Account list, friends, online/offline status.                               |
| `settings`        | Launcher settings: window mode, Java args & memory, logs, Linux shortcuts, proxy, BMCLAPI. |
| `options`         | In-game options mirror (accessibility, controls, sounds, video, chat..).     |
| `about`           | About screen: credits, folders, versions.                                   |
| `media`           | Media player keys (now playing, volume, playback).                          |
| `time`            | Relative time words (ago, recently, days, all day).                         |
| `common`          | Buttons/status strings shared across the launcher (OK, Cancel, Save..).      |

### Placeholders and fragments

- **Placeholders** look like `{name}`, `{count}`, `{server}`, `{error}` - keep them, reorder if
  your grammar needs it.
- Some home-screen entries are deliberate two-part fragments, e.g. `home_editing_prefix` = "Editing "
  and `nav_skins` = "Skins" combine into the page header "Editing Skins". Translate both parts
  naturally - the trailing space in `home_*_prefix` values is intentional.

## Checklist before submitting

- [ ] I copied `en/` and renamed it to my language code
- [ ] Every string is translated (no untranslated English leftovers)
- [ ] Placeholders (`{count}`, `{name}`, `{time}`, ..) are preserved
- [ ] The `meta` block is filled in correctly
- [ ] A WebP flag named `<code>.webp` sits next to `lang.json`
- [ ] `lang.json` is valid JSON

## Notes for maintainers

- English (`en/`) is the source of truth and is maintained in the LumaLauncher repository -
  please don't edit it in pull requests.
- Merged folders are picked up by the launcher without a release - no registry changes needed.