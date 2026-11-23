# 🐍 贪吃蛇小游戏 | Classic Snake Game

一个精美的、功能完整的贪吃蛇网页游戏，使用纯 HTML/CSS/JavaScript 实现，无需任何外部依赖。

![Game Preview](https://img.shields.io/badge/HTML5-Game-orange)
![CSS3](https://img.shields.io/badge/CSS3-Styled-blue)
![JavaScript](https://img.shields.io/badge/JavaScript-ES6+-yellow)
![License](https://img.shields.io/badge/License-MIT-green)

## ✨ 游戏特色

### 🎮 核心玩法
- **经典贪吃蛇机制** - 控制蛇移动吃食物，身体变长，避免撞墙和撞自己
- **渐进式难度** - 每吃 5 个食物速度提升，挑战随分数增加而递增
- **最高分记录** - 使用 `localStorage` 自动保存最高分，刷新页面不丢失
- **奖励食物系统** - 15% 概率生成金色星形奖励食物（50 分），存在 5 秒后消失

### 🎨 视觉效果
- **现代化深色主题** - 优雅的渐变背景，玻璃态 UI 设计
- **蛇身交替配色** - 蛇身段落交替显示两种绿色，头部发光效果
- **精美食物渲染** - 普通食物为带高光的苹果造型，奖励食物为闪烁星形
- **动画反馈** - 吃食物时画布缩放动画，按钮悬停/点击动效
- **网格背景** - 细微网格线增强游戏区域层次感

### 🎯 操作方式
| 操作 | 键盘 | 触屏/鼠标 |
|------|------|-----------|
| 向上 | `W` / `↑` | 点击 ↑ 按钮 |
| 向下 | `S` / `↓` | 点击 ↓ 按钮 |
| 向左 | `A` / `←` | 点击 ← 按钮 |
| 向右 | `D` / `→` | 点击 → 按钮 |
| 暂停/开始 | `Space` | 点击暂停/开始按钮 |

### 📱 响应式设计
- 完美适配桌面端、平板、手机
- 移动端专用触控方向键
- 自适应画布尺寸

## 🚀 快速开始

### 在线体验
直接在浏览器中打开 `snake.html` 即可游玩，无需服务器、无需构建。

```bash
# 克隆仓库
git clone https://github.com/yourusername/snake-game.git
cd snake-game

# 直接用浏览器打开 snake.html
# Windows
start snake.html
# macOS
open snake.html
# Linux
xdg-open snake.html
```

### 本地运行
由于使用了 `localStorage`，建议通过本地服务器运行（避免 `file://` 协议限制）：

```bash
# Python 3
python -m http.server 8000

# Node.js (npx)
npx serve .

# PHP
php -S localhost:8000
```

然后访问 `http://localhost:8000/snake.html`

## 📁 项目结构

```
snake-game/
├── snake.html    # 完整游戏文件（HTML + CSS + JS）
├── README.md     # 本文档
└── LICENSE       # MIT 许可证
```

**单文件架构** - 所有代码包含在 `snake.html` 中：
- **HTML** - 语义化结构，无障碍访问支持（ARIA 标签）
- **CSS** - 现代 CSS（Grid/Flexbox、CSS 变量、动画、媒体查询）
- **JavaScript (ES6+)** - 模块化游戏逻辑，无外部依赖

## ⚙️ 游戏配置

可在 `snake.html` 的脚本顶部修改常量：

```javascript
const GRID_SIZE = 20;        // 格子大小 (px)
const CANVAS_SIZE = 400;     // 画布尺寸 (px)
const GRID_COUNT = 20;       // 网格数量 (CANVAS_SIZE / GRID_SIZE)
const INITIAL_SPEED = 150;   // 初始速度 (ms/帧，越小越快)
const SPEED_INCREMENT = 2;   // 每 5 个食物加速量
const MIN_SPEED = 60;        // 最高速度限制
```

### 颜色主题
```javascript
const COLORS = {
    bg: '#0d1117',           // 背景色
    grid: '#1f2428',         // 网格线
    snakeHead: '#00ff88',    // 蛇头
    snakeBody: '#2ea043',    // 蛇身主色
    snakeBodyAlt: '#238636', // 蛇身交替色
    food: '#f85149',         // 普通食物
    foodGlow: '#ff7b72',     // 食物发光
    bonusFood: '#ffd700',    // 奖励食物
    bonusFoodGlow: '#fff5b1' // 奖励食物发光
};
```

## 🎯 游戏机制详解

### 计分系统
- **普通食物**：+10 分
- **奖励食物（金星）**：+50 分，15% 生成概率，5 秒后消失
- **长度显示**：实时显示蛇身长度

### 速度机制
- 初始间隔：150ms/帧
- 每吃 5 个食物减少 2ms
- 最快限制：60ms/帧

### 碰撞检测
- **墙壁碰撞** - 蛇头超出画布边界
- **自身碰撞** - 蛇头与身体任意段重叠
- **防 180° 转向** - 禁止直接反向移动

### 状态管理
```
初始态 → 运行态 ↔ 暂停态 → 结束态 → 重新开始
```

## 🛠️ 技术亮点

| 特性 | 实现方式 |
|------|----------|
| 游戏循环 | `setInterval` + 动态重启实现变速 |
| 状态持久化 | `localStorage` 存储最高分 |
| 绘图引擎 | Canvas 2D API |
| 圆角矩形 | `quadraticCurveTo` 手绘 |
| 星形绘制 | 三角函数计算顶点 |
| 径向渐变 | `createRadialGradient` 食物高光 |
| 阴影发光 | `shadowBlur` + `shadowColor` |
| 响应式 | CSS Grid + Flexbox + 媒体查询 |
| 无障碍访问 | 语义化 HTML + ARIA labels |

## 📝 待办 / 扩展想法

- [ ] 添加音效（吃食物、游戏结束、按钮点击）
- [ ] 粒子特效（吃食物时的爆炸动画）
- [ ] 关卡/地图系统（障碍物、传送门）
- [ ] 皮肤系统（不同蛇身颜色主题）
- [ ] 排行榜（本地/云端）
- [ ] 触屏滑动手势控制
- [ ] PWA 支持（离线游玩、安装到主屏幕）
- [ ] 多人对战模式（WebRTC）

## 🤝 贡献指南

欢迎提交 Issue 和 Pull Request！

1. Fork 本仓库
2. 创建特性分支：`git checkout -b feature/amazing-feature`
3. 提交更改：`git commit -m 'Add amazing feature'`
4. 推送分支：`git push origin feature/amazing-feature`
5. 发起 Pull Request

## 📄 许可证

本项目采用 [MIT License](LICENSE) 开源许可证。

## 🙏 致谢

- 灵感来源：经典诺基亚贪吃蛇
- 字体：系统默认字体栈（Segoe UI / Tahoma / Geneva / Verdana / sans-serif）
- 图标：Unicode 字符（↑ ↓ ← →）

---

<div align="center">
  <p>如果这个项目给你带来了快乐，请给个 ⭐ Star 支持一下！</p>
  <p>Made with ❤️ for fun</p>
</div>