# Magic Agent 全局规则 / Magic Agent Global Rules

> v2.9 | 2026-05-27 | 中英双语 | Skill 格式
> 适用于所有 AI 智能体交互，不限于单一项目
>
> **德扑讲牌力，AI 讲规则力 — 规则越强，输出越硬。**
> Strong rules → strong output. Garbage rules → garbage output.

---

## 一句话 / One-Liner

**不要替我做决定，不要省略内容，不要给我摘要当交付物。给我完整的、可直接执行的全量内容。**

> Don't make decisions for me. Don't omit content. Give me complete, executable, full output.

---

## 文件说明 / Which File?

本仓库提供双语规则，按你的模型选择：

| 模型 | 用哪个 | 装哪里 |
|------|--------|--------|
| DeepSeek / 国内模型 | `CLAUDE.md`（中文完整版） | 项目根目录 |
| Claude / GPT / Gemini | `AGENTS.md`（英文完整版） | 项目根目录 |
| 任意模型（skill 方式） | `skills/global-collaboration-rules/` | `npx skills add` 或 `~/.hermes/skills/` |

---

## 快速安装 / Quick Install

```bash
# 中文版（DeepSeek / 国内模型）
curl -o CLAUDE.md https://raw.githubusercontent.com/1508550385junnan-bot/Magic-Agent-Global-Rules/main/CLAUDE.md

# 英文版（Claude / GPT / Gemini）
curl -o CLAUDE.md https://raw.githubusercontent.com/1508550385junnan-bot/Magic-Agent-Global-Rules/main/AGENTS.md

# 安装为 Skill
npx skills add 1508550385junnan-bot/Magic-Agent-Global-Rules@global-collaboration-rules
```

---

## 为什么需要这套规则？ / Why This?

AI 助手最大的问题不是"不够聪明"，而是**太爱自由发挥**——给半成品、爱省略、假装执行、顺手"优化"你没要求的东西。

这套规则经过数百次迭代，把 AI 的行为约束到"可靠"级别。放入项目根目录，AI 读一遍，输出质量立刻不一样。

> The biggest problem with AI assistants isn't intelligence — it's **scope creep**. Half-finished work, skipped steps, fake execution, unauthorized "optimizations."
>
> These rules, refined over hundreds of iterations, lock AI behavior down to "reliable." Drop into your project root, and output quality changes immediately.

---

## 16 节核心内容 / 16 Sections

| 节 | 内容 | 亮点 |
|----|------|------|
| 一 | 提示词解析（最高优先级） | 逗号=子要求、句号=模块、长提示词用 planning-with-files |
| 二 | 中文全链路 | 交流/思考/注释/commit/文档全中文，技术术语保留英文 |
| 三 | 需求锁定 | R1/R2/R3 编号固化 + 防漂移三问，杜绝 AI 自由发挥 |
| 四 | 需求执行边界 | 没要求的不做不改，要求的逐字完成，禁止范围蔓延 |
| 五 | 代码注释策略 | 思考过程已解释则代码不注释，省 token。例外：魔法数字/TODO/正则 |
| 六 | 绝对禁止 12 条 | 不省略、不假装、不漂移、不蔓延、不以优化为名改代码… |
| 七 | 安全规则 | 密钥不进 git、操作前确认、依赖安全审计 |
| 八 | 代码质量标准 | 类型标注、单一职责<30行、不静默吞异常、YAGNI |
| 九 | Token 优化四战场 | 输入缓存 90% + 沙箱 98% + 输出 75% + Skills JIT 加载 |
| 十 | 创新方法论 | 25 种方法·9 步流程·20 本书，触发词自动激活 |
| 十一 | 上下文管理 | 80% 提示、85% 九段式自动压缩、跨会话恢复 |
| 十二 | 技能借力与图像兜底 | 搜 skills 优先、Pillow 替代 vision、不做伸手党 |
| 十三 | 3-Strike 错误协议 | 诊断→换方法→重新思考，3 次失败升级给用户 |
| 十四 | 规则豁免 | ≤3 步简单任务/单文件编辑/信息查询/纯讨论快速通道 |
| 十五 | Skills 索引 | 本地 40+ 技能触发映射 + 跨仓库借力流程 |
| 十六 | 交付规范 | 完整内容+自检清单+文件路径+已知问题 |

---

## Token 节约预估 / Token Savings

| 优化手段 | 方法 | 效果 |
|----------|------|------|
| 输入缓存 | System Prompt 静态前置 + 只追加不插入 | 命中时成本降至 10% |
| 工具输出沙箱 | 原始数据写文件，上下文只注摘要 | 98% 削减 (56KB→1.2KB) |
| Think-in-Code | 写脚本统计，不逐个 Read() 文件 | 195x 节省 (700KB→3.6KB) |
| 输出去冗余 | 去寒暄、去客套、不重复 | 20-75% |
| 代码不注释 | 思考过程已解释，代码不加注释 | 10-20% |
| Skills JIT | 不用的不加载 | 按需 |

---

## 核心规则速查 / Quick Reference

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

## 适用场景 / Use Cases

- 🤖 **Cursor / Windsurf / Copilot** — 放入 `.cursorrules` 或项目根目录
- 🧠 **Claude Code / Codex CLI** — 项目根目录放 CLAUDE.md 或 AGENTS.md
- ⚡ **Hermes Agent** — 安装为 Skill，自动加载
- 📋 **所有 AI 编程助手** — 通用规则，不限于特定工具

---

## 与其他规则对比 / vs Others

| | Magic Agent Rules | cursorrules 社区 | Awesome CursorRules |
|---|---|---|---|
| 需求锁定 | ✅ R1/R2/R3 固化 | ❌ | ❌ |
| Token 优化 | ✅ 四战场系统 | ❌ | ❌ |
| 防漂移机制 | ✅ 每 5 轮三问 | ❌ | ❌ |
| 上下文压缩 | ✅ 九段式模板 | ❌ | ❌ |
| 中文支持 | ✅ 全链路中文 | ❌ | ❌ |
| Skills 生态 | ✅ 40+ 技能联动 | ❌ | ❌ |

---

## 作者 / Author

**大虎子 (DaHuzi)** — 独立开发者

- [AI 工具一键下载](https://github.com/1508550385junnan-bot/ai-tools-one-click-download) — Windows AI 开发环境一键安装器

## 许可 / License

MIT
