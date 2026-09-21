# 安装指南

本 Skill 是纯 Markdown，没有任何依赖。按你用的平台选一种装法。

---

## ChatGPT / GPTs

### 方式 A：Custom GPT（推荐）

1. 打开 ChatGPT → 左侧 **Explore** → **Create a GPT**；
2. 切到 **Configure** 标签；
3. 在 **Instructions** 框里粘贴 [`skill/SKILL.md`](../skill/SKILL.md) 的**全部内容**；
4. 在 **Knowledge** 区域，把 `skill/references/` 下的 7 个 `.md` 文件全部上传；
5. 保存并发布。

之后在这个 GPT 里说"把这段小说改成分镜"即可。

### 方式 B：ChatGPT Projects

1. 新建一个 Project；
2. 在 Project 的 **Knowledge** 里上传整个 `skill/` 文件夹（或把 8 个 md 文件都拖进去）；
3. 在 Project 的 **Instructions** 里粘贴 `skill/SKILL.md` 的内容。

### 方式 C：API / Responses API

把 `skill/SKILL.md` 作为 system message 注入，把 `references/*.md` 作为检索文档按需喂给模型。OpenAI 官方 cookbook 里有 `skills_in_api.ipynb` 示例。

---

## Codex CLI

### 用户级（所有项目生效）

```powershell
# Windows
Copy-Item codex\AGENTS.md $env:USERPROFILE\.codex\AGENTS.md
```

```bash
# macOS / Linux
cp codex/AGENTS.md ~/.codex/AGENTS.md
```

### 项目级（只在这个项目生效）

把 `codex/AGENTS.md` 复制到项目根目录，重命名为 `AGENTS.md`。Codex 会按目录树自动合并。

> 想让 Codex 也能查到完整术语库？把整个 `skill/` 文件夹复制到项目根，Codex 会在需要时自动 Read。

---

## Claude Code / Claude Skills

把 `skill/` 整个文件夹复制到你的 skills 根目录：

```powershell
# Windows
Copy-Item -Recurse skill $env:USERPROFILE\.claude\skills\echi-storyboard-director
```

```bash
# macOS / Linux
cp -r skill ~/.claude/skills/echi-storyboard-director
```

Claude 的 Skill 规范与本仓库使用的开放标准兼容，`SKILL.md` 的 YAML frontmatter 会被自动识别。

---

## 其他 Agent（通用）

任何能读 markdown 系统提示词的 Agent 都能用：

1. 把 `skill/SKILL.md` 的内容粘贴到 Agent 的 system prompt / 自定义指令；
2. 把 `skill/references/*.md` 作为知识库文件上传，或在对话中按需引用。

---

## 验证安装成功

新会话里对 Agent 说：

> "帮我把这段改成 Seedance 分镜：'雨夜破庙，沈青衣一脚踢飞刺客的短刀。'"

如果它**没有直接开写**，而是反过来问你版本、风格、剪辑节奏——说明 Skill 已正确加载。
