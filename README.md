# us-kg/clash-rules-lite

Lightweight, hand-maintained Clash rule sets. No 100k-line dumps — every entry is here because someone actually visits it.

Inspired by [zhanyeye/clash-rules-lite](https://github.com/zhanyeye/clash-rules-lite); rewritten and extended for our own use.

## Files

| File | Purpose | Format |
|---|---|---|
| `proxy-rules.txt` | Domains that should go through the proxy | Clash classical |
| `direct-rules.txt` | Domains that go direct | Clash classical |
| `microsoft-rules.txt` | Microsoft services | Clash classical |
| `blacklist-rules.txt` | Blocked categories | Clash classical |
| `edu.yaml` | School & education domains (jjc.edu, lanecc.edu, Microsoft 365, Google Workspace…) | Clash classical |

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
