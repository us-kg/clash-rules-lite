# us-kg/clash-rules-lite

轻量、手维护的 Clash 规则集。没有十几万行的全量表 —— 留下的每一条都是真有人访问的。

灵感来自 [zhanyeye/clash-rules-lite](https://github.com/zhanyeye/clash-rules-lite)，按我们自己的需求重写和扩展。

## 文件

| 文件 | 用途 | 格式 |
|---|---|---|
| `proxy-rules.txt` | 走代理的域名 | Clash classical |
| `direct-rules.txt` | 直连域名 | Clash classical |
| `adslite-rules.txt` | 轻量广告/追踪拦截（hagezi PRO mini，约 6 万条） | Clash classical |
| `edu-rules.txt` | 学校/教育域名（jjc.edu、lanecc.edu、Microsoft 365、Google Workspace…） | Clash classical |
| `loc-cn`（via [dmulle12/rules](https://github.com/dmulle12/rules/raw/rel/loc-cn.yaml)） | 直连的中国大陆服务域名，每日自动更新 | Clash domain |

## 配置模板

`clash-lite.yaml` —— 通用注释版 Clash 配置，通过 jsDelivr CDN 引用上面的规则集。填入订阅链接即可导入使用。
`stash-lite.yaml` —— Stash（iOS）专用版：去掉 TUN，iOS 适用注释，规则集相同。

## 使用

在 Clash 配置里用 `rule-provider` 引用发布后的文件：

```yaml
rule-providers:
  proxy:
    type: http
    behavior: classical
    url: https://cdn.jsdelivr.net/gh/us-kg/clash-rules-lite@release/proxy-rules.txt
    path: ./ruleset/proxy.yaml
    interval: 86400
```

其他文件把文件名换掉即可。每次 push 到 `main` 会自动发布到 `release` 分支和 jsDelivr CDN。

## 自定义

直接改 `.txt` / `.yaml` 文件然后 push —— `Generate Rules for Clash` 工作流会自动重新发布。保持精简：几个月没访问过的域名，大概率不该留在这里。

## 许可证

规则数据是事实性的域名列表。本仓库的文档和工作流为 MIT —— 见 [LICENSE](LICENSE)。
