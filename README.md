# Светлана

Clean fork of the working Aster Android agent, adapted for Russian users.

## Current strategy

Aster is the technical base. We preserve its working voice, Accessibility control, MCP/Binder execution, tools, and security model. We are **not** adding Sanna or MobileAgent to the runtime at this stage.

### First milestone

- Aster source copied into this repository
- Product name: **Светлана**
- Russian UI and user-facing strings
- Russian assistant persona/system instructions
- Existing Aster voice stack kept unchanged
- Existing Accessibility/execution stack kept unchanged
- Existing security controls kept unchanged
- OX2/Hands remains frozen and separate

## Evidence rule

A source change is not a build PASS. We only call the project working after an actual build and runtime verification produce evidence.

## Upstream

Aster: `satyajiit/aster-mcp`

Sanna and MobileAgent are deferred integration candidates, not dependencies of the first Svetlana build.
