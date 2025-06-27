# Modus Web Components - Test Environment

A comprehensive testing and documentation environment for **Modus Web Components** - Trimble's design system implementation. This repository serves as both a QA testing tool and interactive documentation platform.

## 🚀 Quick Start

1. Clone this repository
2. Open `start.html` in your browser to explore atomic components
3. Navigate to `highlevel.html` for complex UI patterns
4. Visit `icons.html` to browse the complete icon library

## 📁 Project Structure

```
test-modus/
├── README.md                          # This file
├── start.html                         # 🏠 Main entry - Atomic Components Explorer
├── highlevel.html                     # 🔧 High-Level Components Showcase
├── icons.html                         # 🎨 Icon Library Browser
├── setup_react.md                     # React integration guide
│
├── components/                        # 📚 Component Documentation (42 files)
│   ├── modus-wc-accordion.md
│   ├── modus-wc-alert.md
│   ├── modus-wc-autocomplete.md
│   ├── modus-wc-avatar.md
│   ├── modus-wc-badge.md
│   ├── modus-wc-breadcrumbs.md
│   ├── modus-wc-button.md
│   ├── modus-wc-card.md
│   ├── modus-wc-checkbox.md
│   ├── modus-wc-chip.md
│   ├── modus-wc-collapse.md
│   ├── modus-wc-date.md
│   ├── modus-wc-divider.md
│   ├── modus-wc-dropdown-menu.md
│   ├── modus-wc-icon.md
│   ├── modus-wc-input-feedback.md
│   ├── modus-wc-input-label.md
│   ├── modus-wc-loader.md
│   ├── modus-wc-menu-item.md
│   ├── modus-wc-menu.md
│   ├── modus-wc-modal.md
│   ├── modus-wc-navbar.md
│   ├── modus-wc-number-input.md
│   ├── modus-wc-pagination.md
│   ├── modus-wc-progress.md
│   ├── modus-wc-radio.md
│   ├── modus-wc-rating.md
│   ├── modus-wc-select.md
│   ├── modus-wc-side-navigation.md
│   ├── modus-wc-skeleton.md
│   ├── modus-wc-slider.md
│   ├── modus-wc-stepper.md
│   ├── modus-wc-switch.md
│   ├── modus-wc-table.md
│   ├── modus-wc-tabs.md
│   ├── modus-wc-text-input.md
│   ├── modus-wc-textarea.md
│   ├── modus-wc-theme-switcher.md
│   ├── modus-wc-time-input.md
│   ├── modus-wc-toast.md
│   ├── modus-wc-toolbar.md
│   ├── modus-wc-tooltip.md
│   └── modus-wc-typography.md
│
├── components_examples/               # 🧪 Interactive Component Examples
│   ├── accordion.html
│   ├── alert.html
│   ├── autocomplete.html
│   ├── avatar.html
│   ├── badge.html
│   ├── breadcrumbs.html
│   ├── button.html
│   ├── card.html
│   ├── checkbox.html
│   ├── chip.html
│   ├── collapse.html
│   ├── date.html
│   ├── divider.html
│   ├── dropdown-menu.html
│   ├── icon.html
│   ├── input-feedback.html
│   ├── input-label.html
│   ├── loader.html
│   ├── menu-item.html
│   ├── menu.html
│   ├── modal.html
│   ├── navbar.html
│   ├── number-input.html
│   ├── pagination.html
│   ├── progress.html
│   ├── radio.html
│   ├── rating.html
│   ├── select.html
│   ├── side-navigation.html
│   ├── skeleton.html
│   ├── slider.html
│   ├── stepper.html
│   ├── switch.html
│   ├── table.html
│   ├── tabs.html
│   ├── text-input.html
│   ├── textarea.html
│   ├── theme-switcher.html
│   ├── time-input.html
│   ├── toast.html
│   ├── toolbar.html
│   ├── tooltip.html
│   └── typography.html
│
├── docs/                              # 📖 Core Documentation
│   ├── setup.md                       # 🔧 Master setup guide & common pitfalls
│   ├── colors.md                      # 🎨 Modus color palette definitions
│   └── icons.md                       # 🔍 Complete icon library (800+ icons)
│
├── highlevel_examples/                # 🏗️ Complex UI Pattern Examples
│   ├── toolbars.html                  # Advanced toolbar compositions
│   └── modus-icons.js                 # Icon utilities and helpers
│
├── styles/                            # 💄 Styling
│   └── modus-qa-styles.css            # Shared QA environment styles
│
└── logos/                             # 🏢 Trimble Brand Assets
    ├── Connect-Horizontal-RGB.svg
    ├── Logo-Accubid-Anywhere-RGB-Full-Horizontal.svg
    ├── Logo-AllPriser-RGB-Full-Horizontal.svg
    ├── Logo-Construction-Analytics-RGB-Full-Horizontal.svg
    ├── Logo-Estimation-MEP-RGB-Full-Horizontal.svg
    ├── Logo-FabShop-RGB-Full-Horizontal.svg
    ├── Logo-FieldLink-RGB-Full-Horizontal.svg
    ├── Logo-LUCKINSlive-RGB-Full-Horizontal.svg
    ├── Logo-ProDesign-RGB-Full-Horizontal.svg
    ├── Logo-Stabicad-RGB-Full-Horizontal.svg
    ├── Logo-SysQue-RGB-Full-Horizontal.svg
    ├── Logo-Trade-Servicelive-RGB-Full-Horizontal.svg
    ├── Tekla-Logo-RGB-Horizontal.svg
    └── Trimble_logo.svg
```

## 🌐 Main Pages Overview

### 🏠 **start.html** - Atomic Components Explorer

The main entry point for testing individual Modus Web Components.

**Features:**

- Interactive sidebar with all 40+ components
- Live component examples loaded in iframes
- Real-time theme switching (4 themes available)
- Responsive design for all screen sizes

### 🔧 **highlevel.html** - High-Level Components Showcase

Demonstrates complex UI patterns built by combining atomic components.

**Features:**

- Advanced toolbar compositions
- Complex navigation patterns
- Real-world UI examples
- Integration patterns

### 🎨 **icons.html** - Icon Library Browser

Comprehensive browser for the complete Modus icon library.

**Features:**

- 800+ searchable icons
- Click-to-copy functionality
- Both basic and field-systems icon sets
- Real-time search filtering

## 🎯 Key Features

### ✅ **Complete Component Coverage**

- All 42 Modus Web Components documented
- Interactive examples for each component
- Multiple configuration options demonstrated

### 🎨 **Theme Testing**

- **4 Official Themes:** Modern Light/Dark, Classic Light/Dark
- Real-time theme switching
- Persistent theme preferences

### 🧪 **QA-Focused Environment**

- Built specifically for testing and validation
- Cross-browser compatibility testing
- Responsive design verification

### 🔍 **Icon Discovery**

- Comprehensive searchable icon library
- Copy icon names with one click
- Visual icon previews

### 📱 **Responsive Design**

- Mobile-first approach
- Tablet and desktop optimized
- Touch-friendly interactions

## 🛠️ Technical Stack

| Technology                   | Purpose                     | Source |
| ---------------------------- | --------------------------- | ------ |
| **Modus Web Components**     | Core component library      | CDN    |
| **Tailwind CSS**             | Utility-first CSS framework | CDN    |
| **Chart.js**                 | Data visualization          | CDN    |
| **Google Fonts (Open Sans)** | Typography                  | CDN    |
| **Modus Icons**              | Icon library                | CDN    |
| **Vanilla JavaScript**       | Interactivity               | Local  |

## 🚦 Getting Started

### Prerequisites

- Modern web browser (Chrome, Firefox, Safari, Edge)
- No build process required - everything runs in the browser

### Usage

1. **Explore Components:**

   ```bash
   # Open in browser
   open start.html
   ```

2. **View High-Level Patterns:**

   ```bash
   # Open in browser
   open highlevel.html
   ```

3. **Browse Icons:**
   ```bash
   # Open in browser
   open icons.html
   ```

### Development Workflow

1. **Component Testing:**

   - Use `start.html` to test individual components
   - Switch themes to verify visual consistency
   - Test responsive behavior

2. **Pattern Development:**

   - Use `highlevel.html` for complex UI patterns
   - Reference `highlevel_examples/` for implementation details

3. **Icon Integration:**
   - Use `icons.html` to find required icons
   - Copy icon names directly to your code

## 📚 Documentation

### Component Documentation

Each component in `/components/` includes:

- **Properties & Attributes** - Complete API reference
- **Events** - Available event handlers
- **CSS Custom Properties** - Theming options
- **Usage Examples** - Code snippets and best practices
- **Accessibility** - ARIA compliance and keyboard navigation

### Setup Guide

The `/docs/setup.md` file contains:

- **CDN Links** - All required external resources
- **Theme Configuration** - How to implement theming
- **Common Pitfalls** - Frequent mistakes and solutions
- **JavaScript Setup** - Component initialization

## 🎨 Theming

### Available Themes

- `modus-modern-light` - Clean, contemporary light theme
- `modus-modern-dark` - Modern dark theme for low-light environments
- `modus-classic-light` - Traditional Trimble light theme
- `modus-classic-dark` - Classic dark theme

### Theme Implementation

```html
<html data-theme="modus-modern-light"></html>
```

## 🔧 Customization

### Adding New Components

1. Create documentation in `/components/modus-wc-[name].md`
2. Add interactive example in `/components_examples/[name].html`
3. Update component list in `start.html`

### Creating High-Level Patterns

1. Add pattern file in `/highlevel_examples/[pattern].html`
2. Update pattern list in `highlevel.html`
3. Document usage patterns

## 📋 Use Cases

- **🧪 QA Testing** - Validate component behavior across themes
- **👀 Design Review** - Visual inspection of component implementations
- **📖 Developer Reference** - Quick access to component documentation
- **🔍 Icon Discovery** - Find and copy icon names for development
- **🏗️ Pattern Library** - Explore high-level UI compositions
- **📱 Responsive Testing** - Verify mobile and desktop layouts

## 🤝 Contributing

This is a testing environment for Modus Web Components. For component issues or feature requests, please refer to the official [Modus Web Components repository](https://github.com/trimble-oss/modus-web-components).

## 📄 License

This testing environment follows the same license as Modus Web Components. Please refer to the official repository for licensing information.

## 🔗 Related Links

- [Modus Web Components](https://github.com/trimble-oss/modus-web-components)
- [Modus Design System](https://modus.trimble.com/)
- [Trimble Developer Portal](https://developer.trimble.com/)

---

**Built with ❤️ for the Trimble development community**
