---
name: icon-library-manager
description: "自动管理图标库 - 创建项目时安装图标库，编辑时添加缺失图标。触发时机：1) UI 需要图标时，2) AI 想用 emoji 时。"
arguments:
  - name: projectPath
    description: 前端项目目录的绝对路径
    required: true
  - name: productDescription
    description: 产品/应用的简要描述
    required: false
---

# 预设图标库

## 核心规则

1. **基于业务场景** - 根据项目类型选择合适的图标风格
2. **统一尺寸** - 所有图标保持相同的尺寸和线宽
3. **按需添加新库** - 当现有库缺少所需图标时，添加风格兼容的图标库

## 工作流程

### 创建新项目

1. 分析业务场景 → 选择合适的图标库
2. 检测前端框架 → 通过 npm/yarn/pnpm 安装
3. 创建集中化图标配置，保持一致的尺寸和线宽

### 添加缺失图标

1. 检查 `package.json` 中已安装的图标库
2. 已有图标库：在同库中查找相似图标
3. 未找到：在风格兼容的库中安装，使用最匹配的图标
4. 添加到 Icons 组件，避免使用 emoji 作为备选

### 图标库选择

| 场景 | 推荐 |
|------|------|
| Dashboard / Admin | Tabler Icons, Lucide |
| 电商 | Lucide, Heroicons |
| 社交 / 社区 | Heroicons |
| 金融 / 银行 | Lucide |
| 医疗健康 | Lucide, Phosphor |
| 移动应用 | Heroicons, Ionicons |
| 创意 / 设计 | Phosphor |
| 国内产品 | iconfont, Remix Icon |
| 通用 / 默认 | Lucide |

### 常用图标库

- **Lucide** - https://lucide.dev (1500+，现代风格，MIT)
- **Tabler Icons** - https://tabler-icons.io (5000+，MIT)
- **Heroicons** - https://heroicons.com (300+，Tailwind 官方，MIT)
- **Phosphor** - https://phosphoricons.com (700+，高端风格，MIT)
- **iconfont** - https://www.iconfont.cn (10000+，阿里巴巴)
- **Remix Icon** - https://remixicon.com (2000+，MIT)

## 图标配置

创建 `config/icon.config.ts`：

```ts
export const IconConfig = {
  defaultSize: 20,
  defaultStroke: 1.5,
  sizes: { navigation: 20, button: 16, card: 20, heading: 24 },
  strokes: { primary: 1.5, emphasis: 2 },
} as const;
```

在图标组件中使用：

```tsx
import { SomeIcon } from 'lucide-react';
import { IconConfig } from '@/config/icon.config';

export const Icons = {
  SomeIcon: (props) => <SomeIcon size={IconConfig.sizes.card} strokeWidth={IconConfig.defaultStroke} {...props} />,
};
```

## 注意事项

- 使用集中化配置保持尺寸一致
- 根据需要添加风格兼容的新图标库
- **避免在 UI 示例中使用 emoji，尽量使用图标库中的图标**
