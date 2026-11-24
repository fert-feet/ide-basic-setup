# IDE Basic Setup

一套可复用的 IDE 通用配置，用于在新电脑上快速恢复熟悉的编辑体验。

仓库按 IDE 分目录保存配置。每个目录只保留跨电脑可复用的设置，并记录必要的外部依赖和恢复方式。

## 目录结构

```text
.
├── README.md
├── .gitignore
└── zed/
    ├── settings.json
    └── keymap.json
```

后续可以按相同方式增加其他 IDE：

```text
vscode/
cursor/
jetbrains/
neovim/
```

新增目录时沿用以下约定：

1. 一个 IDE 一个目录，目录名使用小写。
2. 优先保留工具原生文件名，方便直接复制或建立软链接。
3. 只提交通用配置，不提交账号凭证、本机绝对路径、缓存、日志、会话或历史数据。
4. 外部字体、扩展或插件依赖写入本 README。

## Zed

配置文件位于 [`zed/`](./zed)：

- `settings.json`：字体、保存、Vim、行号、Telemetry 和编辑器行为等通用设置。
- `keymap.json`：快捷键模板；当前没有启用自定义快捷键。

### 配置位置

| 平台 | Zed 配置目录 |
| --- | --- |
| macOS / Linux | `~/.config/zed` |
| Windows | `%APPDATA%\Zed` |

### 恢复配置

先备份新电脑上已有的 Zed 配置，再将对应文件复制到配置目录。例如在 macOS 或 Linux 上：

```bash
mkdir -p ~/.config/zed
cp zed/settings.json ~/.config/zed/settings.json
cp zed/keymap.json ~/.config/zed/keymap.json
```

### 字体依赖

`settings.json` 使用 `Maple Mono NF CN`。未安装该字体时 Zed 会回退到可用字体，配置仍可正常加载。安装字体后即可恢复预期显示效果。

### 有意未同步的配置

以下内容与当前电脑、账号或已安装扩展绑定，因此不放入通用配置：

- Agent 沙箱中与当前用户主目录绑定的绝对写入路径。
- Agent 网络白名单和终端自动放行策略。
- DeepSeek 等默认模型及账号认证。
- `session.trust_all_worktrees` 工作区信任策略。
- Catppuccin 主题、图标扩展及其他需要单独安装的扩展配置。
- Zed Prompt 数据库、历史记录、缓存和日志。
