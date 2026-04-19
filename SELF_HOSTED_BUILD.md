# Remodex Self-Hosted iPhone Build

This fork is prepared for personal self-hosted use:

- Codex sessions stay on your Mac
- your relay stays separate
- the iPhone app runs as your own signed build
- the subscription gate is bypassed for this build

## What changed

- self-hosted build flag in `CodexMobile/BuildSupport/Base.xcconfig`
- custom bundle identifiers and callback scheme
- RevenueCat bootstrap skipped in self-hosted builds
- app access always enabled in self-hosted builds

## Before opening in Xcode

Create `CodexMobile/BuildSupport/PrivateOverrides.xcconfig` from the example and set:

```xcconfig
APPLE_DEVELOPMENT_TEAM = YOUR_TEAM_ID
REMODEX_APP_BUNDLE_IDENTIFIER = io.zbw0520.remodexselfhost
REMODEX_MENU_BAR_BUNDLE_IDENTIFIER = io.zbw0520.remodexselfhost.menubar
REMODEX_TEST_BUNDLE_IDENTIFIER = io.zbw0520.remodexselfhost.tests
REMODEX_UI_TEST_BUNDLE_IDENTIFIER = io.zbw0520.remodexselfhost.uitests
REMODEX_APP_DISPLAY_NAME = Remodex SH
REMODEX_CALLBACK_SCHEME = remodexselfhost
PHODEX_DEFAULT_RELAY_URL =
```

You can keep `PHODEX_DEFAULT_RELAY_URL` empty and continue pairing with a QR code from:

```sh
REMODEX_RELAY="wss://85.137.244.179/relay" remodex up
```

## Xcode install flow

1. Install the full Xcode app.
2. Open `CodexMobile/CodexMobile.xcodeproj`.
3. Set your Apple team in Signing for the app target.
4. Plug in the iPhone and trust the device.
5. Run the `CodexMobile` target on the phone.
6. Open the app and pair with the QR from your Mac bridge.

## Notes

- A free Apple ID works for personal installs and requires periodic re-signing.
- A paid Apple Developer account gives a longer-lived signing workflow.
- This fork is intended for personal self-hosted use.
