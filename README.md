# miniprogram-prototype-designer

一个用于 Codex 的 skill，面向微信小程序、Taro React、uni-app、H5 和其他移动端前端产品，把需求文字整理成可交付的原型与实现导向输出。

## 包含内容

- 页面结构拆解
- 用户流程梳理
- 低保真线框输出建议
- 可点击 HTML 原型输出规范
- 面向开发 Agent 的实现 Prompt

## 仓库结构

```text
miniprogram-prototype-designer/
  SKILL.md
  agents/
    openai.yaml
  references/
    html-prototype-guidelines.md
    prototype-output-template.md
```

## 安装方式

如果你已经安装了 Codex，并且本地带有 `skill-installer`，可以通过 GitHub 安装：

```bash
python C:\Users\MSI\.codex\skills\.system\skill-installer\scripts\install-skill-from-github.py --repo <owner>/miniprogram-prototype-designer --path miniprogram-prototype-designer
```

安装后重启 Codex 以加载新 skill。

## 适用场景

- 根据 PRD 生成页面原型
- 根据需求拆分页面、组件和流程
- 输出独立目录下的 HTML 交互原型
- 生成可直接交给前端开发 Agent 的实现提示词

## 注意事项

- 该 skill 默认优先输出中文内容
- 默认原型产物输出到独立的 `prototype-output/` 目录
- 默认不直接修改现有业务代码目录
