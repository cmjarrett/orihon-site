# orihon-site

The public website for **Orihon** 折本, a private journal for iPhone Duo and iPhone. Served by GitHub Pages at <https://orihon.app>, with <https://orihon.day> forwarding to it.

The app itself lives in a separate private repository. This one holds only what is published.

## Pages

- `index.html`: the front page.
- `privacy/index.html`: the privacy policy, at `https://orihon.app/privacy`. App Store Connect and TestFlight point at this address.
- `support/index.html`: support, at `https://orihon.app/support`.
- `404.html`: shown for any address that does not exist.
- `style.css`: the one stylesheet. Icons are web-sized copies of the app icon.

## Rules

1. **Plain pages only.** No scripts, no cookies, no analytics, no fonts or files loaded from anywhere else. The site keeps the same promise the app does.
2. **The privacy policy must match the app as it is.** When an app change alters what leaves the phone (the weather stamp, for example, would send a coarse location to Apple), change `privacy/index.html` and its effective date here before that build goes to testers.
3. **Changes go through a pull request** that CJ merges. Merging to `main` publishes within a minute or two.

## Preview

```
python -m http.server 8765
```

Then open <http://localhost:8765>.

## Hosting

GitHub Pages, deployed from the `main` branch root. `CNAME` sets the custom domain; `.nojekyll` serves the files as they are. DNS is at Porkbun:

| Host | Type | Answer |
| --- | --- | --- |
| `orihon.app` | A | `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153` |
| `orihon.app` | AAAA | `2606:50c0:8000::153`, `2606:50c0:8001::153`, `2606:50c0:8002::153`, `2606:50c0:8003::153` |
| `www.orihon.app` | CNAME | `cmjarrett.github.io` |

`orihon.day` uses Porkbun URL forwarding to `https://orihon.app`. `support@orihon.app` is Porkbun email forwarding.

Worth doing once: verify `orihon.app` under GitHub Settings, Pages, Verified domains, so no other GitHub account can ever claim the domain.

Later, Universal Links need an `apple-app-site-association` file at `.well-known/` in this repo.
