# My-Skill-Project

一个用于存放个人 Codex skills 的仓库，目前包含多个可独立安装的 skill。

## 当前 Skills

### 1. miniprogram-prototype-designer

面向微信小程序、Taro React、uni-app、H5 和其他移动端前端产品，把需求文字整理成可交付的原型与实现导向输出。

包含内容：

- 页面结构拆解
- 用户流程梳理
- 低保真线框输出建议
- 可点击 HTML 原型输出规范
- 面向开发 Agent 的实现 Prompt

安装方式：

```bash
python C:\Users\MSI\.codex\skills\.system\skill-installer\scripts\install-skill-from-github.py --repo Fatelast/My-Skill-Project --path miniprogram-prototype-designer
```

### 2. icon-generator

根据自然语言图标需求生成可生产使用的 SVG 图标，以及 React 或 Vue 图标组件。默认优先输出 React 组件和原始 SVG。

包含内容：

- SVG 图标生成规范
- React 图标组件输出规范
- Vue 图标组件输出规范
- 图标命名与可访问性规则
- SVG 校验与组件包装辅助脚本

安装方式：

```bash
python C:\Users\MSI\.codex\skills\.system\skill-installer\scripts\install-skill-from-github.py --repo Fatelast/My-Skill-Project --path icon-generator
```

## 仓库结构

```text
miniprogram-prototype-designer/
  SKILL.md
  agents/
    openai.yaml
  references/
    html-prototype-guidelines.md
    prototype-output-template.md

icon-generator/
  SKILL.md
  agents/
    openai.yaml
  scripts/
    icon_transform.py
```

## 使用说明

- 每个 skill 都可以独立安装
- 安装后重启 Codex 以加载新 skill
- 使用时通过对应 skill 名称触发，例如 `$icon-generator`、`$miniprogram-prototype-designer`
