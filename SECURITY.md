# Security Policy / 安全策略

## English

### Reporting a Security Issue

If you find an exposed subscription credential, token, password, private address, or other sensitive information, do not paste the complete value into a public Issue.

Prefer GitHub private vulnerability reporting from the repository's **Security** page. If private reporting is not enabled, open an Issue without the sensitive value, identify only the issue type and affected file, and wait for the maintainer to provide a private communication method.

Include:

- The affected file and approximate location.
- The type of exposure, without the complete credential.
- Suggested revocation, rotation, or history-cleaning steps.

Any published credential should be revoked or rotated immediately. Removing it from the current file is not enough to remove it from Git history.

### Supported Versions

Only the latest version on the default branch is maintained. Problems in third-party rule content or upstream services should be reported to the corresponding upstream project.

---

## 简体中文

### 报告安全问题

如果发现订阅凭据、token、密码、私人地址或其他敏感信息，请不要将完整敏感值粘贴到公开 Issue。

优先通过 GitHub 仓库 **Security** 页面提交私密漏洞报告。如果尚未启用私密报告，请创建不含敏感值的 Issue，只说明问题类型和受影响文件，并等待维护者提供私密沟通方式。

报告时请提供：

- 受影响的文件和大致位置。
- 泄露类型，不包含完整凭据。
- 建议的撤销、轮换或历史清理措施。

任何已经公开的凭据都应立即在对应服务中撤销或轮换。仅从当前文件删除不足以清除 Git 历史中的敏感信息。

### 支持版本

本项目只维护默认分支中的最新版本。第三方规则内容和上游服务问题应提交到相应上游项目。
