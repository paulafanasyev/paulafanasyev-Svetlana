# Светлана — архитектурный план

## Цель

Собрать работающего русскоязычного Android-агента из проверенных компонентов, а не продолжать бесконечную разработку собственного Hands.

## Кандидаты

### MobileAgent
Vision-driven Android agent: screenshot/UI detection → Manager → Executor → Reflector → Notetaker. Android-native, Kotlin/Compose, minSdk 26.

### Sanna
Voice-first Android assistant: wake/STT → LLM → TTS → agent loop, multi-step actions, Accessibility automation, local storage and scheduler.

### Aster
Android execution/tool layer: Accessibility UI tree and actions, system actions, notifications/SMS/calls/files and MCP transports. Local MCP and Binder IPC are especially relevant for an on-device architecture.

## Target composition

User → Svetlana UI/voice → agent core → MobileAgent planning/vision → Aster execution/tools.

Sanna capabilities are candidates for the voice/agent layer; duplicate automation/control code must not be blindly merged.

## Current rule

1. OX2/Hands is frozen for this project.
2. No Azure restoration.
3. No blind dependency transplantation.
4. First establish build/API/runtime compatibility, then integrate the smallest viable slice.
5. PASS requires actual APK/runtime evidence.
