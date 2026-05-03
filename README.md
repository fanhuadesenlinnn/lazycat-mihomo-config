# Mihomo / Clash Meta 懒猫微服优化配置

这个仓库保存一份适合中国大陆日常使用的 Mihomo 配置模板，重点做了：

- 懒猫微服兼容：`heiyu.space` / `lazycat.cloud` 真实 DNS，`6.6.6.6/32`、`2000::6666/128` TUN 旁路，`fc03:1136:3800::/40` 直连。
- 大陆网络体验：国内 DNS 优先、境外 DNS fallback、防污染、国内域名/IP 直连。
- 低维护：规则集自动更新，策略组会记住选择。
- 可扩展：新增服务只需要加一个策略组和一个 `RULE-SET`。

## 使用方式

1. 打开 `clash-myself.optimized.yml`。
2. 把 `proxy-providers.all-proxies.url` 替换为你的订阅链接。
3. 导入 Mihomo / Clash Meta 客户端。
4. 如需 TUN 透明代理，在客户端 UI 中开启，或把 `tun.enable` 改为 `true`。

## 懒猫微服检查

配置生效后可以检查：

```bash
dig AAAA 你的微服名.heiyu.space
dig A hello.lazycat.cloud
```

结果不应是 `198.18.x.x` 这类 fake-ip。启用 TUN 时，还需要确认 `6.6.6.6` 走正常局域网出口。

## 安全提醒

不要把真实订阅链接、节点密码、面板 `secret` 提交到公开仓库。建议仓库保持私有。
