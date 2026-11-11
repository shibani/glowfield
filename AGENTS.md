This is an Expo/React Native mobile application. Prioritize mobile-first patterns, performance, and cross-platform compatibility.

## Expo has changed — do not trust your training data

Expo ships breaking changes every SDK release. APIs you remember are likely renamed, moved, or removed. Before writing any code that touches an Expo, EAS, or React Native API:

1. Read the major version of the `expo` package in `package.json`.
2. Fetch the matching versioned docs: `https://docs.expo.dev/versions/v<major>.0.0/`
3. For anything else, fetch https://docs.expo.dev/llms.txt — an index of all Expo docs with corrections to common LLM misconceptions. Follow its links to the specific page you need; never answer from memory.

## Project: Glowfield

Building a new connective experience. Users appear as orbs in a shared field; online users glow. Tapping an orb sends a request for a 1:1 conversation. Public topic rooms support wellbeing conversations, with AI moderation keeping things civil.

## Stack

- Expo (React Native) + TypeScript, targeting iOS, Android and web
- Firebase JS SDK:
  - Realtime Database: presence only (who's online)
  - Firestore: users, rooms, messages, conversation requests
  - Authentication: the sign-up flow comes later; develop with test accounts
- Orb animation: TBD, options include React Native Skia

## Commands

```bash
npx expo install <package>  # ALWAYS use instead of npm add — resolves SDK-compatible versions
npx expo start              # start the dev server
npx expo lint               # lint
npx tsc --noEmit            # typecheck
npx expo-doctor             # diagnose dependency and config issues
npx expo install --fix      # fix incompatible package versions
firebase emulators:start    # local Auth, Firestore and Realtime Database
```

Run lint and typecheck before declaring any task done.

## Navigation & Routing

- Use **Expo Router** for all navigation. Routes live in `src/app/` — every file there is a screen, `_layout.tsx` files define navigators. Keep non-route code (components, hooks, utils) outside `src/app/`.
- Import `Link`, `router`, and `useLocalSearchParams` from `expo-router`.
- Docs: https://docs.expo.dev/router/introduction.md

## Conventions

- TypeScript strict; no `any`
- Functional components and hooks only
- Firebase access goes through `lib/`, not directly inside components
- Keep presence updates lightweight: heartbeat-based, near-real-time is fine

## Security

- Never read, print or modify `.env*` or `.secret*` files
- Never hardcode API keys or credentials. Real secrets live in Google Secret Manager and are used only from Cloud Functions
- Don't change `database.rules.json` or `firestore.rules` without asking first

## Building with EAS

Use EAS to build, sign, and submit the app in the cloud (`eas build`, `eas submit`) and to ship over-the-air updates (`eas update`) — no local Xcode or Android Studio required. Run EAS CLI as `npx eas-cli@latest <command>`; substitute that for bare `eas` in docs examples.
Docs: https://docs.expo.dev/eas/index.md

## Rules

- If `ios/` and `android/` directories do not exist, they are generated (Continuous Native Generation). Never create or edit them by hand — configure native behavior in `app.json` and config plugins.
- Expo Go only includes its bundled native modules. After adding a library with native code, the app needs a development build: `npx expo run:ios|android` locally, or `eas build --profile development`.
- Prefer recommended Expo modules over third-party libraries, and check your available skills before adding dependencies. Docs: https://docs.expo.dev/versions/latest/index.md

## Workflow

- One feature branch per roadmap item, merged via pull request
- Small, descriptive commits; never squash or rewrite history

## Roadmap

See README.md.