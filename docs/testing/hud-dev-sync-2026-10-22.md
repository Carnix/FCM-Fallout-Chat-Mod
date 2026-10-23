# Dev synchronization and HUD 2.10.151 — 2026-10-22

The user requested current Dev and the local HUD work synchronized, followed by
installation of the newest DEV HUD on the desktop and MSI laptop. The original
45-file working tree, binary diff and generated artifacts were retained in
conversation evidence, and Git stash `42851162c37b55a5b88f2ac2fbff44437f4f33d8`
was kept as an additional recovery point.

## Integrated source

Local Dev was fast-forwarded from `d7a38af1` to `957e8a02` before restoring the
HUD changes. The combined source retains current Dev's adaptive cooldown/retry
handling and the 2.10.150 stationary-name continuation policy. The new widget
version is **2.10.151**; shared bridge regression source remains **0.2.18**.
The visible archive and source manifest are rebuilt from the combined source.
No production promotion or public release is part of this request.

## Verification

The 31 pure Haxe suites, nine source/package checks and empty widget/scenario
compiler diagnostics pass. The source-anchor check initially rejected a missing
2.10.151 metadata line in `BUILD.md`; after correcting the documentation, that
check passed. The complete Ruffle suite passes **93/93** in 504.7 seconds, with
the tested artifact manifest unchanged and the owned harness listener closed.

Backend validation uses an owned disposable Redis and a clean working directory
without local/prod dotenv files. Focused relay/presence tests pass 170 cases;
the full Jest run passes 1,697 tests with nine existing skips. TypeScript unit
tests pass all 445 cases, and the Redis container is removed afterward. Overlay
and dashboard Vitest suites pass 1,307 and 490 cases respectively, as do
typechecks for all three applications.

The DEV package is
`game-mods/FCMBridge/hudmodloader-chat/.build/FCMChatWidget-2.10.151-DEV-test.zip`
(12,023,616 bytes; 16 CRC-verified entries). Both provider folders contain the
same tested archive. Package SHA-256:
`6c16511650f8ba7f6421fe1c25b8eef70b75941d49cea48b344bc07eaddde673`.
Installed BA2 SHA-256:
`3d79f5e6be6db00f34da06e88d605e94fd16c0fbf3b460c9471f49fc4c602e7a`.
Evidence is under `dev-sync-hud151-20261022/` in the conversation evidence directory.
Hosted CI remains pending publication of the local Dev commit.

## Installation contract

Both machines use xScal 0.4.27 and Steam game 1.7.27.11. The verified DEV archive
is installed on both, with the native relay set to
`wss://dev.falloutchatmod.com/relay` and HUD link host to
`dev.falloutchatmod.com/link`. Existing HUD keybinds, appearance settings,
authentication caches and providers were retained. The MSI also received the
verified Steam Address Library v3 for 1.7.27.11. Both games were independently
confirmed closed before replacement. Independent verification confirms all
three desktop/four MSI installation targets and six desktop/seven MSI protected
files. The MSI restore script parses successfully.

- Desktop backup: `Fallout76/.extender-backups/before-hud151-DEV-integration-20261022T053746Z/`.
- MSI backup: `C:\Users\White\Documents\FCM-Repro-Backups\before-hud151-DEV-integration-20261022T053823Z\`.

`DESKTOP-INSTALL.json` and `MSI-INSTALL.json` in conversation evidence retain exact
hashes and restore paths. Insert opens chat; Delete hides the idle HUD; native
input remains selected on both devices.

Authentication caches are preserved as files; a production login is not proof of
Dev authentication. Complete Dev account linking if the new environment prompts.
Native acceptance of 2.10.151 remains pending: check input/send/cancel/map recovery,
channel selection and directed sends, then test two nearby clients' overhead names
while stationary. Earlier 2.10.134 input acceptance does not accept this build's
nameplate behavior or the broader shared Server/provider matrix.
