# Contributing / 参与贡献

## English

Issues and focused improvements are welcome.

### Reporting an Issue

Please include:

- The Clash Verge Rev and Mihomo core versions.
- Expected and actual behavior.
- The smallest configuration fragment that reproduces the issue.
- Relevant logs with subscription URLs, tokens, proxy servers, and other sensitive information removed.

### Submitting a Change

1. Create a branch from the latest version.
2. Keep the change focused on the reported problem.
3. Use two spaces for YAML indentation.
4. For a new rule, document its upstream source, target policy group, and ordering rationale.
5. Check whether any earlier broad rule can capture the intended traffic first.
6. Validate that the target client can load the profile.
7. Scan the full diff and Git history for sensitive information before publishing.

### Rule Ordering

- Specific rules precede broad rules.
- Custom rules precede third-party rule sets.
- Service rules precede `direct`, `proxy`, `cncidr`, and the final `MATCH`.
- Consider whether an IP CIDR rule should use `no-resolve`.

Do not submit subscriptions, proxy credentials, private domains, or identity-linked data.

---

## 简体中文

欢迎提交问题和范围明确的改进。

### 提交 Issue

请提供：

- Clash Verge Rev 与 Mihomo 内核版本。
- 预期行为和实际行为。
- 能够复现问题的最小配置片段。
- 相关日志，但必须先移除订阅地址、token、节点服务器和其他敏感信息。

### 提交更改

1. 基于最新版本创建分支。
2. 只修改与问题直接相关的内容。
3. YAML 使用两个空格缩进。
4. 新增规则时说明上游来源、目标策略组和排序依据。
5. 检查前面的通用规则是否会先匹配目标流量。
6. 验证目标客户端能够加载配置。
7. 发布前检查完整差异和 Git 历史中是否存在敏感信息。

### 规则排序

- 精确规则优先于通用规则。
- 自定义规则优先于第三方规则集。
- 服务专用规则优先于 `direct`、`proxy`、`cncidr` 和最终 `MATCH`。
- IP CIDR 规则应按用途考虑是否使用 `no-resolve`。

请勿提交机场订阅、节点认证信息、私人域名或能够关联身份的信息。
