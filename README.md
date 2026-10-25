# fox-widget-marketplace

[WorkBuddy狐娘小挂件（fox-widget）](https://github.com/pigeon189/zcode-fox-widget/tree/workbuddy) 的自建套件市场。
本仓库只有市场清单和插件副本，源码、问题与讨论都在源码仓库。

- 当前版本：**v1.3.4**
- 同步自：`pigeon189/zcode-fox-widget@workbuddy`（19035ba）
- 平台：Windows（桌面浮层依赖 Win32；其余功能在 macOS / Linux 上只能用本地页面）

## 安装

1. WorkBuddy 左栏「专家 · 技能 · 连接器」→「技能」→「套件」
2. 右上角「添加」→「新增市场」
3. 市场源填：

   ```text
   pigeon189/fox-widget-marketplace
   ```

4. 市场里出现 `fox-widget`，点 + 安装，作用域选 **user**
5. 重启会话（或重开客户端），让 hooks 与 MCP 生效
6. 需要桌面浮层时再装运行时（约 150MB 下载，一次性）：

   ```bash
   node lib/cli.mjs desktop install
   ```

> 宿主不认 `owner/repo#分支`。本仓库默认分支就是市场内容，所以直接填 `pigeon189/fox-widget-marketplace` 即可；
> 若所在环境禁用「新增市场」，可改用分支 ZIP：
> `https://github.com/pigeon189/zcode-fox-widget/archive/refs/heads/workbuddy.zip`

## 升级

市场页「刷新」→ 重装 → 重启客户端。数据在插件数据目录，配置、账本、导入的角色都不丢。
本市场**不启用**挂件内自更新（原地覆盖会和宿主插件管理打架）。

## 它会做什么

- 读宿主的用量数据（`workbuddy.db` 与会话 transcript）汇总今日积分、本轮消耗、上下文余量
- `SessionStart` 钩子幂等拉起本地挂件服务；`UserPromptSubmit` / `Notification` 写低频事件
- 提供 MCP 工具 `whale_balance` / `whale_last_turn` / `whale_widget` / `whale_config`
- 可选：读 `DEEPSEEK_API_KEY` 或插件数据目录 `config.json` 里的 key，显示厂商余额（不配也能用）
- 桌面浮层是一个独立的透明置顶窗口，指针不在角色上时点击穿透

## 许可

MIT。素材与沿革见插件目录内的 `NOTICE` 与 `LICENSE`。
