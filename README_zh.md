# 百度地图 WebAPI Skills

[English Documentation](README.md)


本仓库专门存放**百度地图 WebAPI** 相关的 AI 助手 Skills，供 [Claude](https://claude.ai)、[Cursor](https://cursor.com) 等在使用百度地图服务端 API 时加载，以提供准确的 API 说明与示例。

## 包含的 Skill

| Skill | 说明 |
|-------|------|
| **bmap-webapi** | 百度地图 WebAPI：POI 检索（关键词/周边/区域/多维检索）、路线规划（驾车/步行/骑行/摩托车/公交）、地理编码与逆地理编码、行政区划查询、天气查询、建议出发时间、路线耗时预测等。适用于服务端或直接 HTTP API 调用集成。 |

## 如何使用

### 1. 克隆本仓库

```bash
git clone https://github.com/baidu-maps/webapi-skills.git
cd webapi-skills
```

### 1. 从 GitHub Release 下载（可选）

你也可以直接从 [Releases](https://github.com/baidu-maps/webapi-skills/releases) 下载附件 `webapi-skills.zip`，然后解压使用：

```bash
unzip webapi-skills.zip
cd skills
```

### 2. 将 Skill 注册到你的 AI 助手

把 `skills/` 目录下的 `bmap-webapi` 链接或复制到当前环境对应的 skills 目录，这样 AI 在对话时会自动读取这些文档。

**Claude Desktop（本地）**

- Skills 目录一般为：`~/.claude/skills/`
- 注册（软链，推荐）：
  ```bash
  ln -sfn "$(pwd)/skills/bmap-webapi" ~/.claude/skills/bmap-webapi
  ```
- 或直接把 `skills/bmap-webapi` 文件夹复制到 `~/.claude/skills/` 下。

**Cursor**

- Skills 目录一般为：`~/.cursor/skills/`
- 注册（软链，推荐）：
  ```bash
  ln -sfn "$(pwd)/skills/bmap-webapi" ~/.cursor/skills/bmap-webapi
  ```
- 或直接把 `skills/bmap-webapi` 文件夹复制到 `~/.cursor/skills/` 下。

### 3. 在对话中使用

在支持 Skills 的客户端里，当你的问题涉及「百度地图」「WebAPI」「POI 检索」「路线规划」「地理编码」「天气查询」等时，助手会优先参考本仓库中对应 skill 的文档来回答，从而给出更贴合百度地图 WebAPI 的代码与用法。

## 仓库结构

```
.
├── skills/
│   └── bmap-webapi/               # 百度地图 WebAPI Skill
│       ├── SKILL.md               # Skill 入口与索引
│       ├── references/            # API 参考文档
│       │   ├── capabilities/      # 高级能力文档（路线耗时、出发时间建议等）
│       └── recipes/               # 使用场景
└── README.md
```

`SKILL.md` 中会列出其下所有参考文档和场景食谱，便于 AI 按需读取。

## 许可

Skill 内若声明了 license（如 MIT），以该声明为准；仓库整体可沿用相同许可。
