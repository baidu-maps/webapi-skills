# Baidu Map WebAPI Skills

[中文文档](README_zh.md)


This repository provides AI assistant **Skills** for [Baidu Map WebAPI](https://lbsyun.baidu.com/). Use them with [Claude](https://claude.ai), [Cursor](https://cursor.com), or other clients that support skills so the AI can reference accurate API docs and examples when you work with Baidu Map server-side APIs.

## Included Skills

| Skill | Description |
|-------|-------------|
| **bmap-webapi** | Baidu Map WebAPI: POI search (keyword / nearby / bounds / multi-dimensional), route planning (driving / walking / cycling / motorcycle / transit), geocoding & reverse geocoding, administrative division query, weather query, suggested departure time, route duration prediction, and more. For server-side or direct HTTP API integration. |

## How to Use

### 1. Clone the repo

```bash
git clone https://github.com/baidu-maps/webapi-skills.git
cd webapi-skills
```

### 1. Download from GitHub Releases (Optional)

Download the `webapi-skills.zip` asset from [Releases](https://github.com/baidu-maps/webapi-skills/releases), then unzip it:

```bash
unzip webapi-skills.zip
cd skills
```

### 2. Register the skill with your AI assistant

Link or copy the skill directories under `skills/` into your environment's skills folder so the AI can load its docs during conversations.

**Claude Desktop (local)**

- Skills directory is usually: `~/.claude/skills/`
- Register via symlink (recommended):
  ```bash
  ln -sfn "$(pwd)/skills/bmap-webapi" ~/.claude/skills/bmap-webapi
  ```
- Or copy the `skills/bmap-webapi` folder into `~/.claude/skills/`.

**Cursor**

- Skills directory is usually: `~/.cursor/skills/`
- Register via symlink (recommended):
  ```bash
  ln -sfn "$(pwd)/skills/bmap-webapi" ~/.cursor/skills/bmap-webapi
  ```
- Or copy the `skills/bmap-webapi` folder into `~/.cursor/skills/`.

### 3. Use it in chat

When your questions mention "Baidu Map", "WebAPI", "POI search", "route planning", "geocoding", "weather query", or similar, the assistant will use this skill's docs to give answers and code that match the Baidu Map WebAPI.

## Repo structure

```
.
├── skills/
│   └── bmap-webapi/               # Baidu Map WebAPI skill
│       ├── SKILL.md               # Skill entry and index
│       ├── references/            # API reference docs
│       │   ├── capabilities/      # Advanced capability docs (route duration, departure time, etc.)
│       └── recipes/               # usage scenarios
└── README.md
```

`SKILL.md` lists all reference and recipe files so the AI can load them as needed.

## License

If a skill declares a license (e.g. MIT), that applies to that skill; the repo may use the same license.
