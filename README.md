# Glowfield

Building a new connective experience.

## Current concept

The landing page experience has every user appearing as an orb in a shared field/view. Orbs glow while their person is online, and tapping one sends a request to start a 1:1 conversation. Public rooms organized by topic bring people together around shared interests and wellbeing, AI moderation keeping converations civil. The concept will evolve as the product takes shape. 

## Stack

- React Native with Expo (iOS, Android, web)
- TypeScript
- Firebase: Authentication, Realtime Database (presence), Firestore (messages, users, rooms)

## Getting started

```bash
npm install
npx expo start
```

Copy your Firebase web config into `.env.local` using the `EXPO_PUBLIC_FIREBASE_*` variables.

## Roadmap

- [ ] Orb field: animated, glowing orbs
- [ ] Live presence driving the glow
- [ ] Topic rooms
- [ ] Auth flow: sign-up, login and usernames
- [ ] Conversation requests and 1:1 chat
- [ ] AI moderation for rooms and conversations
- [ ] App Store and Play Store release