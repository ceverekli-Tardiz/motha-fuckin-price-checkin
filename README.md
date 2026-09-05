# Motha Fuckin Price Checkin

A price-checking overlay for **Path of Exile** and **Path of Exile 2**. Press a hotkey on an item
in game and it tells you what the market is paying for it, with the filters that matter for that
kind of item already ticked.

**Windows only.** This repository carries the downloads and the changelog — the source lives
elsewhere and is currently private.

## Download

Grab the newest `PoE2PriceCheck-Setup-<version>.exe` from
**[Releases](../../releases/latest)** and run it.

- It installs for your user only — **no administrator prompt**.
- Once installed, the app keeps itself up to date. You only need this page once.

### Windows will warn you, and here is why

The installer is **not code-signed yet**, so Windows SmartScreen shows *"Windows protected your
PC"* with the continue button hidden behind **More info → Run anyway**.

That warning does not mean anything is wrong with the file — it means nobody has paid for a
certificate that vouches for the publisher. A certificate costs money every month, and spending it
before anyone has installed the thing is the wrong order. **The commitment: a signing certificate
gets bought at 100 downloads**, and this section gets rewritten the day it does.

In the meantime, every release lists the installer's **SHA-256** so you can check that the file you
downloaded is the file that was built.

## What it does with your account

To read the trade site it needs your Path of Exile session, the same one your browser holds. It is
stored **on your machine only**, in `%APPDATA%\poe2-price-check\config.json`, and it is sent to
`pathofexile.com` and nowhere else.

The update check is a plain request for a public file in this repository. It carries **no account,
no identifier, and nothing about your items**.

## Something is broken

Open an [issue](../../issues). Useful things to include: the version shown in the app's header, what
you did, and — if an item was involved — its Ctrl+C text.
