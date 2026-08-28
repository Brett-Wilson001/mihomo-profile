<h1 align="center">Mihomo Profile</h1>

<p align="center">
  <em>面向 <strong>Clash Verge Rev</strong> 与 <strong>Mihomo</strong> 内核的订阅无关 Merge 配置<br/>提供固定策略组、地区节点分类和服务级分流。</em>
</p>

<p align="center">
  <a href="LICENSE"><img src="https://img.shields.io/badge/license-MIT-green?style=flat-square" alt="License: MIT"/></a>
  <img src="https://img.shields.io/badge/配置-YAML-blue?style=flat-square" alt="配置：YAML"/>
  <img src="https://img.shields.io/badge/内核-Mihomo-orange?style=flat-square" alt="内核：Mihomo"/>
</p>

<p align="center">
  <a href="README.md">English</a> | <b>简体中文</b>
</p>

---

## 项目简介

本项目将代理节点与分流逻辑分离：你的订阅负责提供节点，[`merge.yaml`](./merge.yaml) 负责建立固定策略组、节点分类、远程规则提供器和有序分流规则。仓库不包含订阅、代理节点或认证信息。

当前配置以 [Clash Verge Rev](https://github.com/clash-verge-rev/clash-verge-rev) 配合 Mihomo 内核使用的 Merge 配置格式为目标，不保证兼容其他客户端。

---

## 功能特性

- 通过 `include-all` 收集订阅或 provider 中的实际节点。
- 提供自动选择、全部节点以及香港、台湾、日本、新加坡、美国和其他地区策略组。
- 为 AI、社交、流媒体、游戏平台和常用互联网服务提供独立策略组。
- 过滤部分机场伪装成节点的流量、套餐和到期信息。
- 将 Steam 中国大陆 CDN、局域网和中国大陆 IP 段优先直连。
- 将服务专用规则放在通用直连、代理和中国大陆 IP 规则之前。
- 使用远程维护的域名、IP CIDR 和 classical 规则集。

---

## 使用方法

1. 在 [Clash Verge Rev](https://github.com/clash-verge-rev/clash-verge-rev) 中添加自己的订阅配置。
2. 下载 [`merge.yaml`](./merge.yaml)。
3. 将其作为订阅配置的 Merge 配置或扩展配置使用。
4. 更新或重新加载订阅配置。
5. 在客户端中选择所需的默认、服务和地区策略。

不同版本的菜单名称和位置可能有所差异。本仓库不提供节点或订阅服务。

---

## 分流设计

Mihomo 从上到下检查规则，并使用第一个匹配结果。因此，本配置遵循以下顺序约束：

- 自定义域名规则位于第三方规则集之前。
- `SteamCN` 位于 `Steam` 之前，使中国大陆下载 CDN 可以保持直连。
- AI 服务位于范围更广的 Google 和 Microsoft 规则之前。
- YouTube 位于范围更广的 Google 规则之前。
- 服务专用规则位于 `direct`、`proxy`、`cncidr` 和最终 `MATCH` 之前。
- `tld-not-cn` 已提供但默认不启用，避免其过宽范围代理超出预期的流量。

地区策略组依赖节点名称进行分类。机场命名方式特殊时，需要调整对应的 `filter` 表达式。`exclude-filter` 只能尽量排除伪装节点，无法覆盖所有机场格式。

---

## 规则来源与致谢

| 来源仓库 | 用途 |
| --- | --- |
| [Loyalsoldier/clash-rules](https://github.com/Loyalsoldier/clash-rules) | 基础域名、IP CIDR、应用、直连、代理和拦截规则 |
| [blackmatrix7/ios_rule_script](https://github.com/blackmatrix7/ios_rule_script) | AI、互联网、社交、流媒体和游戏服务的细分 classical 规则 |
| [MetaCubeX/mihomo](https://github.com/MetaCubeX/mihomo) | 代理内核和配置格式 |
| [clash-verge-rev/clash-verge-rev](https://github.com/clash-verge-rev/clash-verge-rev) | 目标桌面客户端及 Merge 工作流 |

各上游项目及其内容分别受自身许可证和条款约束。本项目与这些项目不存在隶属关系，也不代表其官方认可。

---

## 隐私与安全

公开修改前，请确认其中不含订阅 URL、token、UUID、密码、私钥、带认证信息的代理节点、私人域名、自建服务地址或本地绝对路径。从最新版本删除敏感信息并不能将其从 Git 历史中移除。

私密报告方式参见 [`SECURITY.md`](./SECURITY.md)。

---

## 参与贡献

欢迎提交 Issue 和范围明确的改进。提交修改前请阅读 [`CONTRIBUTING.md`](./CONTRIBUTING.md)。

---

## 免责声明

分流规则、服务域名、CDN 行为和客户端实现都可能随时变化。使用前请自行检查本配置和上游来源，并自行确保遵守所在地法律、服务条款及网络管理规定。

---

## 开源协议

本项目采用 [MIT License](./LICENSE)。引用的上游规则分别受对应项目的许可证约束。
