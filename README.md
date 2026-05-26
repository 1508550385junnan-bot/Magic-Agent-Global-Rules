# Magic Agent Global Rules 智能体全局协作规则

> v2.5 | 2026-05-26 | 中英双语 | Skill 格式
> 适用于所有 AI 智能体交互，不限于单一项目

---

## 一句话

**不要替我做决定，不要省略内容，不要给我摘要当交付物。给我完整的、可直接执行的全量内容。**

> Don't make decisions for me. Don't omit content. Give me complete, executable, full output.

---

## 文件说明

本仓库提供双语规则，按你的模型选择：

| 模型 | 用哪个 | 装哪里 |
|------|--------|--------|
| DeepSeek / 国内模型 | `CLAUDE.md`（中文完整版） | 项目根目录 |
| Claude / GPT / Gemini | `AGENTS.md`（英文完整版） | 项目根目录 |
| 任意模型（skill 方式） | `skills/global-collaboration-rules/` | `npx skills add` 或 `~/.hermes/skills/` |

---

## 快速安装

```bash
# 中文版（DeepSeek / 国内模型）
curl -o CLAUDE.md https://raw.githubusercontent.com/1508550385junnan-bot/Magic-Agent-Global-Rules/main/CLAUDE.md

# 英文版（Claude / GPT / Gemini）
curl -o CLAUDE.md https://raw.githubusercontent.com/1508550385junnan-bot/Magic-Agent-Global-Rules/main/AGENTS.md

# 安装为 Skill
npx skills add 1508550385junnan-bot/Magic-Agent-Global-Rules@global-collaboration-rules
```

---

## 13 节核心内容

| 节 | 内容 | 亮点 |
|----|------|------|
| 一 | 我对智能体的使用逻辑 | 执行者不是顾问，目标→方案→执行→验收 |
| 二 | 输出规范 | 完整性最高优先级，每次交付含自检清单 |
| 三 | 风格偏好 | 直接、务实、精确、诚实 |
| 四 | 踩坑经验 | 智能体常犯 7 个错误 + 修复方案 |
| 五 | 任务执行框架 | 5 步流程：理解→拆解→计划→执行→交付 |
| 六 | 场景要求 | 代码生成/文档/方案/数据/调试专项规则 |
| 七 | 绝对禁止 | 12 条：不省略、不假装、不漂移、不蔓延... |
| 八 | 快速参考卡 | ASCII 速查 |
| 九 | 上下文防丢失 | 需求固化 R1/R2/R3 + 防漂移三问 + 3-Strike |
| 十 | 技能借力+图像兜底+压缩 | 搜 skills 优先、Pillow 替代 vision、85% 自动压缩 |
| 十一 | Token 优化 | 四战场：缓存 90% + 沙箱 98% + 输出 75% + JIT 加载 |
| 十二 | 中文全链路 | 交流/思考/注释/commit 全中文 |
| 十三 | 代码注释+执行边界+提示词解析 | 思考过程有则代码不注释、逗号=子要求、句号=模块 |

---

## Token 节约预估

| 优化手段 | 方法 | 效果 |
|----------|------|------|
| 输入缓存 | System Prompt 静态前置 + 只追加不插入 | 命中时成本降至 10% |
| 工具输出沙箱 | 原始数据写文件，上下文只注摘要 | 98% 削减 (56KB→1.2KB) |
| Think-in-Code | 写脚本统计，不逐个 Read() 文件 | 195x 节省 (700KB→3.6KB) |
| 输出去冗余 | 去寒暄、去客套、不重复 | 20-75% |
| 代码不注释 | 思考过程已解释，代码不加注释 | 10-20% |
| Skills JIT | 不用的不加载 | 按需 |

---

## 核心规则速查

```
逗号(，) = 子要求 → 小自检
句号(。) = 模块   → 大自检
长/AI提示词 → 用 planning-with-files

没要求的 = 不做不改
要求的   = 一字一句完成
为完成要求而改已有 → 允许
扩展需求/顺便优化 → 禁止

代码注释 = 不加（思考过程已解释，省 token）
例外：魔法数字 / TODO / 正则 / 用户要求加

改代码前 = 读 REQUIREMENTS.md
每 5 轮   = 防漂移三问
80% 上下文 = 提示 | 85% = 九段式自动压缩

技术内容一字不少，寒暄废话一字不多
文件路径引用 > 对话中粘贴
脚本统计分析 > 逐个文件读取
```

---

## 作者

**大虎子** — [AI 工具一键下载](https://github.com/1508550385junnan-bot/ai-tools-one-click-download) 开发者

## 许可

MIT
