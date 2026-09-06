# Agent 2 handoff — Svetlana migration

## Decision

The project direction has been simplified: **Aster-first**. The working Aster Android agent is the technical base for Svetlana. MobileAgent and Sanna are deferred and are NOT runtime dependencies of the first Svetlana build. OX2/Hands remains frozen and separate.

## Upstream evidence

- Aster: Android Accessibility execution/tool layer with MCP, local on-device MCP mode and Binder IPC; MIT license; minSdk 26, JDK 17, compileSdk 36; 49 tools; kill switch and PackagePolicyGuard.
- MobileAgent-Android: vision/planning candidate only for a later phase.
- Sanna: voice/agent-loop candidate only for a later phase.

## Product rule

We are not replacing Aster's working voice stack. **Existing Aster voice is frozen and preserved unchanged.** We also preserve Accessibility, execution, MCP/Binder, tools and security until runtime evidence proves a reason to change them.

## Changes made

1. `README.md` changed to the Aster-first strategy.
2. Added `.github/workflows/import-aster.yml`.
3. The workflow automatically clones the upstream Aster repository into `paulafanasyev-Svetlana`, preserving the Svetlana docs, and sets the Android application label to `Светлана` without rewriting internal Aster identifiers during the first import.
4. Added the migration contract in `docs/ASTER-IMPORT.md` during the import job.

## Current execution state

The import workflow was committed at:

`66079872755a965fcb45f92a6572cd1cc291450c`

The workflow is designed to create the actual Aster source import commit on `main`. At the moment of this report, the GitHub workflow-run query has not yet returned a run for that commit, so the import itself is **NOT YET CLAIMED COMPLETE**.

## Not claimed

- No APK build PASS.
- No runtime PASS.
- No claim that Russian localization is complete yet.
- No package-identifier rename yet; internal Aster identifiers are intentionally preserved for the first stable import.
- No OX2/Hands changes.
- Azure has not been restored.

## Next evidence gate

1. Confirm the import workflow completed and inspect the resulting tree.
2. Build the imported Aster app.
3. Verify the existing voice stack and Accessibility control before changing internals.
4. Then perform Russian user-facing localization without destabilizing the working execution/voice stack.
