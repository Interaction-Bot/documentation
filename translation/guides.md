---
description: Ready-to-use setups for common situations.
---

# Setup guides

Step by step recipes. Each one uses the [dashboard](../website/dashboard/) unless a command is mentioned.

## 1. An international community: one channel per language

**Goal**: members write in their own language, in their own channel, and read everybody.

1. Create the channels `#english`, `#francais`, `#espanol`.
2. Use a [translation group](../commands/groups.md): `/group create name:Community`, then `/group set-channel` for each channel with its language (or use the dashboard page _Translation Groups_).
3. Check with `/check-permissions` that the bot can read and write in the three channels.

A message in any of the channels is translated into the other two. Free servers can have 1 group of 3 channels, premium servers 5 groups of 5.

## 2. Translate a single channel into another

**Goal**: staff write in English in `#announcements`, and French members read `#annonces`.

1. _Channel translation_ > _Add a configuration_.
2. **Channel** `#announcements`, **Sending channel** `#annonces`, **Language** French.
3. Style _Webhook_ for a natural look. Save.

## 3. Translate what some members write

**Goal**: Japanese speakers (role `@japanese`) write anywhere, everybody reads English.

1. _Role translation_ > _Add a configuration_.
2. **Role** `@japanese`, **Language** English, choose a **Sending channel** or leave it empty to answer in the same channel.
3. Add a [blacklist](../website/dashboard/blacklist.md) entry for channels where you don't want translations (premium).

## 4. One-click translation for everybody

**Goal**: any member can translate any message of `#general`.

* Run `/flags set channel:#general flags:🇬🇧 🇫🇷 🇪🇸`: the bot adds the flags under each message, one click translates.
* Or do nothing: members can add any flag reaction themselves, see [Flag translation](flags.md).

## 5. Translate a whole section of the server

**Goal**: all the channels of the category "International" are translated into English.

1. _Category translation_ > _Add a configuration_ with the category and the language English.
2. Optionally set a **Sending channel** and _Delete translation_ so translations don't pile up.

## 6. Read the messages of a channel aloud

1. Join a voice channel and run `/tts start` in the text channel: the messages of this chat are read aloud for as long as the session lasts. To read one text only, run `/tts say`.
2. For a channel read automatically: `/tts-channel set channel:#chat` (or the dashboard page _Text to speech_). See [Text to speech commands](../commands/tts.md).

## 7. Transcribe a voice channel

Run `/transcribe start` in a text channel while in a voice channel, or enable `/transcribe auto enable` to start it when someone joins. See [Voice](../audio/voice.md) and the dashboard page [Speech to text](../website/dashboard/speech-to-text.md).

## 8. A FAQ that answers by itself

Create a group on the dashboard page [FAQ](../website/dashboard/faq.md), add questions and answers, choose the channels and turn on _Auto reply_. See [FAQ and /ask](../qa/faq.md).
