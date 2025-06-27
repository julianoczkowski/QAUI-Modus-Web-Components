# Next.js + Modus Design System Setup Guide

**FOR LLM AI UI BUILDERS**: This guide provides exact setup instructions for Next.js projects using Modus Design System. All versions, dependencies, and URLs are current and tested.

## 🎯 Core Features & Capabilities

- **Modus Integration**: Full Modus Web Components for React 19 with Next.js 15+ support
- **Theme System**: Complete light/dark mode switching with `modus-classic-light` and `modus-classic-dark` themes
- **Component Library**: 40+ production-ready UI components (buttons, cards, forms, navigation, etc.)
- **Icon System**: 1000+ Modus icons with consistent styling
- **TypeScript**: Full type safety and IntelliSense support
- **Responsive Design**: Mobile-first, accessible components
- **Performance**: Optimized for Next.js App Router and Server Components

## 🎨 Design System Variables (CRITICAL FOR LLMs)

### Color Palette

```css
/* Primary Colors - Use these for main actions and branding */
--modus-wc-color-primary: #0063a3;
--modus-wc-color-primary-hover: #004f82;
--modus-wc-color-primary-active: #003d66;

/* Secondary Colors - Use for accents and highlights */
--modus-wc-color-secondary: #6a1b9a;
--modus-wc-color-secondary-hover: #4a148c;

/* Background Colors - Essential for layouts */
--modus-wc-color-base-100: #ffffff; /* Light mode background */
--modus-wc-color-base-20: #252a2e; /* Dark mode background */
--modus-wc-color-base-50: #f1f1f6; /* Light gray background */

/* Status Colors */
--modus-wc-color-success: #1e8a44;
--modus-wc-color-warning: #e49325;
--modus-wc-color-danger: #da212c;
--modus-wc-color-info: #0063a3;
```

### Typography

```css
/* Font Family - Always use Open Sans */
font-family: "Open Sans", -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
```

## 📦 Step 1: Install Dependencies (EXACT VERSIONS)

```bash
# Create Next.js project (if starting fresh)
npx create-next-app@15.0.3 my-modus-app --typescript --tailwind --eslint --app

# Navigate to project
cd my-modus-app

# Install Modus Web Components for React 19
npm install @trimble-oss/moduswebcomponents-react@0.0.0-alpha.27-react19

# Install Modus Icons
npm install @trimble-oss/modus-icons@1.16.0

# Ensure React 19 compatibility
npm install react@19.1.0 react-dom@19.1.0
npm install --save-dev @types/react@19.1.8 @types/react-dom@19.1.6
```

## 🎨 Step 2: Setup Global Styles

Create or update `app/globals.css`:

```css
/* ESSENTIAL MODUS IMPORTS - DO NOT MODIFY THESE URLs */
@import url("@trimble-oss/moduswebcomponents/modus-wc-styles.css");
@import url("https://cdn.jsdelivr.net/npm/@trimble-oss/modus-icons@1/dist/modus-outlined/fonts/modus-icons.css");
@import url("https://fonts.googleapis.com/css2?family=Open+Sans:ital,wght@0,300..800;1,300..800&display=swap");

/* GLOBAL STYLES - CRITICAL FOR PROPER RENDERING */
* {
  box-sizing: border-box;
  padding: 0;
  margin: 0;
}

html,
body {
  max-width: 100vw;
  overflow-x: hidden;
  font-family: "Open Sans", -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
  background-color: var(--modus-wc-color-base-100);
  color: var(--modus-wc-color-text-primary);
  line-height: 1.6;
}

/* THEME SWITCHING SUPPORT */
[data-theme="modus-classic-dark"] body {
  background-color: var(--modus-wc-color-base-20);
  color: #ffffff;
}

/* RESPONSIVE CONTAINER - Use with Tailwind classes */
.modus-container {
  max-width: 1200px;
  margin: 0 auto;
  padding: var(--modus-space-md);
}

/* MODUS + TAILWIND INTEGRATION */
/* Use Tailwind classes for layout and sizing */
/* Use Modus CSS variables for colors and component-specific styling */
```

## 🏗️ Step 3: Setup Root Layout

Update `app/layout.tsx`:

```tsx
import type { Metadata } from "next";
import "./globals.css";

export const metadata: Metadata = {
  title: "Modus Next.js App",
  description: "Built with Modus Design System",
};

export default function RootLayout({
  children,
}: {
  children: React.ReactNode;
}) {
  return (
    <html lang="en" data-theme="modus-classic-light">
      <head>
        <meta name="viewport" content="width=device-width, initial-scale=1" />
      </head>
      <body>{children}</body>
    </html>
  );
}
```

## 🧩 Step 4: Create Main Page Component

Replace `app/page.tsx`:

```tsx
"use client";

import React from "react";
import {
  ModusWcThemeProvider,
  ModusWcCard,
  ModusWcButton,
  ModusWcThemeSwitcher,
  ModusWcAlert,
  ModusWcTextInput,
  ModusWcNavbar,
} from "@trimble-oss/moduswebcomponents-react";

export default function HomePage() {
  const [inputValue, setInputValue] = React.useState("");

  const handleInputChange = (e: CustomEvent) => {
    setInputValue(e.detail.target.value);
  };

  return (
    <ModusWcThemeProvider>
      {/* Navigation */}
      <ModusWcNavbar>
        <div slot="main">
          <span style={{ fontWeight: "bold", fontSize: "1.25rem" }}>
            Modus Next.js App
          </span>
        </div>
        <div slot="profile">
          <ModusWcThemeSwitcher aria-label="Toggle theme" />
        </div>
      </ModusWcNavbar>

      {/* Main Content */}
      <main className="modus-container">
        <div className="flex flex-col items-center gap-8">
          {/* Welcome Card */}
          <ModusWcCard style={{ width: "100%", maxWidth: "600px" }}>
            <div className="p-8 text-center">
              <h1
                style={{
                  fontSize: "var(--modus-font-size-3xl)",
                  marginBottom: "var(--modus-space-md)",
                  color: "var(--modus-wc-color-primary)",
                }}
              >
                Welcome to Modus + Next.js
              </h1>
              <p
                style={{
                  fontSize: "var(--modus-font-size-lg)",
                  marginBottom: "var(--modus-space-lg)",
                  color: "var(--modus-wc-color-text-secondary)",
                }}
              >
                Your app is ready with Modus Design System components!
              </p>

              <div className="flex gap-4 justify-center">
                <ModusWcButton color="primary">Get Started</ModusWcButton>
                <ModusWcButton variant="outline">Learn More</ModusWcButton>
              </div>
            </div>
          </ModusWcCard>

          {/* Interactive Example */}
          <ModusWcCard style={{ width: "100%", maxWidth: "600px" }}>
            <div className="p-8">
              <h2 className="mb-4">Try Interactive Components</h2>

              <ModusWcTextInput
                label="Enter your name"
                placeholder="Type something..."
                value={inputValue}
                onInputChange={handleInputChange}
                style={{ marginBottom: "var(--modus-space-md)" }}
              />

              {inputValue && (
                <ModusWcAlert variant="success">
                  Hello, {inputValue}! 👋
                </ModusWcAlert>
              )}
            </div>
          </ModusWcCard>

          {/* Icon Examples */}
          <ModusWcCard style={{ width: "100%", maxWidth: "600px" }}>
            <div className="p-8">
              <h2 className="mb-4">Modus Icons</h2>
              <div className="flex gap-4 items-center">
                <i
                  className="modus-icons"
                  style={{
                    fontSize: "2rem",
                    color: "var(--modus-wc-color-primary)",
                  }}
                >
                  home
                </i>
                <i
                  className="modus-icons"
                  style={{
                    fontSize: "2rem",
                    color: "var(--modus-wc-color-secondary)",
                  }}
                >
                  settings
                </i>
                <i
                  className="modus-icons"
                  style={{
                    fontSize: "2rem",
                    color: "var(--modus-wc-color-success)",
                  }}
                >
                  check_circle
                </i>
                <i
                  className="modus-icons"
                  style={{
                    fontSize: "2rem",
                    color: "var(--modus-wc-color-info)",
                  }}
                >
                  info
                </i>
              </div>
            </div>
          </ModusWcCard>
        </div>
      </main>
    </ModusWcThemeProvider>
  );
}
```

## 📋 Step 5: Package.json Configuration

Your `package.json` should include these exact dependencies:

```json
{
  "name": "my-modus-app",
  "version": "0.1.0",
  "private": true,
  "scripts": {
    "dev": "next dev",
    "build": "next build",
    "start": "next start",
    "lint": "next lint"
  },
  "dependencies": {
    "@trimble-oss/modus-icons": "^1.16.0",
    "@trimble-oss/moduswebcomponents-react": "^0.0.0-alpha.27-react19",
    "next": "15.0.3",
    "react": "^19.1.0",
    "react-dom": "^19.1.0"
  },
  "devDependencies": {
    "@types/node": "^20",
    "@types/react": "^19.1.8",
    "@types/react-dom": "^19.1.6",
    "eslint": "^8",
    "eslint-config-next": "15.0.3",
    "typescript": "^5"
  }
}
```

## 🚀 Quick Start Commands

```bash
# Start development server
npm run dev

# Build for production
npm run build

# Start production server
npm start
```

## 🧩 Essential Components for LLMs

### Buttons

```tsx
<ModusWcButton color="primary">Primary Action</ModusWcButton>
<ModusWcButton color="secondary">Secondary Action</ModusWcButton>
<ModusWcButton variant="outline">Outline Button</ModusWcButton>
<ModusWcButton variant="text">Text Button</ModusWcButton>
<ModusWcButton disabled>Disabled Button</ModusWcButton>
```

### Form Inputs

```tsx
<ModusWcTextInput
  label="Email"
  type="email"
  placeholder="Enter email"
  required
  onInputChange={(e) => console.log(e.detail.target.value)}
/>

<ModusWcSelect
  label="Country"
  options={[
    { value: 'us', text: 'United States' },
    { value: 'ca', text: 'Canada' },
    { value: 'uk', text: 'United Kingdom' }
  ]}
  onSelectionChange={(e) => console.log(e.detail.value)}
/>

<ModusWcCheckbox
  label="I agree to terms"
  onCheckboxClick={(e) => console.log(e.detail.checked)}
/>
```

### Layout Components

```tsx
<ModusWcCard>
  <div className="p-8">
    <h3>Card Title</h3>
    <p>Card content goes here</p>
  </div>
</ModusWcCard>

<ModusWcAlert variant="success">
  Success message with icon
</ModusWcAlert>

<ModusWcAlert variant="warning">
  Warning message
</ModusWcAlert>

<ModusWcAlert variant="danger">
  Error message
</ModusWcAlert>
```

### Navigation

```tsx
<ModusWcNavbar>
  <div slot="main">
    <span>App Name</span>
  </div>
  <div slot="profile">
    <ModusWcThemeSwitcher />
  </div>
</ModusWcNavbar>

<ModusWcBreadcrumbs>
  <ModusWcBreadcrumbItem href="/">Home</ModusWcBreadcrumbItem>
  <ModusWcBreadcrumbItem href="/products">Products</ModusWcBreadcrumbItem>
  <ModusWcBreadcrumbItem>Current Page</ModusWcBreadcrumbItem>
</ModusWcBreadcrumbs>
```

### Icons Usage

```tsx
{/* Use any icon from Modus Icons library */}
<i className="modus-icons">home</i>
<i className="modus-icons">settings</i>
<i className="modus-icons">person</i>
<i className="modus-icons">search</i>
<i className="modus-icons">menu</i>
<i className="modus-icons">close</i>
<i className="modus-icons">check_circle</i>
<i className="modus-icons">info</i>
<i className="modus-icons">warning</i>
<i className="modus-icons">error</i>
```

## 🎯 LLM Best Practices

### 1. Always Use Theme Provider

Wrap your app content in `<ModusWcThemeProvider>` for proper theming.

### 2. Layout & Spacing - Use Tailwind Classes

- **Layout**: `flex`, `flex-col`, `grid`, `items-center`, `justify-center`
- **Spacing**: `p-4`, `p-8`, `m-4`, `mb-4`, `gap-4`, `gap-8`
- **Sizing**: `w-full`, `max-w-md`, `h-screen`, `text-lg`, `text-2xl`

### 3. Colors - Use Modus CSS Variables

- **Primary actions**: `style={{ color: 'var(--modus-wc-color-primary)' }}`
- **Secondary actions**: `style={{ color: 'var(--modus-wc-color-secondary)' }}`
- **Success states**: `style={{ color: 'var(--modus-wc-color-success)' }}`
- **Warnings**: `style={{ color: 'var(--modus-wc-color-warning)' }}`
- **Errors**: `style={{ color: 'var(--modus-wc-color-danger)' }}`

### 4. Typography

- **Font Family**: Always use Open Sans (already set in global CSS)
- **Font Sizes**: Use Tailwind classes (`text-sm`, `text-lg`, `text-2xl`) or Modus variables for custom sizes

### 5. Best Practice Combination

```tsx
// ✅ Good: Tailwind for layout, Modus colors for theming
<div className="flex items-center gap-4 p-8">
  <ModusWcButton color="primary" className="text-lg">
    Action
  </ModusWcButton>
  <i
    className="modus-icons text-2xl"
    style={{ color: "var(--modus-wc-color-primary)" }}
  >
    home
  </i>
</div>
```

## 📚 Resources

- **Modus Web Components Docs**: https://trimble-oss.github.io/modus-wc-2.0/main/
- **Modus Icons Library**: http://modus-icons.trimble.com/
- **Design System Guidelines**: https://modus.trimble.com/
- **React Integration Guide**: https://trimble-oss.github.io/modus-wc-2.0/main/frameworks/react/

## ✅ Verification Checklist

After setup, verify these work:

- [ ] Theme switching (light/dark)
- [ ] Icons display correctly
- [ ] Components render properly
- [ ] TypeScript IntelliSense works
- [ ] Responsive design functions
- [ ] Form inputs handle events
- [ ] Color variables apply correctly
