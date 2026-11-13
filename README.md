# CF Server Monitor Emerald 主题（实时速率补丁构建）

This repository hosts a patched production build of the official [Tokinx/cf-server-monitor-theme-emerald](https://github.com/Tokinx/cf-server-monitor-theme-emerald) theme, based on **v1.2.10** (source commit `c80591198df4d2a0332b86b41e53e42fd341ed99`). It is published for the 橙星云监控面板 live-rate fix.

本仓库托管基于官方主题 **v1.2.10** 的补丁构建，用于橙星云监控面板的实时速率修复。

- 源码基线 / Source baseline：官方仓库 `main`，标签 `v1.2.10`，提交 `c80591198df4d2a0332b86b41e53e42fd341ed99`
- 发布分支 / Publish branch：`build`（与官方主题相同的目录布局：仓库根目录含 `index.html` 与 `assets/`）
- 补丁说明 / Patch：在 `/api/ws` 未连接时以 3 秒间隔做 HTTP 轻轮询刷新实时速率；首屏已展示最后一条样本后，不再把回放时钟拨回更早样本
- 构建说明 / Build note：为通过官方 `bun run build` 的类型检查，给 `LatestReportSample` 补了 WebSocket 路径里已在使用的可选字段 `timestamp`、`metrics`（仅类型定义，无运行时逻辑变更）

面板请把主题地址指向本仓库 `build` 分支某一提交的 tree URL，例如：

```text
https://github.com/cj409347747-art/cf-server-monitor-theme-emerald/tree/<40-char-SHA>
```

本仓库只托管打过补丁的构建产物，不是上游官方仓库，请不要向 `Tokinx/cf-server-monitor-theme-emerald` 提交本构建。

许可与上游相同，采用 MIT License。版权归原作者 Tokinx 所有。完整条款见 [LICENSE](./LICENSE)。
