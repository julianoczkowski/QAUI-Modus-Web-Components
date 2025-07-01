# Next.js + Modus Design System Setup Guide (Generic)

**FOR LLM AI UI BUILDERS**: This guide provides exact setup instructions for Next.js projects using Modus Design System colors, typography, and styling without web components. All versions, dependencies, and URLs are current and tested.

## 🎯 Core Features & Capabilities

- **Modus Design Integration**: Complete Modus color palette, typography, and design tokens
- **Theme System**: Complete light/dark mode switching with CSS custom properties
- **Icon System**: 1000+ Modus icons with consistent styling
- **TypeScript**: Full type safety and IntelliSense support
- **Responsive Design**: Mobile-first, accessible design patterns
- **Performance**: Optimized for Next.js App Router and Server Components

## 🎨 Design System Variables (CRITICAL FOR LLMs)

### Color Palette

```css
/* Primary Colors - Use these for main actions and branding */
--modus-color-primary: #0063a3;
--modus-color-primary-hover: #004f82;
--modus-color-primary-active: #003d66;

/* Secondary Colors - Use for accents and highlights */
--modus-color-secondary: #6a1b9a;
--modus-color-secondary-hover: #4a148c;

/* Background Colors - Essential for layouts */
--modus-color-base-100: #ffffff; /* Light mode background */
--modus-color-base-50: #f1f1f6; /* Light gray background */
--modus-color-base-20: #252a2e; /* Dark mode background */

/* Text Colors */
--modus-color-text-primary: #171c1e;
--modus-color-text-secondary: #6a6e79;
--modus-color-text-light: #ffffff;

/* Status Colors */
--modus-color-success: #1e8a44;
--modus-color-warning: #e49325;
--modus-color-danger: #da212c;
--modus-color-info: #0063a3;

/* Grays */
--modus-color-gray-light: #f1f1f6;
--modus-color-gray-0: #e0e1e9;
--modus-color-gray-1: #cbcdd6;
--modus-color-gray-2: #b7b9c3;
--modus-color-gray-3: #a3a6b1;
--modus-color-gray-4: #90939f;
--modus-color-gray-5: #7d808d;
--modus-color-gray-6: #6a6e79;
--modus-color-gray-7: #585c65;
--modus-color-gray-8: #464b52;
--modus-color-gray-9: #353a40;
--modus-color-gray-10: #171c1e;
```

### Typography

```css
/* Font Family - Always use Open Sans */
font-family: "Open Sans", -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;

/* Font Sizes */
--modus-font-size-xs: 0.75rem;
--modus-font-size-sm: 0.875rem;
--modus-font-size-base: 1rem;
--modus-font-size-lg: 1.125rem;
--modus-font-size-xl: 1.25rem;
--modus-font-size-2xl: 1.5rem;
--modus-font-size-3xl: 1.875rem;
--modus-font-size-4xl: 2.25rem;

/* Spacing */
--modus-space-xs: 0.25rem;
--modus-space-sm: 0.5rem;
--modus-space-md: 1rem;
--modus-space-lg: 1.5rem;
--modus-space-xl: 2rem;
--modus-space-2xl: 3rem;
```

## 📦 Step 1: Install Dependencies (EXACT VERSIONS)

```bash
# Create Next.js project (if starting fresh)
npx create-next-app@15.0.3 my-modus-app --typescript --tailwind --eslint --app

# Navigate to project
cd my-modus-app

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
@import url("https://fonts.googleapis.com/css2?family=Open+Sans:ital,wght@0,300..800;1,300..800&display=swap");
@import url("https://cdn.jsdelivr.net/npm/@trimble-oss/modus-icons@1/dist/modus-outlined/fonts/modus-icons.css");

/* MODUS DESIGN TOKENS */
:root {
  /* Base Color Palette */
  --modus-color-white: #fff;
  --modus-color-gray-light: #f1f1f6;
  --modus-color-gray-0: #e0e1e9;
  --modus-color-gray-1: #cbcdd6;
  --modus-color-gray-2: #b7b9c3;
  --modus-color-gray-3: #a3a6b1;
  --modus-color-gray-4: #90939f;
  --modus-color-gray-5: #7d808d;
  --modus-color-gray-6: #6a6e79;
  --modus-color-gray-7: #585c65;
  --modus-color-gray-8: #464b52;
  --modus-color-gray-9: #353a40;
  --modus-color-gray-10: #171c1e;
  --modus-color-trimble-gray: #252a2e;
  --modus-color-black: #000;

  /* Blues */
  --modus-color-blue-pale: #dcedf9;
  --modus-color-highlight-blue: #019aeb;
  --modus-color-blue-light: #217cbb;
  --modus-color-trimble-blue: #0063a3;
  --modus-color-blue-dark: #0e416c;

  /* Status Colors */
  --modus-color-green: #1e8a44;
  --modus-color-yellow: #fbad26;
  --modus-color-red: #da212c;

  /* Light Theme (Default) */
  --modus-color-base-page: var(--modus-color-white);
  --modus-color-base-100: var(--modus-color-gray-light);
  --modus-color-base-200: var(--modus-color-gray-1);
  --modus-color-base-300: var(--modus-color-gray-2);
  --modus-color-base-content: var(--modus-color-gray-10);
  --modus-color-primary: var(--modus-color-trimble-blue);
  --modus-color-primary-content: var(--modus-color-white);
  --modus-color-info: var(--modus-color-trimble-blue);
  --modus-color-success: var(--modus-color-green);
  --modus-color-error: var(--modus-color-red);
  --modus-color-warning: var(--modus-color-yellow);

  /* Typography */
  --modus-font-size-xs: 0.75rem;
  --modus-font-size-sm: 0.875rem;
  --modus-font-size-base: 1rem;
  --modus-font-size-lg: 1.125rem;
  --modus-font-size-xl: 1.25rem;
  --modus-font-size-2xl: 1.5rem;
  --modus-font-size-3xl: 1.875rem;
  --modus-font-size-4xl: 2.25rem;

  /* Spacing */
  --modus-space-xs: 0.25rem;
  --modus-space-sm: 0.5rem;
  --modus-space-md: 1rem;
  --modus-space-lg: 1.5rem;
  --modus-space-xl: 2rem;
  --modus-space-2xl: 3rem;
}

/* Dark Theme */
[data-theme="modus-classic-dark"] {
  --modus-color-base-page: var(--modus-color-black);
  --modus-color-base-100: var(--modus-color-trimble-gray);
  --modus-color-base-200: var(--modus-color-gray-8);
  --modus-color-base-300: var(--modus-color-gray-9);
  --modus-color-base-content: var(--modus-color-gray-1);
  --modus-color-primary: var(--modus-color-highlight-blue);
  --modus-color-primary-content: var(--modus-color-black);
}

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
  background-color: var(--modus-color-base-page);
  color: var(--modus-color-base-content);
  line-height: 1.6;
}

/* RESPONSIVE CONTAINER - Use with Tailwind classes */
.modus-container {
  max-width: 1200px;
  margin: 0 auto;
  padding: var(--modus-space-md);
}

/* UTILITY CLASSES */
.modus-text-primary {
  color: var(--modus-color-primary);
}

.modus-text-secondary {
  color: var(--modus-color-gray-6);
}

.modus-bg-primary {
  background-color: var(--modus-color-primary);
  color: var(--modus-color-primary-content);
}

.modus-bg-card {
  background-color: var(--modus-color-base-100);
  border: 1px solid var(--modus-color-base-200);
  border-radius: 8px;
}

/* BUTTON STYLES */
.modus-btn {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  padding: 0.75rem 1.5rem;
  font-family: inherit;
  font-size: var(--modus-font-size-base);
  font-weight: 600;
  text-decoration: none;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  transition: all 0.2s ease;
}

.modus-btn-primary {
  background-color: var(--modus-color-primary);
  color: var(--modus-color-primary-content);
}

.modus-btn-primary:hover {
  background-color: var(--modus-color-blue-dark);
}

.modus-btn-secondary {
  background-color: transparent;
  color: var(--modus-color-primary);
  border: 1px solid var(--modus-color-primary);
}

.modus-btn-secondary:hover {
  background-color: var(--modus-color-primary);
  color: var(--modus-color-primary-content);
}

/* CARD STYLES */
.modus-card {
  background-color: var(--modus-color-base-100);
  border: 1px solid var(--modus-color-base-200);
  border-radius: 8px;
  padding: var(--modus-space-lg);
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

/* ALERT STYLES */
.modus-alert {
  padding: var(--modus-space-md);
  border-radius: 4px;
  margin-bottom: var(--modus-space-md);
}

.modus-alert-success {
  background-color: #e0eccf;
  color: var(--modus-color-green);
  border-left: 4px solid var(--modus-color-success);
}

.modus-alert-warning {
  background-color: #fff5e4;
  color: var(--modus-color-yellow);
  border-left: 4px solid var(--modus-color-warning);
}

.modus-alert-error {
  background-color: #fbd4d7;
  color: var(--modus-color-red);
  border-left: 4px solid var(--modus-color-error);
}

.modus-alert-info {
  background-color: var(--modus-color-blue-pale);
  color: var(--modus-color-primary);
  border-left: 4px solid var(--modus-color-info);
}

/* FORM STYLES */
.modus-input {
  width: 100%;
  padding: 0.75rem;
  font-family: inherit;
  font-size: var(--modus-font-size-base);
  border: 1px solid var(--modus-color-base-300);
  border-radius: 4px;
  background-color: var(--modus-color-base-page);
  color: var(--modus-color-base-content);
}

.modus-input:focus {
  outline: none;
  border-color: var(--modus-color-primary);
  box-shadow: 0 0 0 2px rgba(0, 99, 163, 0.2);
}

.modus-label {
  display: block;
  margin-bottom: var(--modus-space-sm);
  font-weight: 600;
  color: var(--modus-color-base-content);
}
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

export default function HomePage() {
  const [inputValue, setInputValue] = React.useState("");
  const [theme, setTheme] = React.useState("modus-classic-light");

  const toggleTheme = () => {
    const newTheme =
      theme === "modus-classic-light"
        ? "modus-classic-dark"
        : "modus-classic-light";
    setTheme(newTheme);
    document.documentElement.setAttribute("data-theme", newTheme);
  };

  return (
    <>
      {/* Navigation */}
      <nav className="modus-bg-card border-b">
        <div className="modus-container">
          <div className="flex justify-between items-center py-4">
            <h1 className="text-2xl font-bold modus-text-primary">
              Modus Next.js App
            </h1>
            <button
              onClick={toggleTheme}
              className="modus-btn modus-btn-secondary"
              aria-label="Toggle theme"
            >
              <i className="modus-icons mr-2">
                {theme === "modus-classic-light" ? "dark_mode" : "light_mode"}
              </i>
              {theme === "modus-classic-light" ? "Dark" : "Light"}
            </button>
          </div>
        </div>
      </nav>

      {/* Main Content */}
      <main className="modus-container">
        <div className="flex flex-col items-center gap-8 py-8">
          {/* Welcome Card */}
          <div className="modus-card w-full max-w-2xl text-center">
            <h1 className="text-4xl font-bold mb-4 modus-text-primary">
              Welcome to Modus + Next.js
            </h1>
            <p className="text-lg mb-6 modus-text-secondary">
              Your app is ready with Modus Design System styling!
            </p>

            <div className="flex gap-4 justify-center">
              <button className="modus-btn modus-btn-primary">
                Get Started
              </button>
              <button className="modus-btn modus-btn-secondary">
                Learn More
              </button>
            </div>
          </div>

          {/* Interactive Example */}
          <div className="modus-card w-full max-w-2xl">
            <h2 className="text-2xl font-bold mb-4">
              Try Interactive Components
            </h2>

            <div className="mb-4">
              <label className="modus-label" htmlFor="name-input">
                Enter your name
              </label>
              <input
                id="name-input"
                type="text"
                className="modus-input"
                placeholder="Type something..."
                value={inputValue}
                onChange={(e) => setInputValue(e.target.value)}
              />
            </div>

            {inputValue && (
              <div className="modus-alert modus-alert-success">
                <strong>Hello, {inputValue}! 👋</strong>
              </div>
            )}
          </div>

          {/* Icon Examples */}
          <div className="modus-card w-full max-w-2xl">
            <h2 className="text-2xl font-bold mb-4">Modus Icons</h2>
            <div className="flex gap-6 items-center justify-center">
              <i
                className="modus-icons text-4xl"
                style={{ color: "var(--modus-color-primary)" }}
              >
                home
              </i>
              <i
                className="modus-icons text-4xl"
                style={{ color: "var(--modus-color-success)" }}
              >
                check_circle
              </i>
              <i
                className="modus-icons text-4xl"
                style={{ color: "var(--modus-color-warning)" }}
              >
                warning
              </i>
              <i
                className="modus-icons text-4xl"
                style={{ color: "var(--modus-color-info)" }}
              >
                info
              </i>
            </div>
          </div>

          {/* Status Examples */}
          <div className="modus-card w-full max-w-2xl">
            <h2 className="text-2xl font-bold mb-4">Status Messages</h2>
            <div className="space-y-4">
              <div className="modus-alert modus-alert-success">
                <strong>Success:</strong> Your action was completed
                successfully!
              </div>
              <div className="modus-alert modus-alert-warning">
                <strong>Warning:</strong> Please review your input.
              </div>
              <div className="modus-alert modus-alert-error">
                <strong>Error:</strong> Something went wrong.
              </div>
              <div className="modus-alert modus-alert-info">
                <strong>Info:</strong> Here's some helpful information.
              </div>
            </div>
          </div>
        </div>
      </main>
    </>
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

## 🎯 LLM Best Practices

### 1. Theme Switching

Use JavaScript to toggle between light and dark themes:

```tsx
const toggleTheme = () => {
  const newTheme =
    theme === "modus-classic-light"
      ? "modus-classic-dark"
      : "modus-classic-light";
  document.documentElement.setAttribute("data-theme", newTheme);
};
```

### 2. Layout & Spacing - Use Tailwind Classes

- **Layout**: `flex`, `flex-col`, `grid`, `items-center`, `justify-center`
- **Spacing**: `p-4`, `p-8`, `m-4`, `mb-4`, `gap-4`, `gap-8`
- **Sizing**: `w-full`, `max-w-md`, `h-screen`, `text-lg`, `text-2xl`

### 3. Colors - Use Modus CSS Variables

- **Primary actions**: `style={{ color: 'var(--modus-color-primary)' }}`
- **Success states**: `style={{ color: 'var(--modus-color-success)' }}`
- **Warnings**: `style={{ color: 'var(--modus-color-warning)' }}`
- **Errors**: `style={{ color: 'var(--modus-color-error)' }}`

### 4. Typography

- **Font Family**: Always use Open Sans (already set in global CSS)
- **Font Sizes**: Use Tailwind classes (`text-sm`, `text-lg`, `text-2xl`) or Modus variables

### 5. Icons Usage

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

### 6. Best Practice Combination

```tsx
// ✅ Good: Tailwind for layout, Modus colors and classes for theming
<div className="flex items-center gap-4 p-8">
  <button className="modus-btn modus-btn-primary">Action</button>
  <i
    className="modus-icons text-2xl"
    style={{ color: "var(--modus-color-primary)" }}
  >
    home
  </i>
</div>
```

## 📚 Resources

- **Modus Icons Library**: http://modus-icons.trimble.com/
- **Design System Guidelines**: https://modus.trimble.com/
- **Next.js Documentation**: https://nextjs.org/docs

## ✅ Verification Checklist

After setup, verify these work:

- [ ] Theme switching (light/dark)
- [ ] Icons display correctly
- [ ] Modus color variables apply correctly
- [ ] Typography renders with Open Sans
- [ ] Responsive design functions
- [ ] Form inputs styled properly
- [ ] Button styles work correctly
