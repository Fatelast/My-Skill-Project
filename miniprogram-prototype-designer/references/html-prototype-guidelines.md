# HTML Prototype Guidelines

当用户要求最终交付“可交互原型文件”时，默认优先使用 `HTML`。

## 目标

输出一个可以直接在本地打开的交互原型目录，而不是只输出文档说明。

## 输出边界

- 原型文件统一输出到项目根目录下新建的 `prototype-output/`
- 不得把原型 HTML、CSS、JS、mock 文件直接写入现有业务目录
- 不得修改现有 `src/`、`pages/`、`components/`、`config/`、`public/` 等原项目目录
- 除非用户明确取消该限制，否则必须保持“原型目录”和“业务代码目录”隔离

## 推荐目录结构

```text
prototype-output/
  index.html
  pages/
    home.html
    list.html
    detail.html
    form.html
    result.html
    mine.html
  assets/
    common.css
    pages.css
    app.js
    mock.js
```

## 最低交付要求

- 至少有一个入口页
- 至少覆盖主流程页面
- 页面可通过点击跳转
- 筛选、弹层、Tab、表单、成功反馈等关键交互可演示
- 不依赖后端接口
- 使用本地 mock 数据
- 所有原型资源都在 `prototype-output/` 内闭环

## 页面职责建议

- `index.html`
  - 作为统一入口或默认首页
- `pages/*.html`
  - 承担每个核心页面
- `assets/common.css`
  - 全局变量、基础布局、通用组件样式
- `assets/pages.css`
  - 页面级差异样式
- `assets/app.js`
  - 点击跳转、弹层开关、Tab 切换、表单提交模拟
- `assets/mock.js`
  - 线路、用户、记录等 mock 数据

## 交互要求

至少覆盖以下类型：

- 页面跳转
- Tab 切换
- 抽屉或底部弹层开关
- 筛选确认或重置
- 表单填写与校验提示
- 成功页跳转

## 样式要求

- 以移动端竖屏为主
- 页面宽度模拟手机容器
- 结构清晰，不追求品牌视觉稿级别效果
- 字号、间距、按钮层级明确
- 多页面风格一致

## 回退规则

以下情况不要伪造专有格式：

- 用户说要 `.sketch`，但本地没有稳定生成链路
- 用户说要 `.mp`，但没有明确具体工具格式

此时统一回退：

1. 明确说明回退到 `HTML`
2. 仍然交付完整交互原型目录

## 与 Taro / React / uni-app 的关系

如果用户后续要继续开发：

- 可在 HTML 原型后补一段开发映射说明
- 标明哪些页面将映射到 Taro 页面
- 标明哪些交互对应 hooks、store、services

不要在生成 HTML 原型时强制混入完整业务代码实现。
