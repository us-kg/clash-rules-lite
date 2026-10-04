# us-kg/clash-rules-lite

Lightweight, hand-maintained Clash rule sets. No 100k-line dumps — every entry is here because someone actually visits it.

Inspired by [zhanyeye/clash-rules-lite](https://github.com/zhanyeye/clash-rules-lite); rewritten and extended for our own use.

## Files

| File | Purpose | Format |
|---|---|---|
| `proxy-rules.txt` | Domains that should go through the proxy | Clash classical |
| `direct-rules.txt` | Domains that go direct | Clash classical |
| `adslite-rules.txt` | Lightweight ad/tracker blocklist (hagezi PRO mini, ~60k) | Clash classical |
| `edu-rules.txt` | School & education domains (jjc.edu, lanecc.edu, Microsoft 365, Google Workspace…) | Clash classical |

## BackCN

| `backcn-rules.txt` | Mainland-locked services needing a China IP (currently 抖音) | Clash classical |

## Config template

`clash-lite.yaml` — a generic annotated Clash config that consumes the rule sets above via jsDelivr CDN. Fill in your subscription URL and import it.
`stash-lite.yaml` — Stash (iOS) variant: no TUN, iOS-specific notes, same rule sets.

## Usage

Reference the published files as `rule-provider` in your Clash config:

```yaml
rule-providers:
  proxy:
    type: http
    behavior: classical
    url: https://cdn.jsdelivr.net/gh/us-kg/clash-rules-lite@release/proxy-rules.txt
    path: ./ruleset/proxy.yaml
    interval: 86400
```

Replace `proxy-rules.txt` with any other filename for the rest. Files are published to the `release` branch and jsDelivr CDN on every push to `main`.

## Customizing

Edit the `.txt` / `.yaml` files directly and push — the `Generate Rules for Clash` workflow rebuilds the release automatically. Keep it lean: if you haven't visited a domain in months, it probably doesn't belong here.

## License

Rule data is factual domain lists. This repo's docs and workflow are MIT — see [LICENSE](LICENSE).
