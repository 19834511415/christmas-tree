---
AIGC:
    Label: "1"
    ContentProducer: 001191440300708461136T1XGW3
    ProduceID: 2e41251c7efd46a4786ccc7c29508f32_06ea88e9e2ab11f18c5752540024e231
    ReservedCode1: adQJWvZmVZGqXUYqMJQ+y4IiMZSH8hUBPfGoKowSGnUmNMAgf/W0RJ/fsP5YO2KNbaumidIEmpsMBzBo25KA65thMPh5UIrSBV0+eU+/vLVLv0xs7BnjqUCAOu2ll8zbPGijk+IXLqIvpDUdDmAnf0bXiugG37zphxeHHT8//GKy7l0QBF4aXGLl2B8=
    ContentPropagator: 001191440300708461136T1XGW3
    PropagateID: 2e41251c7efd46a4786ccc7c29508f32_06ea88e9e2ab11f18c5752540024e231
    ReservedCode2: adQJWvZmVZGqXUYqMJQ+y4IiMZSH8hUBPfGoKowSGnUmNMAgf/W0RJ/fsP5YO2KNbaumidIEmpsMBzBo25KA65thMPh5UIrSBV0+eU+/vLVLv0xs7BnjqUCAOu2ll8zbPGijk+IXLqIvpDUdDmAnf0bXiugG37zphxeHHT8//GKy7l0QBF4aXGLl2B8=
---

# Magic Christmas Tree 🎄✨

基于 WebGL (Three.js) 和计算机视觉 (MediaPipe) 的交互式 3D 圣诞树体验。

- **沉浸式 3D 视觉**：Three.js 粒子系统，金球、银块、红蓝宝石、辉光效果 (Bloom)
- **AI 手势识别**：Google MediaPipe，无需穿戴设备
- **物理交互**：握拳聚合成树、张手炸开星云、挥动旋转视角、捏合抓取照片
- **回忆画廊**：支持上传本地照片，照片化作漂浮光影

## 在线访问

部署到 GitHub Pages 后，访问 `https://<你的用户名>.github.io/<仓库名>/`

> ⚠️ 手势识别依赖摄像头，浏览器规定 `getUserMedia` 仅在 **HTTPS** 或 **localhost** 下可用。
> GitHub Pages 默认 HTTPS，所以线上可以正常玩手势；本地双击 html 文件则不行。

## 本地运行

```bash
python3 -m http.server 5191
# 打开 http://127.0.0.1:5191/
```

不要直接双击 `index.html`（`file://` 协议下摄像头和模块加载都会失败）。

## 目录结构

```
.
├── index.html                       # 全部代码（单文件，819 行）
├── models/
│   └── hand_landmarker.task         # MediaPipe 手势模型（已本地化，4.4MB）
├── .nojekyll                        # 跳过 Jekyll 处理
└── README.md
```

## 改哪里

### 1. 视觉效果 —— `index.html` 顶部 `CONFIG` 对象

```js
const CONFIG = {
    goldCount: 500,       // 金球粒子数
    silverCount: 500,     // 银块数
    gemCount: 300,        // 红蓝宝石数
    emeraldCount: 300,    // 绿宝石数
    dustCount: 1000,      // 星尘数
    treeHeight: 75,       // 树高
    maxRadius: 30,        // 最大半径
    camDistance: 110,     // 相机距离
    bloomStrength: 0.7,   // 辉光强度（越高越梦幻）
    bloomThreshold: 0.35, // 辉光阈值（调低 = 更多粒子发光）
    bloomRadius: 0.6
};
```

### 2. 交互逻辑 —— `setupMediaPipe()`（约第 566 行）

握拳、张手、挥手、捏合等手势判定都在这里。

### 3. 首屏遮罩

`#loading` 元素默认只在摄像头成功后隐藏（约第 582 行）。若用户拒绝摄像头权限，屏幕中央会残留一行 `CRAFTING MAGIC...` 文字。

## 技术栈

Three.js r160 · EffectComposer 后期处理 · MediaPipe Hand Landmarker · HTML5 / CSS3

## 原项目

<https://github.com/Vita0519/ChristmasTree>
*（内容由AI生成，仅供参考）*
