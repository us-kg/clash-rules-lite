# us-kg/clash-rules-lite

轻量、手维护的 Clash 规则集。没有十几万行的全量表 —— 留下的每一条都是真有人访问的。

灵感来自 [zhanyeye/clash-rules-lite](https://github.com/zhanyeye/clash-rules-lite)，按我们自己的需求重写和扩展。

## 文件

| 文件 | 用途 | 格式 |
|---|---|---|
| `proxy-rules.txt` | 走代理的域名 | Clash classical |
| `direct-rules.txt` | 直连域名 | Clash classical |
| `microsoft-rules.txt` | 微软服务 | Clash classical |
| `blacklist-rules.txt` | 屏蔽类别 | Clash classical |
| `edu.yaml` | 学校/教育域名（jjc.edu、lanecc.edu、Microsoft 365、Google Workspace…） | Clash classical |

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
