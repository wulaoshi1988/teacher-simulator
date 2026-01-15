# 🎓 教师模拟器 - Teacher Simulator

一个以教师职业体验为核心的文字RPG游戏，讲述新教师在星光中学的成长故事。

## 📖 项目简介

**教师模拟器**是一款基于Vue 3 + Pinia开发的互动叙事游戏。玩家扮演一名刚入职星光中学的新教师，在一个季度的教学周期中，通过做出各种选择，体验教育工作的酸甜苦辣。

### 核心理念

- **氛围编程**：快速迭代，注重体验
- **数值系统**：管理精力、教学能力、人际关系等多维数值
- **随机事件**：面对教学危机、家校沟通、师生关系等挑战
- **多重结局**：根据你的选择，走向不同的结局

## 🛠 技术栈

- **前端框架**: Vue 3.4+ (Composition API)
- **构建工具**: Vite 5.0+
- **状态管理**: Pinia 2.1+ (官方推荐)
- **类型系统**: TypeScript 5.0+
- **样式方案**: Tailwind CSS 3.4+
- **持久化**: pinia-plugin-persistedstate
- **部署**: Vercel (免费托管)

## 🎮 游戏玩法

### 核心数值

| 数值 | 说明 | 范围 |
|------|------|------|
| ⚡ 精力值 | 核心行动资源 | 0-100 |
| 📚 教学能力 | 影响学生成绩提升 | 0-100 |
| 👥 班级管理 | 影响课堂氛围 | 0-100 |
| ❤️ 学生好感 | 学生对你的信任度 | 0-100 |
| 📱 家长沟通 | 与家长的关系 | 0-100 |
| 💼 领导评价 | 上级的认可度 | 0-100 |
| 🏥 健康值 | 长期高压会下降 | 0-100 |
| 🌙 个人时间 | 用于自我提升 | 0-100 |

### 行动类别

1. **📚 教学与班务**: 精心备课、常规上课、课后辅导、主题班会
2. **💬 人际与沟通**: 家访、教研、向上管理、同事协作
3. **🌿 个人与修养**: 读书充电、健身运动、社交放松

### 随机事件

游戏中会随机触发各种事件，需要玩家即时做出应对：
- 📚 公开课危机
- 📱 家长群争议
- ⚡ 学生打架
- 📋 "双减"难题
- 🏥 体检警报

### 多重结局

- 🕯️ 【燃烧的蜡烛】- 能力强但健康耗尽
- 📈 【精致的利己主义者】- 精通规则但失去初心
- 🌻 【幸福的园丁】- 平衡发展的幸福结局
- ✨ 【初心未泯】- 理想主义者的坚持
- 🚪 【中途离场】- 健康或压力问题导致退出
- 📚 【平凡的起点】- 继续前行的普通结局

## 🚀 快速开始

### 环境要求

- Node.js 18+ 
- npm 或 pnpm

### 安装步骤

```bash
# 1. 克隆项目
cd teacher-simulator

# 2. 安装依赖
npm install

# 3. 启动开发服务器
npm run dev

# 4. 构建生产版本
npm run build
```

### 访问游戏

开发模式: http://localhost:3000

构建后: `dist/` 目录下的文件

## 📁 项目结构

```
teacher-simulator/
├── src/
│   ├── components/          # Vue组件
│   │   ├── common/         # 通用组件
│   │   ├── game/          # 游戏组件
│   │   │   ├── StatsPanel.vue     # 数值面板
│   │   │   ├── ActionMenu.vue     # 行动菜单
│   │   │   ├── EventDisplay.vue   # 事件展示
│   │   │   ├── QuarterSummary.vue # 季度总结
│   │   │   └── EndingScreen.vue   # 结局画面
│   │   └── layout/        # 布局组件
│   ├── stores/            # Pinia状态管理
│   │   ├── statsStore.ts  # 数值系统
│   │   ├── gameStore.ts   # 游戏流程
│   │   ├── eventStore.ts  # 事件系统
│   │   └── uiStore.ts     # UI状态
│   ├── composables/       # 组合式函数
│   ├── types/             # TypeScript类型
│   ├── data/              # 游戏数据
│   │   ├── actions.ts     # 行动定义
│   │   ├── events.ts      # 事件定义
│   │   └── endings.ts     # 结局定义
│   ├── utils/             # 工具函数
│   ├── App.vue            # 应用入口
│   └── main.ts            # 应用配置
├── public/                # 静态资源
├── index.html
├── package.json
├── vite.config.ts
├── tailwind.config.js
└── tsconfig.json
```

## 🎨 设计特点

### 1. 简约文字风格
- 专注文字和内容，减少视觉干扰
- 使用emoji增强表达
- 清晰的数值可视化

### 2. 响应式设计
- 移动端：垂直堆叠布局
- 桌面端：左右分栏布局
- 适配各种屏幕尺寸

### 3. 流畅动画
- 数值变化的过渡效果
- 弹窗的淡入淡出
- 按钮的悬停反馈

## 🔧 自定义扩展

### 添加新行动

在 `src/data/actions.ts` 中添加：

```typescript
{
  id: 'unique_id',
  name: '行动名称',
  category: 'teaching', // teaching | class_management | communication | personal
  description: '行动描述',
  energyCost: 10,
  baseEffects: {
    teachingAbility: 5,
    // ...其他效果
  }
}
```

### 添加新事件

在 `src/stores/eventStore.ts` 的 `events` 数组中添加：

```typescript
{
  id: 'unique_id',
  title: '事件标题',
  description: '事件描述',
  type: 'crisis', // crisis | social | emergency | opportunity
  baseProbability: 20,
  choices: [
    {
      id: 'choice_id',
      description: '选择描述',
      energyCost: 10,
      statChanges: { /* 效果 */ },
      successRate: 80
    }
  ]
}
```

### 调整数值平衡

在 `src/stores/statsStore.ts` 中修改：
- 初始数值
- 消耗公式
- 恢复机制

## 📝 开发日志

### v1.0.0 (2024.01.15)
- ✨ 初始版本发布
- 📊 完整的数值系统
- 🎲 8个随机事件
- 🏆 6个结局
- 📱 响应式设计
- 💾 存档功能

## 🤝 贡献指南

欢迎贡献！请提交Issue或Pull Request。

## 📄 许可证

MIT License

## 🙏 致谢

- Vue.js 团队
- Pinia 团队
- Tailwind CSS 团队
- 所有测试玩家

---

**🎓 一个关于教育、理想与现实的游戏**

*基于真实教师经历改编*
"# teacher-niuma" 
"# teacher-niuma" 
