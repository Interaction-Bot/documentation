---
description: The 100 languages supported by Interaction Bot and how flags map to languages.
---

# Languages and flags

Interaction Bot translates **100 languages**. The source language is detected automatically, you only choose the **target** language.

In Discord, `/languages` shows the same list.

## Supported languages

| Language | Code | Language | Code |
| --- | --- | --- | --- |
| Afrikaans | `af` | Lingala | `ln` |
| Albanian | `sq` | Lithuanian | `lt` |
| Amharic | `am` | Luxembourgish | `lb` |
| Arabic | `ar` | Macedonian | `mk` |
| Armenian | `hy` | Malagasy | `mg` |
| Asturian | `ast` | Malay (macrolanguage) | `ms` |
| Azerbaijani | `az` | Malayalam | `ml` |
| Bashkir | `ba` | Marathi | `mr` |
| Belarusian | `be` | Modern Greek (1453-) | `el` |
| Bengali | `bn` | Mongolian | `mn` |
| Bosnian | `bs` | Nepali (macrolanguage) | `ne` |
| Bulgarian | `bg` | Northern Sotho | `ns` |
| Burmese | `my` | Norwegian | `no` |
| Catalan | `ca` | Occitan (post 1500) | `oc` |
| Cebuano | `ceb` | Oriya (macrolanguage) | `or` |
| Central Khmer | `km` | Panjabi | `pa` |
| Chinese (Simplified) | `zh` | Persian | `fa` |
| Chinese (Traditional) | `zh-tw` | Polish | `pl` |
| Croatian | `hr` | Portuguese | `pt` |
| Czech | `cs` | Pushto | `ps` |
| Danish | `da` | Romanian | `ro` |
| Dutch | `nl` | Russian | `ru` |
| English | `en` | Scottish Gaelic | `gd` |
| Estonian | `et` | Serbian | `sr` |
| Finnish | `fi` | Sindhi | `sd` |
| French | `fr` | Sinhala | `si` |
| Fulah | `ff` | Slovak | `sk` |
| Galician | `gl` | Slovenian | `sl` |
| Ganda | `lg` | Somali | `so` |
| Georgian | `ka` | Spanish | `es` |
| German | `de` | Sundanese | `su` |
| Gujarati | `gu` | Swahili (macrolanguage) | `sw` |
| Haitian | `ht` | Swati | `ss` |
| Hausa | `ha` | Swedish | `sv` |
| Hebrew | `he` | Tagalog | `tl` |
| Hindi | `hi` | Tamil | `ta` |
| Hungarian | `hu` | Thai | `th` |
| Icelandic | `is` | Tswana | `tn` |
| Igbo | `ig` | Turkish | `tr` |
| Iloko | `ilo` | Ukrainian | `uk` |
| Indonesian | `id` | Urdu | `ur` |
| Irish | `ga` | Uzbek | `uz` |
| Italian | `it` | Vietnamese | `vi` |
| Japanese | `ja` | Welsh | `cy` |
| Javanese | `jv` | Western Frisian | `fy` |
| Kannada | `kn` | Wolof | `wo` |
| Kazakh | `kk` | Xhosa | `xh` |
| Korean | `ko` | Yiddish | `yi` |
| Lao | `lo` | Yoruba | `yo` |
| Latvian | `lv` | Zulu | `zu` |

## Flags

Flag translation understands **175 flags**. A flag stands for the main language of the country, for example 🇫🇷 gives French, 🇬🇧, 🇺🇸 and 🇨🇦 give English, 🇧🇷 and 🇵🇹 give Portuguese, 🇨🇭 gives German and 🇧🇪 gives Dutch. The flags reach **68 of the 100 languages**. The other languages are reached with [`/translate`](commands.md#translate) or with the translation rules, which take a language by its name.

Special flags:

* 🏴‍☠️ **Pirate flag**: the message is translated in English, then written in pirate speech.
* 🇮🇱 **Israel**: Hebrew. 🇧🇩 **Bangladesh**: Bengali. 🇧🇼 **Botswana**: Tswana.
* 🏴 **Wales** and 🏴 **Scotland** (the regional flags): Welsh and Scottish Gaelic.

{% hint style="info" %}
If a flag does nothing, check that flag translation is not switched off for the channel on the [Flags](../website/dashboard/flag-translation.md) page, and that the message has some text to read. Flags are not affected by the exceptions of the server.
{% endhint %}
