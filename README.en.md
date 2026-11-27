# DokoDesk

[日本語](README.md) | **English**

DokoDesk is a remote desktop for your own Mac. Control your Mac from your iPhone, iPad, or another Mac.
Your devices connect directly over [Tailscale](https://tailscale.com) (a separate free app). Your screen and input never go through anyone else's servers.

> **Mac only.** DokoDesk controls Macs. Windows and Linux PCs are not supported.

## Requirements

- A Mac to control (Apple silicon or Intel, macOS 13 or later) with **DokoDesk for Mac** (free, download below)
- An iPhone or iPad (iOS 16 or later) with **DokoDesk** from the App Store
- A Tailscale account (free; sign in with Google, Apple, or Microsoft)

## Setup (about 10 minutes)

The easiest way: **install DokoDesk on your iPhone / iPad first and follow "Getting started"** in the app. You can send the Mac download link to yourself from there.

### 1. iPhone / iPad

1. Install **DokoDesk** from the App Store.
2. Open it. "Getting started" walks you through: install Tailscale → send the link to your Mac → scan the QR code.

### 2. Mac

1. Open the link you sent from your iPhone, or download **[DokoDesk for Mac](https://github.com/ken-kurosu/taildesk-releases/releases/latest/download/TailDeskHost.zip)**.
2. Open the downloaded app ("TailDeskHost"). If macOS asks whether to open it, choose **Open**. When asked to move it to the Applications folder, choose **Move**.
3. The "DokoDesk setup" window appears. Press the buttons from top to bottom:
   - Install Tailscale and **sign in with the same account** as your iPhone / iPad
   - Allow **Screen Recording** and **Accessibility** (System Settings opens — turn on the switch for DokoDesk; it may be listed as "TailDeskHost")
4. A QR code appears. Scan it with DokoDesk on your iPhone / iPad. Done.

DokoDesk for Mac starts automatically at login and keeps the Mac awake while it's on power.

## Controlling one Mac from another Mac

You can also control, for example, your office Mac from your home Mac. The controlling Mac must have Apple silicon (M1 or later) — it runs the iPad version of DokoDesk.

1. On the **Mac to be controlled**, install DokoDesk for Mac (section 2 above).
2. On the **controlling Mac**, install **DokoDesk** from the App Store, then install Tailscale and sign in with the same account.
3. On the Mac to be controlled, choose DokoDesk in the menu bar → **Start Pairing…**.
4. On the controlling Mac, open **DokoDesk** (from Launchpad or Applications — not the menu-bar icon), press **Add a Mac**, enter the "Mac's address" (100.x.x.x) shown in the pairing window, then the 12-digit fingerprint and the 6-digit code, and press **Pair**. (Macs don't scan the QR code, so you enter the numbers instead.)

Your mouse and keyboard go straight to the controlled Mac.

## Pricing

The first month is free. After that, a monthly or yearly subscription (prices are shown in the App Store in your currency). You can manage or cancel it in Settings → your name → Subscriptions. DokoDesk for Mac is free.

## Troubleshooting

- **Tailscale says "needs approval"**: approve the device in the Tailscale admin console (https://login.tailscale.com/admin/machines).
- **Can't connect**: make sure DokoDesk for Mac is running (menu-bar icon), both devices show "Connected" in Tailscale with the same account, and the Mac isn't asleep. While on power, DokoDesk keeps the Mac awake (not on battery).
- **The screen is black or input doesn't work**: on the Mac, check System Settings → Privacy & Security → Screen Recording and Accessibility, and turn DokoDesk (TailDeskHost) on.

## If you lose a device

On the Mac, choose DokoDesk in the menu bar → **Paired Devices** and unregister that device. It can no longer connect. Turning on the Face ID lock in DokoDesk on your iPhone / iPad is recommended.

## Security design

- The Mac accepts connections only from your Tailscale network (100.x.x.x).
- Only paired devices can control it (devices verify each other with per-device certificates).
- All traffic is encrypted with TLS 1.3 and never goes through the developer's servers.
- Content copied from password managers is never sent to your iPhone / iPad.

## Contact

- Bugs and requests: [Issues](https://github.com/ken-kurosu/taildesk-releases/issues)
- Email: kurosu@i-kasa.com

## Privacy

[Privacy Policy](PRIVACY.md)
