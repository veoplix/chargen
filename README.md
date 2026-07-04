# [CharGen](https://chargen.veoplix.com)

CharGen is a browser-based character name generator built to create original, pronounceable, and stylistically varied names for fictional people, heroes, villains, wizards, monsters, and general-purpose characters. It combines multilingual phonetic patterns with mood tuning and archetype-driven shaping, then wraps the results in a practical workflow for reviewing, saving, copying, and researching name candidates.

The project is implemented as a single static HTML page with embedded CSS and JavaScript. There is no backend, no build step, and no database. Everything runs in the browser.

## Purpose

CharGen exists to help users quickly generate fictional character names that sound believable, distinct, and fitting for a chosen tone or role. It is designed for situations where a name should feel invented, readable, and expressive rather than generic or random.

It is especially useful when a name needs to be:

- original rather than copied from a known character or existing word
- easy to pronounce aloud
- shaped to fit a narrative role or fantasy archetype
- adaptable to different tones, moods, and genres
- easy to shortlist and reuse later

Typical use cases include:

- naming player characters, NPCs, and enemies in games
- creating heroes, villains, wizards, and monsters for worldbuilding
- naming characters for novels, comics, animation, and film
- generating names for tabletop RPG campaigns
- exploring cast ideas for fantasy, sci-fi, horror, and adventure settings
- finding temporary or final names during concept development

## What The Tool Does

CharGen generates invented character names and presents each one as a rich result card. Every card includes:

- the generated name
- a segmented pronunciation hint
- a style tag showing the language family or mixed style used
- a syllable count
- a mood indicator
- an archetype indicator
- text-to-speech buttons for multiple languages
- one-click copy
- a favourite toggle
- a web search shortcut
- social handle check links across multiple platforms
- a remove button for dismissing a generated name from the current list

In addition to automatic generation, the tool lets users create custom names manually, save favourites in the browser, and manage dedicated custom and favourite views.

## Core Features

### 1. Automatic Character Name Generation

The main Generate view produces batches of character names immediately on load and continues generating more as the user scrolls.

- initial batch size: 7 names
- infinite scroll batch size: 5 names
- available name lengths: 2 to 4 syllables
- supported moods: `neutral`, `happy`, `scary`, `scifi`, `fantasy`, `funny`
- supported archetypes: `regular`, `hero`, `villain`, `wizard`, `monster`

Each generated entry receives a unique ID and can be copied, saved to favourites, researched externally, or removed from the current result feed.

### 2. Multilingual Phonetic Engine

CharGen blends weighted phonetic inventories inspired by these language sets:

- English
- Polish
- Spanish
- German
- French
- Italian
- Portuguese
- Mixed mode, which combines a dominant language with a secondary accent language

For each language, the generator defines:

- onset consonants and consonant clusters
- vowel nuclei
- coda endings
- probabilities for vowel starts and closed syllables

This keeps the output much closer to pronounceable fictional names than to random letter strings.

### 3. Archetype-Based Generation

Archetypes are one of CharGen’s central features. They do not simply label results after the fact. Each archetype actively changes how names are built.

The implemented archetypes aim for these effects:

- `regular`: balanced names for broad everyday or neutral character use
- `hero`: cleaner, brighter, more noble-sounding names
- `villain`: darker, sharper, harsher names with more menace
- `wizard`: mystical, archaic, arcane-sounding names
- `monster`: heavier, rougher, more creature-like names

Archetypes influence:

- which language styles are more likely to be selected
- which consonants, vowels, and endings are preferred
- how likely syllables are to start with vowels or end with hard codas
- how final name endings are refined after generation

This gives CharGen much more control over narrative flavor than a simple random-name generator.

### 4. Mood-Based Output Shaping

Moods work alongside archetypes and further adjust the phonetic weighting.

The implemented moods aim for these effects:

- `neutral`: balanced default output
- `happy`: softer, brighter, lighter-sounding names
- `scary`: harsher, darker, more guttural names
- `scifi`: sharper, more synthetic or futuristic names
- `fantasy`: flowing, archaic, mystical names
- `funny`: bouncy, whimsical, playful names

Mood affects:

- consonant selection
- vowel selection
- ending selection
- the likelihood of open versus closed syllables

Because mood and archetype are combined, the same archetype can still produce very different results depending on the selected emotional or genre tone.

### 5. Archetype-Aware Ending Refinement

After syllables are generated, CharGen applies additional finishing logic to make the final result read more like a character name.

This refinement stage can:

- soften overly harsh endings for certain archetypes
- add or favor stronger endings for darker archetypes
- bias endings toward softer or harder phonetic profiles
- keep the final adjustment inside the active language inventory when possible

This is one of the main reasons the output feels more character-oriented than purely phonetic assembly.

### 6. Pronunciation Preview

Every result includes a pronunciation string rendered as dot-separated syllable chunks, for example in a format like `/ka·ren/`.

This is not a strict phonetic transcription. Its purpose is to help the user quickly judge rhythm, syllable shape, and speakability.

### 7. Native Text-to-Speech Playback

Each result card includes speech buttons for:

- English
- Polish
- Spanish
- German
- French
- Italian
- Portuguese

CharGen uses the browser Web Speech API and tries to select a suitable local voice for the requested language when available. This is useful for hearing how a fictional name lands across different pronunciation contexts.

For the most reliable speech synthesis behavior and voice availability, CharGen works best in Google Chrome.

### 8. Custom Name Creation

The Custom view allows manual entry of character names.

Current custom-entry behavior:

- trims leading and trailing whitespace
- collapses repeated spaces to single spaces
- capitalizes the first character
- derives a simple pronunciation display from the typed value
- estimates syllable count by vowel-group matching
- stores the entry locally in the browser

Custom names are displayed with the same result-card tooling as generated names, including speech playback, favourite toggling, copy support, search, social links, and deletion from the custom list.

### 9. Browser-Saved Favourites

Any generated or custom name can be added to favourites using the heart icon.

Favourites behavior:

- saved in `localStorage`
- persist between browser sessions on the same browser profile
- can be removed again by toggling the heart
- are shown in a dedicated Favourite view
- can also be deleted directly from the favourites list

CharGen uses these storage keys:

- `chargen-favorites-v1`
- `chargen-custom-words-v1`

No cloud sync is implemented.

### 10. One-Click Copy

Clicking a generated or custom name copies it to the clipboard and briefly changes the label to `Copied!`.

This makes it easy to collect shortlists while reviewing many options quickly.

### 11. Fast Search And Social Handle Checks

Each result card includes a direct Google search shortcut and a broad set of social profile or handle checks.

Built-in external shortcuts include:

- Google Search
- YouTube
- Facebook
- X
- Instagram
- TikTok
- Twitch
- Reddit
- Pinterest
- Threads
- Snapchat
- Tumblr
- Bluesky

These shortcuts open the corresponding external pages and help users research whether a character name is already strongly associated with another identity, creator, character, or social presence.

### 12. Dismiss Generated Results

Generated names can be removed individually from the current results list using the trash action on each generated card.

This is useful when reviewing large batches and narrowing the visible set without affecting saved favourites or custom entries.

## Interface Overview

CharGen is organized into three views.

### Generate

The main exploration workspace.

- choose syllable length from 2 to 4
- choose a mood from six presets
- choose an archetype from five presets
- receive an initial batch automatically
- keep scrolling to load additional results
- remove weak candidates directly from the current list

### Custom

Manual entry and storage.

- type a custom character name
- press Create or hit Enter
- review it using the same pronunciation and shortcut tools as generated results
- delete entries when they are no longer needed

### Favourite

Shortlist management.

- view saved favourites
- replay pronunciation
- search or inspect handles externally
- remove entries directly from the favourite list

## How The Generator Works

CharGen does not use a language model, a backend AI service, or a fixed dictionary of ready-made names. It uses handcrafted weighted phonetic rules and several post-processing stages.

At a high level, generation works like this:

1. Select a global style using archetype-weighted language preferences.
2. Convert that choice into a style plan with either one dominant language or a dominant-plus-accent mixed strategy.
3. For each syllable, choose whether it begins with an onset or a vowel.
4. Pick consonants, vowels, and optional endings using base language weights modified by both mood and archetype.
5. Smooth transitions between neighboring syllables to reduce repeated boundaries and awkward vowel collisions.
6. Clean repeated clusters and overlong letter sequences.
7. Refine the final ending according to the selected archetype.
8. Capitalize the result and attach metadata for display.

## Built-In Output Quality Rules

The implementation includes several safeguards to keep names more readable and pronounceable.

Examples include:

- avoiding awkward `qu` plus incompatible vowel combinations
- avoiding problematic `y` and `j` sequences such as `jyi`
- reducing unnatural word-initial `y` vowels in some language contexts
- recognizing multi-letter clusters like `sch`, `sz`, `th`, `ng`, and `qu` as single boundaries during cleanup
- smoothing repeated syllable boundaries
- collapsing overlong repeated vowels and consonants

These rules do not guarantee perfect linguistics, but they materially improve the quality and readability of generated names.

## When CharGen Is Most Useful

CharGen is strongest during ideation, naming exploration, and early character development.

It is especially useful when you want to:

- create a large batch of fictional names quickly
- keep names aligned with specific character roles
- experiment with genre tone without rewriting naming rules manually
- discover names that sound distinctive but still pronounce naturally
- build a shortlist for a cast of heroes, villains, mages, monsters, or neutral NPCs
- check whether a candidate is already visually tied to existing online identities or fandom use

It works well for solo creators, writers, game developers, dungeon masters, and anyone building fictional worlds or casts.

## Project Structure

The repository for CharGen is intentionally minimal:

- `index.html`: the full application, including layout, styling, and logic
- `README.md`: this readme file
- `LICENSE`: project license

There is no package manifest, no bundler configuration, and no backend service.

## Running The Project

Because CharGen is a static client-side app, setup is simple.

### Option 1: Use The Hosted Project Page

Open the live project page:

[`https://chargen.veoplix.com`](https://chargen.veoplix.com)

This is the fastest way to use CharGen with no local setup.

For the best speech synthesis experience, Google Chrome is recommended.

### Option 2: Open Directly

Open `index.html` in a modern browser.

### Option 3: Serve Locally

For more predictable browser behavior, serve the folder with a small local web server.

Example:

```powershell
cd chargen
python -m http.server 8000
```

Then open `http://localhost:8000`.

Using a local server can help avoid browser differences around clipboard access or speech synthesis behavior.

## Dependencies And External Services

CharGen has no package-managed runtime dependencies, but it does rely on external browser-loaded assets and platform APIs:

- Tailwind CSS CDN
- Font Awesome CDN
- Google Fonts for `Space Grotesk`
- browser `speechSynthesis` support
- browser `localStorage` support
- browser clipboard support

External destinations used by the shortcut buttons include:

- Google Search
- YouTube
- Facebook
- X
- Instagram
- TikTok
- Twitch
- Reddit
- Pinterest
- Threads
- Snapchat
- Tumblr
- Bluesky

If any of these external services are unavailable, the generator itself still works, but related research shortcuts may not.

## Privacy And Data Handling

CharGen is primarily local-first in behavior.

What stays local:

- generated results shown in the current session
- saved favourites in browser `localStorage`
- saved custom names in browser `localStorage`
- speech playback handled by the browser

What leaves the browser:

- external searches and profile or handle checks opened on third-party websites

There is no dedicated CharGen backend collecting or storing user data in the current implementation.

## Limitations

CharGen is a focused ideation tool, not a complete identity-clearance or canon-management system.

- It does not verify trademark status.
- It does not verify actual handle availability.
- It does not validate lore consistency across your own project.
- It does not guarantee perfect pronunciation in every language.
- It relies on browser support for speech synthesis, clipboard access, and `localStorage`.
- Speech quality and voice availability vary by browser and operating system.
- Generated names are weighted-random outputs, so quality varies by run and by taste.

## Why CharGen Is Distinctive

CharGen is more than a random fantasy name picker. Its value comes from the combination of:

- multilingual weighted phonetic generation
- mood-based sound shaping
- archetype-driven structure and finishing rules
- syllable smoothing and orthographic cleanup
- built-in pronunciation preview and speech playback
- broad social and web research shortcuts
- a lightweight zero-backend browser implementation

That makes it especially effective for fast character-naming exploration where tone, role, and pronounceability all matter.

## Summary

CharGen is a compact character naming workbench for generating original-sounding fictional names with controllable tone and role. It helps users move from raw name exploration to shortlist review inside a single page: generate, listen, compare, save, remove, and research further.

If your goal is to name heroes, villains, wizards, monsters, or general fictional characters quickly and with more stylistic control than a basic random generator, CharGen is built for that exact stage of the creative process.