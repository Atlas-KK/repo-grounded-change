# Repo Grounded Change Skill

用于在现有代码仓库中评估并实施代码、UI、交互、重构或架构改动的 Codex Skill。它先以代码和测试为证据理解现状，再比较方案、形成可验收的修改规格，并在用户明确批准后实施。

## 适用场景

- 先评估再改造现有功能。
- 比较多种实现方案及其兼容性、风险和成本。
- 在动手前形成明确的范围、验收标准和回滚边界。
- 对 UI、交互、架构或重构方案执行确认门禁。

如果用户已经给出直接、无歧义且没有重大方案选择的实现任务，通常不需要使用本 Skill。

## 工作流程

1. 检查仓库、当前行为和工作树状态。
2. 将用户痛点转换为可观察目标和约束。
3. 比较 2–3 个可行方案及其产品和工程影响。
4. 输出可直接执行的修改规格与验收标准。
5. 等待用户明确批准方案。
6. 按批准范围实施并验证。
7. 报告变更、检查结果与剩余风险。

## 安装

用户级安装路径：

```text
$HOME/.agents/skills/repo-grounded-change/SKILL.md
```

项目级安装路径：

```text
<项目目录>/.agents/skills/repo-grounded-change/SKILL.md
```

Codex 通常会自动发现 Skill；如果没有出现，请重启 Codex。

## 使用示例

```text
$repo-grounded-change 先评估当前登录流程的问题，给出方案，我确认后再修改
```

```text
$repo-grounded-change 比较两种缓存改造方式，说明兼容性和测试影响
```

## 仓库结构

| 路径 | 说明 |
| --- | --- |
| `SKILL.md` | 授权边界、证据标签、七步工作流和停止条件 |
| `references/discovery-and-impact.md` | 现状取证与影响分析 |
| `references/options-and-clarification.md` | 方案比较与澄清规则 |
| `references/change-spec-and-acceptance.md` | 修改规格和验收标准 |
| `agents/openai.yaml` | Codex 中的 Skill 展示配置 |

## 核心原则

- 先读取仓库证据，不向用户询问代码中可以发现的事实。
- 未获得明确批准前保持只读。
- 保护用户已有修改，不夹带无关清理。
- 新证据若改变已批准的行为、范围或迁移策略，应停止并重新确认。

## 相关文档

- [Skill 主说明](./SKILL.md)
- [现状取证与影响分析](./references/discovery-and-impact.md)
- [方案比较与澄清](./references/options-and-clarification.md)
- [修改规格与验收](./references/change-spec-and-acceptance.md)
- [OpenAI：Build skills](https://developers.openai.com/codex/skills)
