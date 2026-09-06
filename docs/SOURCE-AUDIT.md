# Source audit — initial pass

## MobileAgent-Android

Upstream: `GiggleWang/MobileAgent-Android`

Observed architecture: Android-native Kotlin/Compose application. Core packages separate agent phases (`agent/`), LLM API (`api/`), device control (`controller/`), services, data and UI. The agent loop captures screenshots, uses Accessibility/UI detection, plans, executes atomic actions, reflects on the result and optionally records notes. minSdk 26; target SDK 34 in the upstream README.

Integration implication: MobileAgent is the strongest candidate for the initial Android shell/agent execution loop, but its existing Accessibility controller must be compared with Aster before merging.

## Sanna

Upstream: `sannabotdev/sannabotapp`

Observed architecture/features: React Native + native Kotlin; wake/STT/LLM/TTS voice loop; Accessibility automation; multi-step tool use; local storage; scheduler/notifications sub-agents. README states MIT license.

Integration implication: Sanna is a candidate source for voice UX and agent-loop concepts, not an additional independent Android-control stack. We should avoid importing its Accessibility layer if Aster becomes the execution backend.

## Aster

Upstream: `satyajiit/aster-mcp`

Observed architecture/features: Android companion app in Kotlin/Compose with AccessibilityService, MCP server, command handlers, local MCP mode and Binder IPC. README states minSdk 26, compileSdk 36, JDK 17, and MIT license. It exposes 49 tools and includes kill switch and PackagePolicyGuard safety controls.

Integration implication: Aster is the strongest candidate for the execution/tool boundary. Local MCP or Binder IPC is preferable to exposing the device-control channel unnecessarily.

## Current conclusion

Do not merge all three wholesale. The likely composition is:

`Svetlana UI/voice` + `Sanna voice concepts` + `MobileAgent vision/planning` + `Aster execution/tools`.

The next step is source-level overlap analysis and build-system compatibility, followed by a minimal vertical slice.
