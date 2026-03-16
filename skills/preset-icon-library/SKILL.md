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

## Icon Library Options

Based on the product type, select the most suitable icon library:

| Product Type | Recommended Library | Reason |
|--------------|---------------------|--------|
| Dashboard / Admin / SaaS | Lucide | Clean, modern, professional look |
| E-commerce / Shopping | Lucide or Heroicons | Clear, recognizable commerce icons |
| Social / Community | Heroicons or Tabler | Friendly, approachable design |
| Finance / Banking | Lucide | Professional, trustworthy appearance |
| Healthcare / Medical | Lucide or Phosphor | Clean, medical-standard icons |
| Education / Learning | Lucide or Remix | Modern, accessible icons |
| General / Multi-purpose | Lucide | Most popular, versatile choice |
| Mobile App | Heroicons or Ionicons | Touch-friendly, clear at small sizes |
| Dashboard with data viz | Lucide | Great for charts and data UI |
| Creative / Design | Phosphor or Feather | Unique, artistic style |

### Popular Icon Libraries Reference

- **Lucide** - https://lucide.dev (Most popular, 1500+ icons, MIT license)
- **Heroicons** - https://heroicons.com (By Tailwind CSS team, MIT license)
- **Tabler Icons** - https://tabler-icons.io (1500+ icons, MIT license)
- **Phosphor Icons** - https://phosphoricons.com (700+ icons, MIT license)
- **Feather Icons** - https://feathericons.com (280+ icons, MIT license)
- **Ionicons** - https://ionic.io/ionicons (1300+ icons, MIT license)
- **Remix Icon** - https://remixicon.com (2000+ icons, Apache 2.0)

## Workflow

1. **Analyze the product description** (if provided) to determine the best icon library

2. **Detect the frontend framework** to determine the correct installation method:

   - **React** - Check for `package.json` with React dependencies
   - **Vue** - Check for `package.json` with Vue dependencies or `.vue` files
   - **Next.js** - Check for `package.json` with Next.js
   - **Nuxt** - Check for `nuxt.config.ts` or `.nuxt` directory
   - **Svelte** - Check for `package.json` with Svelte or `.svelte` files
   - **Astro** - Check for `astro.config.mjs`
   - **Plain HTML/JS** - Use CDN or npm package

3. **Install the icon library** using the appropriate package manager:

   ```bash
   # For React/Vue/Next.js projects
   npm install lucide-react   # Lucide for React
   npm install lucide-vue-next # Lucide for Vue
   npm install @heroicons/react  # Heroicons for React
   npm install @heroicons/vue    # Heroicons for Vue
   npm install @tabler/icons    # Tabler Icons
   npm install @phosphor-icons/react  # Phosphor for React
   
   # Or use the generic package
   npm install lucide
   ```

4. **Configure the icon library** if needed (some frameworks require setup)

5. **Provide usage examples** to the user

## Detection and Installation Examples

### React Project

```bash
# Check if React project
if grep -q '"react"' package.json; then
    # Install Lucide (recommended default)
    npm install lucide-react
    
    # Or Heroicons
    npm install @heroicons/react
fi
```

### Vue Project

```bash
# Check if Vue project  
if grep -q '"vue"' package.json; then
    npm install lucide-vue-next
    # or
    npm install @heroicons/vue
fi
```

### Next.js Project

```bash
# Next.js with Lucide
npm install lucide-react

# Create a icon component for convenience
cat > components/Icons.tsx << 'EOF'
import { 
  Home, User, Settings, Search, Bell, 
  Menu, X, ChevronDown, ChevronRight,
  Plus, Edit, Trash, Save, Check, X as XIcon,
  Loader2, AlertCircle, Info
} from 'lucide-react';

export const Icons = {
  Home, User, Settings, Search, Bell,
  Menu, X, ChevronDown, ChevronRight,
  Plus, Edit, Trash, Save, Check, XIcon,
  Loader2, AlertCircle, Info
};
EOF
```

### Plain HTML/JS Project

For non-framework projects, use CDN:

```html
<!-- Lucide CDN -->
<script src="https://unpkg.com/lucide@latest/dist/umd/lucide.js"></script>

<!-- Or Heroicons -->
<script src="https://unpkg.com/@heroicons/react/24/outline/index.js"></script>
```

## Output

After installing, provide the user with:

1. **Which icon library was selected** and why
2. **Installation commands used**
3. **Usage examples** for the specific framework
4. **Next steps** if additional configuration is needed

## Notes

- If no product description is provided, default to **Lucide** (most popular, versatile)
- Consider the project's design system - if using Tailwind CSS, Heroicons or Lucide are natural fits
- For projects requiring many icons (e.g., admin dashboards), Lucide or Tabler are best
- For creative/marketing sites, Phosphor offers a unique style
- Always use the latest version with `latest` tag or check compatible versions
