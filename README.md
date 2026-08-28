<h1 align="center">Mihomo Profile</h1>

<p align="center">
  <em>A subscription-independent Merge profile for <strong>Clash Verge Rev</strong> and the <strong>Mihomo</strong> core<br/>with stable policy groups, region-based node selection, and service-specific routing.</em>
</p>

<p align="center">
  <a href="LICENSE"><img src="https://img.shields.io/badge/license-MIT-green?style=flat-square" alt="License: MIT"/></a>
  <img src="https://img.shields.io/badge/config-YAML-blue?style=flat-square" alt="Configuration: YAML"/>
  <img src="https://img.shields.io/badge/core-Mihomo-orange?style=flat-square" alt="Core: Mihomo"/>
</p>

<p align="center">
  <b>English</b> | <a href="README_zh.md">简体中文</a>
</p>

---

## Overview

This project keeps proxy nodes and routing logic separate: your subscription supplies the nodes, while [`merge.yaml`](./merge.yaml) supplies fixed policy groups, node classification, remote rule providers, and ordered routing rules. It does not contain subscriptions, proxy nodes, or credentials.

The profile currently targets the Merge configuration format used by [Clash Verge Rev](https://github.com/clash-verge-rev/clash-verge-rev) with the Mihomo core. Compatibility with other clients is not guaranteed.

---

## Features

- Collects actual subscription or provider nodes through `include-all`.
- Provides automatic, all-node, and region-based groups for Hong Kong, Taiwan, Japan, Singapore, the United States, and other regions.
- Provides dedicated policy groups for AI, social, streaming, gaming, and common internet services.
- Filters common traffic, quota, and expiry entries that some providers expose as nodes.
- Routes Steam China CDN, LAN traffic, and mainland China IP ranges directly.
- Keeps service-specific rules ahead of broad direct, proxy, and China IP rules.
- Uses remotely maintained domain, IP CIDR, and classical rule sets.

---

## Usage

1. Add your own subscription profile in [Clash Verge Rev](https://github.com/clash-verge-rev/clash-verge-rev).
2. Download [`merge.yaml`](./merge.yaml).
3. Attach it to the subscription as a Merge profile or Merge extension.
4. Update or reload the subscription profile.
5. Select the preferred default, service, and region policies in the client.

Client labels and menu locations may differ between releases. This repository does not provide nodes or subscription services.

---

## Routing Design

Mihomo evaluates rules from top to bottom and uses the first match. The profile therefore follows these ordering constraints:

- Custom domain rules precede third-party rule sets.
- `SteamCN` precedes `Steam` so mainland China download CDN traffic can remain direct.
- AI services precede broader Google and Microsoft rules.
- YouTube precedes the broader Google rule.
- Service-specific rules precede `direct`, `proxy`, `cncidr`, and the final `MATCH` rule.
- `tld-not-cn` is available but disabled by default because its broad scope can proxy more traffic than intended.

Region groups classify nodes by name. Providers with unusual naming conventions may require changes to the corresponding `filter` expressions. The `exclude-filter` patterns are best-effort and cannot cover every provider format.

---

## Rule Sources and Acknowledgments

| Repository | Usage |
| --- | --- |
| [Loyalsoldier/clash-rules](https://github.com/Loyalsoldier/clash-rules) | Foundational domain, IP CIDR, application, direct, proxy, and rejection rules |
| [blackmatrix7/ios_rule_script](https://github.com/blackmatrix7/ios_rule_script) | Service-specific classical rules for AI, internet, social, streaming, and gaming services |
| [MetaCubeX/mihomo](https://github.com/MetaCubeX/mihomo) | Proxy core and configuration format |
| [clash-verge-rev/clash-verge-rev](https://github.com/clash-verge-rev/clash-verge-rev) | Target desktop client and Merge workflow |

Upstream projects and their content remain subject to their own licenses and terms. This project is not affiliated with or endorsed by those projects.

---

## Privacy and Security

Before publishing a change, verify that it contains no subscription URL, token, UUID, password, private key, authenticated proxy entry, private domain, self-hosted service address, or local absolute path. Deleting a secret from the latest version does not remove it from Git history.

See [`SECURITY.md`](./SECURITY.md) for private reporting guidance.

---

## Contributing

Issues and focused improvements are welcome. Read [`CONTRIBUTING.md`](./CONTRIBUTING.md) before submitting a change.

---

## Disclaimer

Routing rules, service domains, CDN behavior, and client implementations can change without notice. Review the profile and upstream sources before use. You are responsible for complying with applicable laws, service terms, and network policies.

---

## License

This project is licensed under the [MIT License](./LICENSE). Referenced upstream rules are governed by their respective projects.
