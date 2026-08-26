# AITS Public Downloads and User Guide

[繁體中文](README.md) | [English](README_EN.md)

AITS is a macOS menu bar AI assistant that generates suggested replies from the current screen and provides rewriting, translation, and proofreading for selected text. The app does not open a home window or show a Dock icon; all features are available from the menu bar or through hotkeys.

This repository provides public installers and user documentation only. It does not contain the source code, API keys, or private settings.

## Download the Latest Version

Latest version: AITS v0.2.4

- [Download AITS-0.2.4.dmg](https://github.com/White8709/AITS-Releases/releases/download/v0.2.4/AITS-0.2.4.dmg)
- [View the AITS v0.2.4 release](https://github.com/White8709/AITS-Releases/releases/tag/v0.2.4)
- SHA-256: `8db575ce5ec53afd63a79387bde1c3320f320ddbbd07d401bd35de8ebbe92f0b`

The current installer uses an ad-hoc signature and has not been signed with a Developer ID or notarized by Apple. macOS may display a security warning the first time you open the app.

## Installation

1. Download and open `AITS-0.2.4.dmg`.
2. Drag `AITS.app` into `Applications`.
3. Open AITS from the Applications folder.
4. If macOS blocks the app, open System Settings > Privacy & Security, find AITS, and click Open Anyway.
5. After launch, access AITS or its Settings from the macOS menu bar.

## First-Time Setup

AITS requires the following macOS permissions:

- Screen Recording: captures the current screen so the suggested reply feature can understand its context.
- Accessibility: detects selected text and pastes results back into the original app.

Enable these permissions in System Settings > Privacy & Security. If macOS asks you to restart the app, quit AITS completely and open it again.

Next, open Settings > AI to choose a provider and model, then enter your API key. API keys are stored in the macOS Keychain and are never written to this repository.

## Features and Hotkeys

| Feature | Default hotkey | Description |
| --- | --- | --- |
| Suggested replies and rewriting | `Control + T` | Generates suggested replies from the current screen when no text is selected, or rewriting suggestions when text is selected. |
| Translation | `Control + Y` | Translates selected text, then pastes the chosen result after you select it or press Return. |
| Proofreading | `Control + U` | Corrects grammar, spelling, punctuation, and clear typographical errors, then automatically pastes the result. |

Translation and proofreading send only the selected text. If no text is selected, AITS does not send a provider request.

## Menu Bar and Hotkey Controls

The menu bar provides:

- Manual suggestion generation
- Three independent hotkey toggle buttons for Suggestions, Translation, and Proofreading
- A global pause/resume hotkeys control
- Settings
- Quit AITS

The three hotkeys can be enabled or disabled independently, and their states persist across launches. The global Pause Hotkeys control acts as the master switch: pausing stops every hotkey without changing the three individual switches; resuming restores only the hotkeys that were individually enabled.

Manual suggestion generation remains available from the menu bar even while hotkeys are paused.

## Settings Pages

- General: language and the global Pause Hotkeys master switch.
- Suggestions: suggested reply/rewrite hotkey, suggestion count, System Prompt, and rewrite profiles.
- Translation: translation hotkey, target language, and System Prompt.
- Proofreading: proofreading hotkey and System Prompt.
- AI: provider, model, and API key.

## Basic Usage

### Generate Suggested Replies

1. Open a chat, email, support, or other app where you want to reply.
2. Make sure no text is selected, then press `Control + T`.
3. AITS captures the current screen and generates suggestions.
4. Select a suggestion to copy it to the clipboard and paste it back into the original app.

### Rewrite Selected Text

1. Select text in any app.
2. Press `Control + T`.
3. Choose a rewrite profile and result.
4. AITS attempts to replace the original selection with the result.

### Translate Selected Text

1. Select the text you want to translate.
2. Press `Control + Y`.
3. Select a translation in the result panel, or press Return to use the current result.
4. AITS pastes the translation back into the original app.

### Proofread Selected Text

1. Select the text you want to proofread.
2. Press `Control + U`.
3. When proofreading is complete, AITS automatically pastes the result into the original app.

## Troubleshooting

### macOS Says the Developer Cannot Be Verified

The current version has not been signed with a Developer ID or notarized. Open System Settings > Privacy & Security, find the blocked `AITS.app`, click Open Anyway, and confirm that you want to open it.

### Hotkeys Do Not Respond

Make sure AITS is running, the hotkey is not being used by another app, the corresponding individual hotkey switch is enabled, and hotkeys are not globally paused.

### Screen Capture or Automatic Paste Does Not Work

Make sure AITS has Screen Recording and Accessibility permissions. Some apps or specialized text fields may not accept automatic paste; the result remains on the clipboard, so you can paste it manually with `Command + V`.

## Privacy

- AITS processes the screen or selected text only when you trigger a feature.
- Screen content or text is sent to the AI provider you configure.
- API keys are stored in the macOS Keychain.
- This public download repository does not contain API keys, private settings, or source code.

## Known Limitations

- The current release is not notarized.
- Selected-text detection and automatic paste support may vary between apps.
- Local models require you to run a compatible local service separately.
