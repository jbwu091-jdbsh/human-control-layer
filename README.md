# Human Control Layer Skill

[English](README.en.md)

把当前项目状态压缩成三份给负责人看的短文档，让不阅读源码的人也能在 5～10 分钟内理解：系统是什么、主要部分怎样协作、做到哪里、风险是什么、为什么采用当前结构。

## 何时使用

在用户明确要求当前项目快照、重要阶段完成，或旧文档已明显误导负责人时创建或更新。普通 Bug、小功能、一次提交或常规任务完成不会自动触发。它只描述**当前状态**；重大变更实施前的决策材料由独立的 [Human Diff](https://github.com/jbwu091-jdbsh/human-diff) 负责。

## 安装到 Codex

```bash
python3 ~/.codex/skills/.system/skill-installer/scripts/install-skill-from-github.py \
  --repo jbwu091-jdbsh/human-control-layer --path . --name human-control-layer
```

安装后开启新对话即可使用；也可明确说“用 human-control-layer 更新这个项目的当前快照”。其他支持 Markdown 指令包的 Agent/Harness 可直接读取 `SKILL.md` 与模板，无需 Codex 专有 API。

## 项目输出

```text
docs/human/
├── HCL-PROJECT_MAP.md       # 系统边界、模块、数据流
├── HCL-CURRENT_STATE.md     # 阶段、进展、风险、下一步
├── HCL-DECISIONS.md         # 仍生效的重要决策
└── archive/                 # 仅在需要保存已失效历史时创建
```

首次创建时用 [`templates/`](templates/) 中的三个模板填入真实项目证据。更新时只修改确实过时的文件，删除或归档失效内容，不追加任务流水账。建议长度分别约为 1500–2500、800–1500、2000–3000 中文字。

## 仓库内容

- `SKILL.md`：触发、证据、更新和压缩规则。
- `templates/`：三个 `HCL-` 前缀的项目文档模板。
- `README.md` / `README.en.md`：中英文使用说明。

v0.1 为纯 Markdown Skill，不依赖脚本、数据库、Hook 或特定 Harness。
