# Birch Screenshots

Simulator screenshots of [Birch](https://github.com/Birch-Wallet/birch-wallet), captured by the fastlane `screenshots` lane. This repo is a submodule of birch-wallet at `fastlane/screenshots/`, so the lane writes straight into it.

The wallet shown is the test fixture from `birchUITests/ScreenshotTests.swift`. No real keys or addresses appear.

## Layout

| Path | What it is |
|---|---|
| `dark/en-US/`, `light/en-US/` | Bare captures, one per device and screen, named `<Device>-NN-Name.png`. Devices: iPhone 17 Pro, iPhone 17 Pro Max, iPhone 11 Pro Max, iPhone 13 mini, iPad Pro 13-inch (M5), and iPhone Duo closed and open. |
| `dark/framed/`, `light/framed/` | The iPhone captures in device frames, named `<Device>-NN-Name_framed.png`. |

The `appstore/` and `appstore-duo/` upload sets stay on your machine and aren't committed.

## Updating

From birch-wallet:

```sh
fastlane screenshots                          # every device
fastlane screenshots only:"iPhone 17 Pro"     # one device, keep the rest

git -C fastlane/screenshots add -A
git -C fastlane/screenshots commit -m "Update screenshots"
git -C fastlane/screenshots push
git add fastlane/screenshots
git commit -m "Update screenshots submodule"
```

A full run replaces `dark/` and `light/`. Commit after the whole run finishes, so the repo never holds a half-regenerated set.

## Who uses them

- The App Store listing.
- [birch-design](https://github.com/Birch-Wallet/birch-design): **Overlay app** lays the iPhone 17 Pro captures over the rebuilt screens, and `tools/build-assets.py` cuts QR codes and the status bar from them. The design site on GitHub Pages copies the iPhone 17 Pro captures when it deploys.
