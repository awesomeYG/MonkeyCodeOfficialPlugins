---
name: preset-icon-library
description: When creating a new frontend project, analyze the product description and automatically install and configure a suitable icon library to avoid using emojis in the UI.
arguments:
  - name: projectPath
    description: Absolute path to the frontend project directory
    required: true
  - name: productDescription
    description: Brief description of the product/app type to help select the appropriate icon library
    required: false
---

# Preset Icon Library

When creating a new frontend project, automatically select and configure an appropriate icon library based on the product description.

## Core Rules (MUST FOLLOW)

1. **Single Icon Library Per Project** - Only ONE icon library allowed in a project. Never mix multiple icon libraries.

2. **Business Scenario Based Selection** - Icon style must match the business scenario:
   - Dashboard/Admin: Professional, clean, data-oriented
   - E-commerce: Clear, commerce-focused, trustworthy
   - Social/Community: Friendly, approachable, warm
   - Finance/Banking: Professional, serious, trustworthy
   - Healthcare: Clean, medical-standard, empathetic
   - Education: Modern, accessible, encouraging
   - Creative/Design: Unique, artistic, distinctive

3. **Consistent Icon Properties** - All icons must maintain:
   - Same size (e.g., 20px or 24px standard)
   - Same stroke width/line weight (e.g., 1.5px or 2px)
   - Same style (outline vs solid vs duotone)

## Icon Library Options

Based on the business scenario, select the most suitable icon library:

| Business Scenario | Recommended Library | Style | Size | Stroke |
|-------------------|---------------------|-------|------|--------|
| Dashboard / Admin / SaaS | Lucide | Outline | 20px | 1.5px |
| E-commerce / Shopping | Lucide | Outline/Solid | 20px | 1.5px |
| Social / Community | Heroicons | Outline | 20px | 1.5px |
| Finance / Banking | Lucide | Outline | 20px | 2px |
| Healthcare / Medical | Lucide | Outline | 20px | 1.5px |
| Education / Learning | Lucide | Outline | 20px | 1.5px |
| General / Multi-purpose | Lucide | Outline | 20px | 1.5px |
| Mobile App | Heroicons | Solid/Outline | 24px | 1.5px |
| Dashboard with data viz | Lucide | Outline | 16px/20px | 1.5px |
| Creative / Design | Phosphor | Duotone | 24px | 1.5px |

### Popular Icon Libraries Reference

- **Lucide** - https://lucide.dev (1500+ icons, MIT license)
- **Heroicons** - https://heroicons.com (By Tailwind CSS team, MIT license)
- **Tabler Icons** - https://tabler-icons.io (1500+ icons, MIT license)
- **Phosphor Icons** - https://phosphoricons.com (700+ icons, MIT license)

## Workflow

1. **Analyze the business scenario** from product description to determine the best icon library and style

2. **Check existing icon usage** - If the project already has an icon library installed, continue using it instead of adding a new one

3. **Detect the frontend framework** to determine the correct installation method

4. **Install the icon library** using the appropriate package manager

5. **Create icon configuration** with consistent size and stroke settings

6. **Provide usage guidelines** ensuring all icons follow the same standards

## Icon Configuration Standards

### Size Standards

| Usage Context | Recommended Size |
|--------------|------------------|
| Navigation menu | 20px |
| Buttons | 16px or 20px |
| Form inputs | 16px |
| Data tables | 16px |
| Cards/Widgets | 20px |
| Headers/Page titles | 24px |

### Stroke Width Standards

| Style | Recommended Stroke |
|-------|-------------------|
| Standard outline | 1.5px |
| Heavy/Emphasis | 2px |
| Subtle/Secondary | 1px |

### Implementation Example

For a React project with Lucide:

```bash
npm install lucide-react
```

Create a centralized icon configuration:

```tsx
// components/Icons.tsx
import { 
  Home, User, Settings, Search, Bell, 
  Menu, X, ChevronDown, ChevronRight,
  Plus, Edit, Trash, Save, Check,
  Loader2, AlertCircle, Info, Eye,
  Dashboard, Package, Users, CreditCard,
  BarChart3, PieChart, TrendingUp, Calendar
} from 'lucide-react';

// All icons configured with consistent size and stroke
export const Icons = {
  // Navigation
  Home: (props) => <Home size={20} strokeWidth={1.5} {...props} />,
  Dashboard: (props) => <Dashboard size={20} strokeWidth={1.5} {...props} />,
  User: (props) => <User size={20} strokeWidth={1.5} {...props} />,
  Settings: (props) => <Settings size={20} strokeWidth={1.5} {...props} />,
  Menu: (props) => <Menu size={20} strokeWidth={1.5} {...props} />,
  
  // Actions
  Search: (props) => <Search size={20} strokeWidth={1.5} {...props} />,
  Bell: (props) => <Bell size={20} strokeWidth={1.5} {...props} />,
  Plus: (props) => <Plus size={20} strokeWidth={1.5} {...props} />,
  Edit: (props) => <Edit size={16} strokeWidth={1.5} {...props} />,
  Trash: (props) => <Trash size={16} strokeWidth={1.5} {...props} />,
  Save: (props) => <Save size={16} strokeWidth={1.5} {...props} />,
  Check: (props) => <Check size={16} strokeWidth={1.5} {...props} />,
  Eye: (props) => <Eye size={16} strokeWidth={1.5} {...props} />,
  
  // Navigation arrows
  ChevronDown: (props) => <ChevronDown size={16} strokeWidth={1.5} {...props} />,
  ChevronRight: (props) => <ChevronRight size={16} strokeWidth={1.5} {...props} />,
  
  // Status
  AlertCircle: (props) => <AlertCircle size={20} strokeWidth={1.5} {...props} />,
  Info: (props) => <Info size={20} strokeWidth={1.5} {...props} />,
  Loader2: (props) => <Loader2 size={20} strokeWidth={1.5} {...props} />,
  
  // Business-specific
  Package: (props) => <Package size={20} strokeWidth={1.5} {...props} />,
  Users: (props) => <Users size={20} strokeWidth={1.5} {...props} />,
  CreditCard: (props) => <CreditCard size={20} strokeWidth={1.5} {...props} />,
  BarChart3: (props) => <BarChart3 size={20} strokeWidth={1.5} {...props} />,
  PieChart: (props) => <PieChart size={20} strokeWidth={1.5} {...props} />,
  TrendingUp: (props) => <TrendingUp size={20} strokeWidth={1.5} {...props} />,
  Calendar: (props) => <Calendar size={20} strokeWidth={1.5} {...props} />,
};
```

## Output

After installing, provide the user with:

1. **Selected icon library** and business scenario rationale
2. **Standard icon configuration** (size, stroke width)
3. **Centralized icon component** for consistent usage
4. **Usage guidelines** - enforce single library and consistent styling

## Notes

- NEVER allow mixing multiple icon libraries in one project
- ALWAYS enforce consistent icon size and stroke width across all components
- If existing project has an icon library, continue using it rather than introducing new ones
- Default to Lucide for most business scenarios unless specifically justified
- Document the chosen icon library and standards in project README
