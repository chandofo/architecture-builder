# architecture-builder
Regarding the generation of functional architecture diagrams

https://youtu.be/FbxpN0qgRME

# 功能架构图生成器

一个通用的功能架构图可视化工具，支持 JSON 配置驱动、在线编辑、拖拽调整、导出图片/PPT。

## ✨ 功能特性

| 功能     | 说明                                       |
| ------ | ---------------------------------------- |
| 5种层级类型 | module/capability/process/component/data |
| 灵活布局   | 能力容器支持宽度倍数（1-6倍）、列数配置                    |
| 在线编辑   | 所有文字点击即可编辑                               |
| 拖拽排序   | 层级、卡片、能力组都支持拖拽调整顺序                       |
| 主题定制   | 颜色、字体、间距全方位可配置                           |
| 导出功能   | PNG图片、剪贴板、PPTX、JSON配置                    |
| 画布调整   | 右下角拖拽手柄自由调整画布大小                          |

## 📁 目录结构

```
architecture-builder/
├── README.md                    # 项目说明文档
├── skill/
│   └── SKILL.md                # Skill 详细说明
├── src/
│   ├── architecture-builder.html    # 主程序
│   └── templates/
│       └── architecture-config-template.json  # 配置模板
├── examples/
│   └── project-management-architecture.json  # 示例配置
└── docs/
    └── agent-prompt.md          # AI 智能体提示词
```

## 🚀 快速开始

### 方式1：直接打开

1. 用浏览器打开 `src/architecture-builder.html`
2. 开始编辑和调整

### 方式2：导入配置

1. 将你的 JSON 配置粘贴到右侧面板的文本框
2. 点击"加载"按钮
3. 开始编辑

### 方式3：AI 生成

1. 使用 `docs/agent-prompt.md` 配置 AI 智能体
2. 用自然语言描述你的业务系统，或者直接提供截图识别
3. AI 生成 JSON 配置
4. 导入本工具

## 📖 快速教程

### 1. 修改文字

- 点击任意卡片 → 弹出输入框 → 修改内容
- 点击层级标签（如"能力层"）→ 修改层级名称
- 点击能力组标题（如"项目管理"）→ 修改组名称

### 2. 调整布局

点击能力组容器（灰色框），右侧面板会显示布局配置：

- **每行最大卡片数**: 控制该层级一行显示多少个
- **宽度倍数**: 让这个容器占据 N 个卡片宽度（1-6倍）

### 3. 拖拽排序

- 拖拽层级边框可以调整层级顺序
- 拖拽卡片可以调整同层级内的顺序
- 拖拽灰色能力容器可以调整能力组的顺序

### 4. 导出

点击右下角按钮：

- **保存**: 导出 PNG 图片
- **复制**: 复制到剪贴板（直接粘贴到 PPT）
- **导出**: 导出 PPTX 文件
- **下载**: 保存 JSON 配置文件

## 🎯 应用场景

### 项目管理架构图

```
呈现层 → 能力层（项目管理/实施管理/成本管理...）→ 流程层 → 组件层 → 数据层
```

### 电商系统架构图

```
前端展示 → 业务能力（商品/订单/会员/支付）→ 核心流程 → 公共组件 → 数据层
```

### CRM 系统架构图

```
门户层 → 销售能力/服务能力/营销能力 → 业务流程 → 技术组件 → 数据层
```

### 任何功能架构

只要能抽象为 5 层结构的系统，都可以用本工具快速绘制！

## 🔧 配置说明

### 完整 JSON 结构

```json
{
  "title": "架构图标题",
  "config": {
    "font": {
      "family": "'Microsoft YaHei', 'PingFang SC', sans-serif",
      "size": 12,
      "weight": 700
    },
    "colors": {
      "primary": "#C00000",
      "background": "#FFFFFF",
      "border": "#E5E7EB"
    },
    "spacing": {
      "gridGap": 12,
      "layerGap": 20,
      "layerPadding": 18
    },
    "layout": {
      "capabilityColumns": 7,
      "processColumns": 5,
      "componentColumns": 3,
      "dataColumns": 5,
      "moduleColumns": 5
    }
  },
  "layers": [
    {
      "type": "module",
      "name": "呈现层",
      "items": ["功能A", "功能B"]
    }
  ]
}
```

### 层级类型说明

| 类型           | 说明               |
| ------------ | ---------------- |
| `module`     | 模块层 - 最上层的功能入口   |
| `capability` | 能力层 - 业务能力分组（核心） |
| `process`    | 流程层 - 业务流程节点     |
| `component`  | 组件层 - 技术组件       |
| `data`       | 数据层 - 数据来源/处理    |

### 能力层高级配置

```json
{
  "type": "capability",
  "name": "能力层",
  "items": [
    {
      "name": "核心能力",
      "columns": 3,           // 内部排列列数 1-5
      "widthMultiplier": 2,   // 容器宽度倍数 1-6
      "items": ["能力1", "能力2", "能力3"]
    }
  ]
}
```

## 🤖 AI 智能体

配合 `docs/agent-prompt.md`，可以让 AI 智能体：

1. 理解你的业务系统描述
2. 自动生成层级结构
3. 输出标准 JSON 配置
4. 直接导入本工具渲染

**提示**: 将 `docs/agent-prompt.md` 的内容作为 System Prompt 配置给 AI！

## 💡 使用技巧

1. **宽度倍数**: 如果某个能力组内容特别多，设置 `widthMultiplier: 2` 让它占2倍宽度
2. **列数调整**: 如果能力项数量是6个，设置 `columns: 3` 可以排成2行更美观
3. **颜色主题**: 点击右侧面板的颜色选择器，实时预览效果
4. **备份配置**: 编辑完成后记得"下载"JSON配置，方便后续修改

## 📋 示例

项目已包含 `examples/project-management-architecture.json` 示例，可以直接导入查看效果。

## 🔗 相关文档

- [SKILL 详细说明](skill/SKILL.md)
- [AI 智能体提示词](docs/agent-prompt.md)
- [配置模板](src/templates/architecture-config-template.json)

## 📝 更新日志

### v1.0.0

- 初始版本发布
- 5种层级类型支持
- 能力容器宽度倍数配置
- 画布拖拽调整大小
- 全元素点击编辑功能
- AI 智能体提示词配套

