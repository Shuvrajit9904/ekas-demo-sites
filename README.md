# ekas demo storefronts

Two fictional single-page customer sites used to exercise the **ekas** A2P 10DLC
compliance wizard demo. Hosted on GitHub Pages. Everything here is fake test data.

| Site | Folder | Notes |
|------|--------|-------|
| Lotus & Sage Spa | [`/spa`](./spa) | Day spa. Homepage has a compliant-looking SMS opt-in. `consent.png` shows a **pre-checked** box (a hard failure). **No `terms.html`** — the ToS URL deliberately 404s. `privacy.html` has no SMS clause (a warning). |
| Red Barn Market | [`/market`](./market) | Online farm store. Homepage opt-in is missing some disclosures (a warning). `consent.png` shows consent **required to check out** (a hard failure). The demo points the Privacy URL at `shop.html` (wrong page, a hard failure). `terms.html` has no SMS section (a warning). |

The `consent.png` in each folder is the opt-in screenshot referenced from the
demo's "Message flow / opt-in" field and analyzed by the vision scanner.

Regenerate screenshots:

```bash
CHROME="/Applications/Google Chrome.app/Contents/MacOS/Google Chrome"
"$CHROME" --headless=new --disable-gpu --hide-scrollbars --force-device-scale-factor=2 \
  --window-size=640,700 --screenshot=spa/consent.png "file://$PWD/spa/consent.html"
"$CHROME" --headless=new --disable-gpu --hide-scrollbars --force-device-scale-factor=2 \
  --window-size=640,760 --screenshot=market/consent.png "file://$PWD/market/consent.html"
```
