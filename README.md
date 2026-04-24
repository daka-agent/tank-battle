# ⚔ 经典坦克大战 - 联机版

> 经典 FC 坦克大战 Web 重制版 | 单人 · 双人 · 联机 | 零安装 · 打开即玩

![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=flat&logo=html5&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat&logo=javascript&logoColor=black)
![License](https://img.shields.io/badge/License-MIT-blue.svg)

---

## ✨ 游戏特性

| 特性 | 描述 |
|------|------|
| 🎮 三种模式 | 单人对战 · 本地双人 · 跨电脑联机 |
| 🌐 P2P 联机 | PeerJS (WebRTC) 直连，无需搭建服务器 |
| 🤖 智能 AI | 敌方坦克自动寻路，偏向攻击玩家与司令部 |
| 🧱 可破坏地形 | 砖墙可击碎，钢墙不可摧毁 |
| 🦅 司令部防守 | 底部中央，被击中即游戏结束 |
| 🏆 积分系统 | 击杀 +100 分，过关 +500 分 |
| 📈 关卡递进 | 3 种地图布局循环，难度逐关提升 |
| ❤️ 多命机制 | 3 条命/人，重生 2 秒无敌闪烁 |
| 🎵 8-bit 音效 | 程序化生成背景音乐及全部音效，无外部文件 |

---

## 🚀 快速开始

直接用浏览器打开 `index.html` 即可游玩，**无需安装任何依赖**。

```bash
git clone https://github.com/daka-agent/tank-battle.git
cd tank-battle
# 双击 index.html 或用浏览器直接打开
```

---

## 🎮 操作方式

### 本地对战

| 操作 | 玩家1 🟢 | 玩家2 🔵 |
|:----:|:--------:|:--------:|
| 上 | ↑ | W |
| 下 | ↓ | S |
| 左 | ← | A |
| 右 | → | D |
| 射击 | 空格 | F |
| 暂停 | P | P |
| 静音 | M | M |
| 重新开始 | R | R |

### 联机对战

| 操作 | 房主 🟢 | 加入者 🔵 |
|:----:|:-------:|:---------:|
| 移动 | 方向键 | W A S D |
| 射击 | 空格 | F |
| 暂停 | P | — |
| 静音 | M | M |

---

## 🌐 联机对战指南

### 操作步骤

```
玩家A（房主）                    玩家B（加入者）
    │                                │
    ├─ 联机对战 → 创建房间           ├─ 联机对战 → 加入房间
    ├─ 获得 6 位房间号 ──────────→  ├─ 输入房间号 → 连接
    ├─ 看到「好友已连接」            ├─ 等待房主开始
    ├─ 点击「开始游戏！」            │
    │                                │
    └────── 🎮 游戏开始！ ──────────┘
```

### 前提条件

- 两台电脑均需互联网访问（P2P 连接，游戏数据直传）
- 现代浏览器（Chrome / Edge / Firefox）
- ⚠️ **国内用户**：PeerJS 信令服务器可能需要科学上网

### 技术架构

```
[P1 房主]                           [P2 加入者]
键盘输入 → 游戏逻辑 → Canvas渲染      键盘输入 → 发送按键
              ↑                         │
         接收按键 ←──── 网络传输 ←──────┘
              │
         状态快照 ────→ 网络传输 ────→ Canvas渲染
```

- **PeerJS** (WebRTC) P2P 直连，零服务器部署
- **主机权威**架构：房主运行完整游戏逻辑，加入者仅渲染+发输入
- 约 33ms 同步一次，实时延迟显示
- 自动尝试多个信令服务器配置
- 断线自动检测并提示

---

## 🛠 技术实现

| 项目 | 技术 |
|------|------|
| 渲染 | Canvas 2D，624×624px（26×26 格 × 24px） |
| 坦克 | 48×48px（2 格），带履带动画 |
| 游戏循环 | `requestAnimationFrame` 60fps |
| 音效 | Web Audio API 程序化生成，无外部文件 |
| 联机 | PeerJS (WebRTC)，单 CDN 引用 |
| 架构 | 单文件，零构建，零依赖安装 |

---

## 📁 项目结构

```
tank-battle/
├── index.html     # 完整游戏（HTML + CSS + JavaScript）
├── LICENSE        # MIT 许可证
├── README.md      # 项目说明
└── .gitignore     # Git 忽略规则
```

---

## 📜 许可证

[MIT License](LICENSE)
