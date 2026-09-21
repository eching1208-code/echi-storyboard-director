# Echi Storyboard Director

> **AI 影视分镜导演 Skill** —— 把小说、剧本、故事梗概，一键变成可直接粘贴进 Seedance / Sora / Runway / Pika 的标准化分镜脚本。
>
> *Professional AI film storyboard director for text-to-video generators.*

[![License: AGPL-3.0](https://img.shields.io/badge/License-AGPL--3.0-blue.svg)](LICENSE)
[![Platform: ChatGPT](https://img.shields.io/badge/Platform-ChatGPT%20%2F%20GPTs-black.svg)](#install-on-chatgpt)
[![Platform: Codex CLI](https://img.shields.io/badge/Platform-OpenAI%20Codex-green.svg)](#install-on-codex-cli)
[![Platform: Claude](https://img.shields.io/badge/Platform-Claude%20Code-orange.svg)](#install-on-claude)
[![Style: cinematic](https://img.shields.io/badge/Style-Cinematic%202.35%3A1-red.svg)](#)

---

## 为什么用这个 Skill

大多数人写 AI 视频提示词的方式是：**一句话扔给模型**，出来的镜头要么"动作飘"、要么"表情面瘫"、要么"镜头之间跳戏"。

Echi Storyboard Director 把专业导演的镜头语言压缩成一套**可复用、可校验、纯文本**的规则集，让任何支持 Skill 的 Agent 都能按电影工业标准出分镜：

- **镜头级规范**：景别 × 机位高度 × 焦段 × 景深 × 运镜 × 构图，每一镜都写齐；
- **动作四层拆解**：预备姿势 → 发力瞬间 → 接触/命中 → 收尾反应，AI 生成的身体不再"飘"；
- **表情五官时间线**：禁止"悲伤/愤怒/震惊"这类抽象词，必须翻译成眉毛、眼睛、嘴、下颌在 0.3–1.5 秒内的肌肉变化顺序；
- **画面衔接铁律**：180° 轴线、视线匹配、运动方向一致、动作匹配切点、景别跨档；
- **引导式提问**：不会一上来就写——缺素材时按 5 步逐步追问原文、版本、风格、剪辑节奏、角色参考；
- **交付前自检**：9 条硬指标逐条过，不合格不出片。

## 它能做什么

| 你给它 | 它给你 |
|---|---|
| 一段小说 / 剧本 / 故事梗概 | 1–N 段可直接粘贴的分镜脚本 |
| Seedance 2.0 / 2.5 选择 | 严格匹配 15s/5–6 镜 或 30s/10–12 镜 |
| 风格 + 画幅 + 剪辑节奏 | 电影级构图、光影、切点 |
| 角色参考图 | 标注参考图权重（0.8 / 0.7 / 0.5） |

## 快速开始

### 在 ChatGPT / GPTs 上

1. 把 [`skill/`](skill/) 整个文件夹作为 **Knowledge files** 上传到你的 Custom GPT；
2. 在 GPT 的 Instructions 顶部粘贴 [`skill/SKILL.md`](skill/SKILL.md) 的内容；
3. 对 GPT 说："把这段小说改成分镜：……"

详细步骤见 [`docs/installation.md`](docs/installation.md#chatgpt--gpts)。

### 在 OpenAI Codex CLI 上

把 [`codex/AGENTS.md`](codex/AGENTS.md) 复制到 `~/.codex/AGENTS.md`（用户级）或你的项目根目录（项目级）。详细步骤见 [`docs/installation.md`](docs/installation.md#codex-cli)。

### 在 Claude Code / 其他 Agent 上

把 [`skill/`](skill/) 整个文件夹放进 Agent 的 skills 根目录。详细步骤见 [`docs/installation.md`](docs/installation.md#claude-code--其他-agent)。

## 示例

输入：
> 雨夜破庙，沈青衣一脚踢飞刺客的短刀，反手拔剑抵住对方咽喉。

输出（节选一镜）：
```
【18-21 秒】: [动作匹配——接剑出鞘方向] 特写，平拍，85mm 长焦浅景深，缓推，
构图：剑尖从画面右伸入，抵住刺客画左的喉结，焦点锁剑尖与皮肤接触点。
她手腕一转，剑尖斜斜压下，冰凉剑锋贴上刺客喉结——刺客眼睛先定住不动，
瞳孔放大，血色从脸上退下去，唇色变浅；舌尖无意识舔了一下干唇，喉结用力
滚一次却没敢咽到底，肩向后缩半寸，背微微弓起。一滴雨顺着剑脊滑下，
停在刃口。动作音：剑尖轻触衣领的摩擦。
```

完整示例见 [`examples/01-rainy-temple.md`](examples/01-rainy-temple.md)。

## 仓库结构

```
echi-storyboard-director/
├── skill/                      # 核心 Skill（开放标准 SKILL.md）
│   ├── SKILL.md                #   主入口：引导流程 + 工作流 + 铁律
│   └── references/
│       ├── shot-system.md      #   镜头体系 + 衔接铁律 + 画面五要素
│       ├── action-library.md   #   动作四层拆解 + 表情五官时间线
│       ├── effects-audio.md    #   光影 / 打斗 / 抒情 / 转场 / 音效
│       ├── dialogue-rules.md   #   台词字数 + 直角引号 + 拆镜
│       ├── output-template.md  #   输出模板 + 9 条自检清单
│       ├── seedance-params.md  #   Seedance 2.0 高级参数
│       └── dimensions-44.md    #   8 维 44 项进阶体系
├── codex/
│   └── AGENTS.md               # Codex CLI 适配版
├── examples/                   # 可运行示例
├── docs/                       # 安装与平台适配文档
└── assets/                     # Logo / Banner（待补充）
```

## 兼容性

| 平台 | 支持程度 | 安装方式 |
|---|---|---|
| ChatGPT / Custom GPT | ✅ 一等公民 | 上传 Knowledge files |
| OpenAI Codex CLI | ✅ 一等公民 | 复制 AGENTS.md |
| Claude Code / Claude Skills | ✅ 直接可用 | 放入 skills 目录 |
| 任何读 markdown 的 Agent | ✅ | 粘贴 SKILL.md 到系统提示词 |

## 为什么选 AGPL-3.0

这个项目采用 **GNU AGPL v3.0**。它意味着：

- ✅ 你可以自由使用、修改、分发；
- ⚠️ 如果你把修改后的版本放到**网络服务**里给别人用，必须公开你修改后的完整源码；
- ⚠️ 所有衍生作品必须同样以 AGPL-3.0 开源；
- ⚠️ 必须保留原作者署名。

**商业授权**：如果你想把本 Skill 整合进闭源产品或 SaaS，需要联系作者获取商业授权。详见 [LICENSE](LICENSE)。

> 💡 纯文本 Skill 的特性决定了它一旦公开，源码对所有人可见。AGPL-3.0 提供的是**法律层面**的保护（copyleft + 网络使用触发开源义务 + 署名要求），而不是技术加密。

## Roadmap

- [ ] 增加 Sora / Runway / Pika 的参数适配表
- [ ] 增加横屏 / 竖屏 / 方形三种画幅的构图模板
- [ ] 增加短剧、MV、广告片三种品类的预设
- [ ] 提供可交互的在线 demo

## 贡献

欢迎 PR。先读 [`CONTRIBUTING.md`](CONTRIBUTING.md)。

## 许可证

**AGPL-3.0** © Echi. 详见 [LICENSE](LICENSE)。
