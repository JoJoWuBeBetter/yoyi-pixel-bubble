# 又一像素气泡（yoyi-pixel-bubble）

[LAPLACE Chat](https://chat.laplace.live) 的 NES 复古游戏风弹幕皮肤（模版）。
纯 CSS 实现，不包含任何 JavaScript，作为 OBS 浏览器源使用。

![预览图](预览图.png)

## 版本

| 文件 | 名称 | 说明 |
|---|---|---|
| `yoyi-pixel-bubble.css` | 又一像素气泡 | 标准版，大航海图标保持平台默认 |
| `yoyi-pixel-bubble-areca-nut.css` | 又一像素气泡 大果版 | 大航海徽章替换为槟榔胶囊（舰长=金 / 提督=银 / 总督=铜） |

## 特性

- **NES 风像素气泡**：阶梯角描边 + 阶梯小尾巴 + 硬投影，气泡恒占满行宽，弹幕长短只影响高度
- **全像素字体**：Zpix 最像素，中文英文统一像素字形
- **大航海联动**：舰长蓝 / 提督紫 / 总督红描边，气泡、头像框、徽章同步变色
- **底部锚定头像**：长弹幕撑开气泡时，头像始终与气泡底边、尾巴对齐
- **入场动画**：左侧滑入 + 过冲回弹，弹幕流速过高时自动降级关闭
- **深浅色双主题**：OBS 场景名加 `[dark]` 即切换深色配色
- 仅定制弹幕事件（`.event--message`），SC / 礼物 / 上舰等事件保持平台默认样式

## 使用方法

### 方式一：远程模版（推荐）

配置器（chat.laplace.live）→「样式」标签页 →「远程模版 URL」填入：

```text
https://cdn.jsdelivr.net/gh/你的用户名/仓库名@main/yoyi-pixel-bubble.css
```

> 远程模版有最多 5 分钟缓存，保存后稍等再刷新。

### 方式二：自定义 CSS

复制 CSS 文件全文 → OBS 浏览器源 →「自定义 CSS」粘贴
（此方式请先把文件中的 `@layer remote-css` 改为 `@layer custom-css`）

> 大果版的槟榔徽章使用仓库内 `assets/` 图片；建议通过远程模版使用。
> 若必须粘贴自定义 CSS，请将这三张图片发布到你自己可控的静态资源地址后，
> 再替换对应的 `--guard-nut` 路径。

### 建议配置

- 配置器中开启「显示头像」（本皮肤布局依赖头像列）
- 弹幕字号建议设为 **24**（Zpix 为 12px 网格设计，12 的倍数最清晰）
- 使用 `[dark]` / `[scene:xxx]` 场景联动时，OBS 浏览器源需开启
  「用户信息的读取权限」

## 目录结构

```text
├── yoyi-pixel-bubble.css              # 标准版
├── yoyi-pixel-bubble-areca-nut.css    # 大果版
└── assets/                            # 图标素材（槟榔徽章等）
```

## 技术说明

- 气泡边框与尾巴移植自 NES.css 的 Balloon 组件：
  8×8 SVG `border-image` 阶梯角 + 双伪元素 `box-shadow` 逐像素尾巴
- 大航海配色通过 CSS 变量（`--bubble-border` / `--bubble-ring`）按
  `.guard-level--1/2/3` 切换，徽章、描边、尾巴全自动同步
- 使用 `@layer` 层叠层保证与平台内置模版的优先级兼容
- 引用回复内的头像使用 `all: revert-layer` 还原平台默认样式，互不干扰

## 致谢与引用

- [NES.css](https://github.com/nostalgic-css/NES.css)（MIT）— 像素边框实现方案
- [Zpix 最像素](https://github.com/SolidZORO/zpix-pixel-font) — 中英像素字体
  （个人使用免费，商用前请查阅其仓库授权说明）
- [LAPLACE Chat](https://chat.laplace.live) — 弹幕机平台
  （[模版开发文档](https://subspace.institute/docs/laplace-chat/templates)）

## 开发工具

- 代码：**KIMI K3**（AI 辅助编写全部 CSS）
- 图片：**OpenAI GPT Image 2**（槟榔徽章等图标素材生成）

## License

CSS 代码 MIT。Zpix 字体与槟榔图标素材的授权请分别遵循其原始来源说明。
