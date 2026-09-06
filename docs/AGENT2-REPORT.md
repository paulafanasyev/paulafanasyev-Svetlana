# Agent 2 handoff — Svetlana migration

## Decision

A new clean repository `paulafanasyev/paulafanasyev-Svetlana` is now the experimental integration target. OX2/Hands is frozen and is not being modified by this migration.

## Evidence from upstream projects

- MobileAgent-Android: Android-native vision agent with Manager/Executor/Reflector/Notetaker, Accessibility-based UI detection/actions, minSdk 26, Kotlin 1.9, Compose, and no PC/ADB requirement.
- Sanna: Android voice-first assistant using React Native + native Kotlin, Accessibility automation, multi-step agent loop, local storage and scheduler; MIT license.
- Aster: Android Accessibility execution/tool layer with MCP, local on-device MCP mode and Binder IPC; MIT license; Android minSdk 26, JDK 17, compileSdk 36; 49 tools and explicit safety controls including kill switch and PackagePolicyGuard.

## Initial architecture

Svetlana UI/voice → agent core → MobileAgent planning/vision → Aster execution/tools. Sanna is treated as a candidate source for voice/agent-loop capabilities; duplicate automation layers must not be blindly merged.

## Changes made in this migration

1. Created the new clean repository target.
2. Added `README.md` defining the project direction.
3. Added `docs/ARCHITECTURE.md` with the initial integration boundary.
4. Added this handoff report.

## Not done / not claimed

- No source code from the three upstream repositories has been copied into the app yet.
- No APK build has been claimed.
- No runtime PASS has been claimed.
- No OX2/Hands code has been changed as part of this migration.
- Azure has not been restored.

## Next evidence gate

Perform source-level compatibility audit of the three repositories, identify overlapping Android control/agent/voice layers, choose exact revisions, then create the minimal buildable Android skeleton before any broad transplant.
