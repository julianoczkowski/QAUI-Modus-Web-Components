# Modus React Components — Setup Guide

A comprehensive guide for integrating the official Modus React Components library into React applications, including TypeScript support, proper event handling, and best practices.

**Note**: This guide covers the **official Modus React Components library** (`@trimble-oss/moduswebcomponents-react`), which is the recommended approach for React projects. This library provides proper React wrapper components that are automatically generated using Stencil's React Framework Integration.

---

## 1. Installation & Dependencies

### Primary Installation

Install the Modus React Components library with the appropriate React version:

```bash
# For React 18 (most common)
npm install @trimble-oss/moduswebcomponents-react@<latest-version>-react18

# Example with specific version
npm install @trimble-oss/moduswebcomponents-react@1.0.0-react18

# For React 17
npm install @trimble-oss/moduswebcomponents-react@<latest-version>-react17
```

**Important**:

- Specify the target React version in the package name
- Lock the installed package versions to avoid unintended breakages
- The React library has a peer dependency on the base web components package

### Optional Dependencies (Install as needed)

```bash
# TypeScript support (if not already installed in your React project)
npm install --save-dev @types/react @types/react-dom

# Chart.js (only if you need data visualization/charts)
npm install chart.js

# Tailwind CSS (only if you want utility-first CSS alongside Modus)
npm install -D tailwindcss postcss autoprefixer
```

**Note**: Most React/Next.js projects won't need these additional dependencies. Modus React Components work perfectly with just the core installation.

---

## 2. React Application Setup

### 2.1 Styling Setup

In your main CSS file (`src/index.css` or `src/App.css`) or main JavaScript entry point:

```tsx
// Import in your main JavaScript file
import "@trimble-oss/moduswebcomponents/modus-wc-styles.css";
```

Or in CSS:

```css
/* Import in your main CSS file */
@import url("@trimble-oss/moduswebcomponents/modus-wc-styles.css");
```

### 2.2 Icons and Fonts Setup (Required)

#### Install Modus Icons Package

```bash
npm install @trimble-oss/modus-icons
```

#### Add Icon Fonts and Google Fonts

In your main CSS file (`src/index.css` or `src/App.css`):

```css
/* Modus Icons - Choose one variant */
@import url("https://cdn.jsdelivr.net/npm/@trimble-oss/modus-icons@1/dist/modus-outlined/fonts/modus-icons.css");
/* OR for solid icons: */
@import url("https://cdn.jsdelivr.net/npm/@trimble-oss/modus-icons@1/dist/modus-solid/fonts/modus-icons.css");

/* Google Fonts: Open Sans (Required for proper typography) */
@import url("https://fonts.googleapis.com/css2?family=Open+Sans:ital,wght@0,300..800;1,300..800&display=swap");
```

### 2.3 HTML Theme Attribute

In your `public/index.html`, ensure the root HTML element has the theme attribute:

```html
<!DOCTYPE html>
<html lang="en" data-theme="modus-modern-light">
  <head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1" />
    <title>My Modus React App</title>
  </head>
  <body>
    <div id="root"></div>
  </body>
</html>
```

**Available themes**: `modus-modern-light` · `modus-modern-dark` · `modus-classic-light` · `modus-classic-dark`

---

## 3. Basic Usage

### 3.1 Simple Component Usage

Import and use Modus React Components like any other React component:

```tsx
import React from "react";
import {
  ModusWcButton,
  ModusWcBadge,
  ModusWcAlert,
} from "@trimble-oss/moduswebcomponents-react";

const BasicExample: React.FC = () => {
  return (
    <div>
      {/* Simple button */}
      <ModusWcButton color="primary" size="md">
        Click Me
      </ModusWcButton>

      {/* Badge */}
      <ModusWcBadge aria-label="Badge" content="New" />

      {/* Alert */}
      <ModusWcAlert variant="success" alertTitle="Success!" dismissible>
        Operation completed successfully.
      </ModusWcAlert>
    </div>
  );
};

export default BasicExample;
```

### 3.2 TypeScript Support

The Modus React Components library includes full TypeScript support out of the box. Component props are automatically typed:

```tsx
import React from "react";
import {
  ModusWcTextInput,
  ModusWcButton,
} from "@trimble-oss/moduswebcomponents-react";

const TypedExample: React.FC = () => {
  return (
    <div>
      {/* TypeScript will provide autocomplete and type checking */}
      <ModusWcTextInput
        label="Enter your name"
        placeholder="John Doe"
        required={true}
        size="md"
        // TypeScript will catch invalid prop values
        // color="invalid-color" // This would cause a TypeScript error
      />

      <ModusWcButton
        color="primary"
        variant="filled"
        size="lg"
        disabled={false}
      >
        Submit
      </ModusWcButton>
    </div>
  );
};

export default TypedExample;
```

---

## 4. Event Handling

### 4.1 Basic Event Handling

Modus React Components use standard React event patterns with proper TypeScript support:

```tsx
import React from "react";
import {
  ModusWcButton,
  ModusWcTextInput,
} from "@trimble-oss/moduswebcomponents-react";

const EventHandlingExample: React.FC = () => {
  const handleButtonClick = (event: CustomEvent) => {
    console.log("Button clicked:", event.detail);
  };

  const handleInputChange = (event: CustomEvent) => {
    console.log("Input changed:", event.detail);
  };

  return (
    <div>
      <ModusWcButton onButtonClick={handleButtonClick}>
        Click Handler
      </ModusWcButton>

      <ModusWcTextInput label="Enter text" onInputChange={handleInputChange} />
    </div>
  );
};

export default EventHandlingExample;
```

### 4.2 Controlled Input Pattern

The recommended pattern for form inputs with React state management:

```tsx
import React, { useState } from "react";
import { ModusWcTextInput } from "@trimble-oss/moduswebcomponents-react";

interface Props extends React.ComponentProps<typeof ModusWcTextInput> {}

const ControlledInput: React.FC<Props> = (props) => {
  const [value, setValue] = useState("");

  const handleInputChange = (
    e: CustomEvent<HTMLModusWcTextInputElementEventMap["inputChange"]>
  ) => {
    const value = e.detail.target.value;
    setValue(value);
  };

  return (
    <ModusWcTextInput
      {...props}
      onInputChange={handleInputChange}
      value={value}
    />
  );
};

export default ControlledInput;
```

## 5. Component Wrapping Pattern

### 5.1 Basic Component Wrapper

It's recommended to wrap Modus components in your own React components for better abstraction:

```tsx
import React from "react";
import { ModusWcAvatar } from "@trimble-oss/moduswebcomponents-react";

interface Props extends React.ComponentProps<typeof ModusWcAvatar> {}

const Avatar: React.FC<Props> = (props) => {
  return <ModusWcAvatar {...props} />;
};

export default Avatar;
```

### 5.2 Enhanced Component Wrapper

Create more sophisticated wrappers with custom logic:

```tsx
import React from "react";
import { ModusWcTextInput } from "@trimble-oss/moduswebcomponents-react";

interface Props
  extends Omit<React.ComponentProps<typeof ModusWcTextInput>, "inputChange"> {
  onValueChange: (value: string) => void;
}

const TextInput: React.FC<Props> = (props) => {
  const handleInputChange = (
    e: CustomEvent<HTMLModusWcTextInputElementEventMap["inputChange"]>
  ) => {
    const value = e.detail.target.value;
    props.onValueChange(value);
  };

  return <ModusWcTextInput {...props} onInputChange={handleInputChange} />;
};

export default TextInput;
```

## 6. Form Integration

### 6.1 Complete Form Example

```tsx
import React, { useState } from "react";
import {
  ModusWcTextInput,
  ModusWcSelect,
  ModusWcTextarea,
  ModusWcCheckbox,
  ModusWcButton,
} from "@trimble-oss/moduswebcomponents-react";

const FormExample: React.FC = () => {
  const [formData, setFormData] = useState({
    name: "",
    email: "",
    category: "",
    description: "",
    agreed: false,
  });

  const categoryOptions = [
    { label: "Select a category...", value: "" },
    { label: "Bug Report", value: "bug" },
    { label: "Feature Request", value: "feature" },
    { label: "General Inquiry", value: "general" },
  ];

  const handleSubmit = (e: React.FormEvent) => {
    e.preventDefault();
    console.log("Form submitted:", formData);
  };

  return (
    <form onSubmit={handleSubmit}>
      <ModusWcTextInput
        label="Name"
        required
        value={formData.name}
        onInputChange={(e) =>
          setFormData({ ...formData, name: e.detail.target.value })
        }
      />

      <ModusWcTextInput
        label="Email"
        type="email"
        required
        value={formData.email}
        onInputChange={(e) =>
          setFormData({ ...formData, email: e.detail.target.value })
        }
      />

      <ModusWcSelect
        label="Category"
        required
        options={categoryOptions}
        value={formData.category}
        onInputChange={(e) =>
          setFormData({ ...formData, category: e.detail.target.value })
        }
      />

      <ModusWcTextarea
        label="Description"
        rows={4}
        value={formData.description}
        onInputChange={(e) =>
          setFormData({ ...formData, description: e.detail.target.value })
        }
      />

      <ModusWcCheckbox
        label="I agree to the terms"
        checked={formData.agreed}
        onInputChange={(e) =>
          setFormData({ ...formData, agreed: e.detail.target.checked })
        }
      />

      <ModusWcButton type="submit" color="primary">
        Submit
      </ModusWcButton>
    </form>
  );
};

export default FormExample;
```

---

## 7. Theme Management in React

### 7.1 Theme Switcher Component

```tsx
import React, { useState, useEffect } from "react";
import { ModusWcThemeSwitcher } from "@trimble-oss/moduswebcomponents-react";

const ThemeSwitcher: React.FC = () => {
  const [currentTheme, setCurrentTheme] = useState("modus-modern-light");

  useEffect(() => {
    // Apply theme to document
    document.documentElement.setAttribute("data-theme", currentTheme);

    // Persist to localStorage
    localStorage.setItem("modus-theme", currentTheme);
  }, [currentTheme]);

  useEffect(() => {
    // Load saved theme on mount
    const savedTheme = localStorage.getItem("modus-theme");
    if (savedTheme) {
      setCurrentTheme(savedTheme);
    }
  }, []);

  return (
    <ModusWcThemeSwitcher
      onThemeChange={(e) => setCurrentTheme(e.detail.theme)}
    />
  );
};

export default ThemeSwitcher;
```

### 7.2 Manual Theme Selection

```tsx
import React, { useState, useEffect } from "react";
import { ModusWcSelect } from "@trimble-oss/moduswebcomponents-react";

const ManualThemeSelector: React.FC = () => {
  const [currentTheme, setCurrentTheme] = useState("modus-modern-light");

  const themeOptions = [
    { label: "Modern Light", value: "modus-modern-light" },
    { label: "Modern Dark", value: "modus-modern-dark" },
    { label: "Classic Light", value: "modus-classic-light" },
    { label: "Classic Dark", value: "modus-classic-dark" },
  ];

  useEffect(() => {
    document.documentElement.setAttribute("data-theme", currentTheme);
    localStorage.setItem("modus-theme", currentTheme);
  }, [currentTheme]);

  return (
    <ModusWcSelect
      label="Choose Theme"
      options={themeOptions}
      value={currentTheme}
      onInputChange={(e) => setCurrentTheme(e.detail.target.value)}
    />
  );
};

export default ManualThemeSelector;
```

---

## 8. Advanced Patterns & Best Practices

### 8.1 Toast Notifications

```tsx
import React, { useState } from "react";
import {
  ModusWcButton,
  ModusWcToast,
  ModusWcAlert,
} from "@trimble-oss/moduswebcomponents-react";

const ToastExample: React.FC = () => {
  const [toasts, setToasts] = useState<
    Array<{ id: string; message: string; variant: string }>
  >([]);

  const showToast = (message: string, variant: string = "info") => {
    const id = Date.now().toString();
    setToasts((prev) => [...prev, { id, message, variant }]);

    // Auto-remove after 5 seconds
    setTimeout(() => {
      setToasts((prev) => prev.filter((toast) => toast.id !== id));
    }, 5000);
  };

  const removeToast = (id: string) => {
    setToasts((prev) => prev.filter((toast) => toast.id !== id));
  };

  return (
    <div>
      <ModusWcButton
        onButtonClick={() => showToast("Hello from React!", "success")}
      >
        Show Toast
      </ModusWcButton>

      {toasts.map((toast) => (
        <ModusWcToast key={toast.id}>
          <ModusWcAlert
            variant={toast.variant}
            alertTitle={toast.message}
            dismissible
            onDismiss={() => removeToast(toast.id)}
          />
        </ModusWcToast>
      ))}
    </div>
  );
};

export default ToastExample;
```

### 8.2 Dynamic Component Lists

```tsx
import React, { useState } from "react";
import {
  ModusWcButton,
  ModusWcChip,
} from "@trimble-oss/moduswebcomponents-react";

const DynamicChipList: React.FC = () => {
  const [chips, setChips] = useState<string[]>([
    "React",
    "TypeScript",
    "Modus",
  ]);

  const addChip = () => {
    const newChip = `Item ${chips.length + 1}`;
    setChips((prev) => [...prev, newChip]);
  };

  const removeChip = (index: number) => {
    setChips((prev) => prev.filter((_, i) => i !== index));
  };

  return (
    <div>
      <ModusWcButton onButtonClick={addChip}>Add Chip</ModusWcButton>

      <div style={{ display: "flex", gap: "8px", marginTop: "16px" }}>
        {chips.map((chip, index) => (
          <ModusWcChip
            key={index}
            chipStyle="outline"
            showClose
            onChipClose={() => removeChip(index)}
          >
            {chip}
          </ModusWcChip>
        ))}
      </div>
    </div>
  );
};

export default DynamicChipList;
```

---

## 9. Charts Integration

For data visualization using Chart.js:

```tsx
import React, { useRef, useEffect } from "react";
import { Chart, registerables } from "chart.js";

Chart.register(...registerables);

const ChartExample: React.FC = () => {
  const chartRef = useRef<HTMLCanvasElement>(null);

  useEffect(() => {
    if (chartRef.current) {
      new Chart(chartRef.current, {
        type: "bar",
        data: {
          labels: ["Q1", "Q2", "Q3", "Q4"],
          datasets: [
            {
              label: "2025 Revenue ($M)",
              data: [12, 18, 16, 21],
              backgroundColor: "var(--modus-blue-primary, #0063a3)",
            },
          ],
        },
        options: {
          responsive: true,
          plugins: {
            legend: { position: "bottom" },
            tooltip: { mode: "index", intersect: false },
          },
        },
      });
    }
  }, []);

  return <canvas ref={chartRef} width="600" height="400" />;
};

export default ChartExample;
```

---

## 10. Testing Considerations

### 10.1 Jest Configuration

Testing Modus React Components works like testing any other React components:

```javascript
// jest.config.js
module.exports = {
  // ... other config
  setupFilesAfterEnv: ["<rootDir>/src/setupTests.ts"],
  testEnvironment: "jsdom",
};
```

### 10.2 Testing Example

```tsx
import React from "react";
import { render, screen, fireEvent } from "@testing-library/react";
import "@testing-library/jest-dom";
import {
  ModusWcButton,
  ModusWcTextInput,
} from "@trimble-oss/moduswebcomponents-react";

test("renders modus button", () => {
  render(<ModusWcButton>Test Button</ModusWcButton>);
  expect(screen.getByText("Test Button")).toBeInTheDocument();
});

test("handles button click", () => {
  const handleClick = jest.fn();
  render(<ModusWcButton onButtonClick={handleClick}>Click Me</ModusWcButton>);

  fireEvent.click(screen.getByText("Click Me"));
  expect(handleClick).toHaveBeenCalled();
});

test("handles input change", () => {
  const handleChange = jest.fn();
  render(<ModusWcTextInput label="Test Input" onInputChange={handleChange} />);

  const input = screen.getByLabelText("Test Input");
  fireEvent.change(input, { target: { value: "test value" } });
  expect(handleChange).toHaveBeenCalled();
});
```

---

## 11. Performance Optimization

### 11.1 Lazy Loading Components

```tsx
import React, { lazy, Suspense } from "react";
import { ModusWcLoader } from "@trimble-oss/moduswebcomponents-react";

const HeavyModusComponent = lazy(
  () => import("./components/HeavyModusComponent")
);

const App: React.FC = () => {
  return (
    <Suspense fallback={<ModusWcLoader />}>
      <HeavyModusComponent />
    </Suspense>
  );
};
```

### 11.2 Memoization for Complex Props

```tsx
import React, { useMemo } from "react";
import { ModusWcSelect } from "@trimble-oss/moduswebcomponents-react";

const OptimizedSelect: React.FC<{ data: any[] }> = ({ data }) => {
  const options = useMemo(
    () => data.map((item) => ({ label: item.name, value: item.id })),
    [data]
  );

  return <ModusWcSelect options={options} label="Optimized Select" />;
};

export default OptimizedSelect;
```

---

## 12. Icon Usage in React

There are multiple ways to use Modus Icons in React. Choose the method that best fits your needs:

### 12.1 Icon Font Method (Recommended)

**Best for**: Most React applications, easy styling, good performance

After installing the icon fonts (see section 2.2), use the simple `<i>` element:

```tsx
import React from "react";

const IconExamples: React.FC = () => {
  return (
    <div>
      {/* Basic icons */}
      <i className="modus-icons">add</i>
      <i className="modus-icons">delete</i>
      <i className="modus-icons">edit</i>

      {/* Styled icons */}
      <i
        className="modus-icons"
        style={{ fontSize: "2rem", color: "var(--modus-blue-primary)" }}
      >
        settings
      </i>

      {/* In buttons */}
      <button>
        <i className="modus-icons">save</i>
        Save Document
      </button>
    </div>
  );
};
```

### 12.2 ModusWcIcon Component

**Best for**: When you need component-level props and integration with other Modus components

```tsx
import React from "react";
import {
  ModusWcIcon,
  ModusWcButton,
} from "@trimble-oss/moduswebcomponents-react";

const ModusIconExamples: React.FC = () => {
  return (
    <div>
      {/* Basic Modus icon component */}
      <ModusWcIcon name="add" />
      <ModusWcIcon name="delete" />

      {/* In Modus buttons */}
      <ModusWcButton variant="outlined" shape="circle">
        <ModusWcIcon name="settings" decorative />
      </ModusWcButton>
    </div>
  );
};
```

### 12.3 SVG Import Method (Advanced)

**Best for**: Tree-shaking, when you only need a few specific icons, TypeScript strict mode

```tsx
import React from "react";
// Import specific SVG icons (requires @trimble-oss/modus-icons package)
import AddIcon from "@trimble-oss/modus-icons/dist/modus-outlined/svg/add.svg";
import DeleteIcon from "@trimble-oss/modus-icons/dist/modus-outlined/svg/delete.svg";

const SVGIconExamples: React.FC = () => {
  return (
    <div>
      {/* Direct SVG imports */}
      <img src={AddIcon} alt="Add" width="24" height="24" />
      <img src={DeleteIcon} alt="Delete" width="24" height="24" />

      {/* Inline SVG for better control */}
      <svg width="24" height="24" fill="currentColor" viewBox="0 0 24 24">
        <use href="#add" />
      </svg>
    </div>
  );
};
```

### 12.4 Reusable Icon Component (Best Practice)

Create a wrapper component for consistent icon usage:

```tsx
import React from "react";

interface IconProps {
  name: string;
  size?: "sm" | "md" | "lg" | "xl";
  color?: string;
  className?: string;
  "aria-label"?: string;
  decorative?: boolean;
}

const Icon: React.FC<IconProps> = ({
  name,
  size = "md",
  color,
  className = "",
  "aria-label": ariaLabel,
  decorative = false,
}) => {
  const sizeMap = {
    sm: "1rem",
    md: "1.25rem",
    lg: "1.5rem",
    xl: "2rem",
  };

  return (
    <i
      className={`modus-icons ${className}`}
      style={{
        fontSize: sizeMap[size],
        color: color,
      }}
      aria-label={decorative ? undefined : ariaLabel || name}
      aria-hidden={decorative}
    >
      {name}
    </i>
  );
};

// Usage
const MyComponent: React.FC = () => {
  return (
    <div>
      <Icon name="add" size="lg" color="var(--modus-blue-primary)" />
      <Icon name="delete" decorative />
      <Icon name="settings" aria-label="Open settings" />
    </div>
  );
};
```

### 12.5 Available Icon Names

Common icon names you can use:

```tsx
// Basic actions
add, delete, edit, save, search, settings, user, home, calendar, email

// Navigation
arrow_left, arrow_right, arrow_up, arrow_down, chevron_left, chevron_right

// UI elements
close, menu, more_vertical, more_horizontal, check, cancel

// File operations
file, folder_open, folder_closed, download, upload

// Communication
phone, email, chat, notifications

// Status
check_circle, warning, error, info, success
```

**Full icon list**: [Modus Icons Reference](http://modus-icons.trimble.com/modus-solid/#install)

### 12.6 Accessibility Best Practices

```tsx
// Decorative icons (no meaning)
<i className="modus-icons" aria-hidden="true">star</i>

// Meaningful icons
<i className="modus-icons" aria-label="Delete item">delete</i>

// Icons in buttons
<button aria-label="Save document">
  <i className="modus-icons" aria-hidden="true">save</i>
</button>

// Icons with text
<button>
  <i className="modus-icons" aria-hidden="true">save</i>
  Save Document
</button>
```

---

## 13. Complete Example App

```tsx
// App.tsx
import React, { useState } from "react";
import {
  ModusWcNavbar,
  ModusWcCard,
  ModusWcSelect,
  ModusWcAlert,
  ModusWcButton,
} from "@trimble-oss/moduswebcomponents-react";

const App: React.FC = () => {
  const [selectedValue, setSelectedValue] = useState("");

  const frameworkOptions = [
    { label: "Choose your framework...", value: "" },
    { label: "React", value: "react" },
    { label: "Vue", value: "vue" },
    { label: "Angular", value: "angular" },
  ];

  const userCard = {
    name: "React Developer",
    email: "dev@trimble.com",
  };

  const visibility = {
    apps: true,
    help: true,
    search: true,
    user: true,
  };

  return (
    <div>
      <ModusWcNavbar userCard={userCard} visibility={visibility}>
        <span slot="center">Modus React App</span>
      </ModusWcNavbar>

      <main style={{ padding: "2rem" }}>
        <ModusWcCard>
          <h2 slot="header">Welcome to Modus + React</h2>

          <ModusWcSelect
            label="Choose your framework"
            options={frameworkOptions}
            value={selectedValue}
            onInputChange={(e) => setSelectedValue(e.detail.target.value)}
          />

          {selectedValue && (
            <ModusWcAlert
              variant="success"
              alertTitle="Great choice!"
              dismissible
            >
              You selected {selectedValue}
            </ModusWcAlert>
          )}

          <div slot="actions">
            <ModusWcButton color="primary">Get Started</ModusWcButton>
          </div>
        </ModusWcCard>
      </main>
    </div>
  );
};

export default App;
```

---

## Summary

This guide provides everything needed to successfully integrate the **official Modus React Components library** into React applications. Key takeaways:

1. **Use the dedicated React library**: `@trimble-oss/moduswebcomponents-react` with proper React version targeting
2. **Icons and fonts are mandatory**: Install `@trimble-oss/modus-icons` and import the CSS for proper functionality
3. **Multiple icon usage options**: Icon fonts (recommended), ModusWcIcon component, or direct SVG imports
4. **Import components like regular React components**: No need for `defineCustomElements()` or refs for basic usage
5. **Full TypeScript support**: Components come with proper typing out of the box
6. **Standard React patterns**: Event handling, controlled inputs, and component composition work as expected
7. **Wrap components**: Create your own wrapper components for better abstraction and flexibility
8. **Testing is straightforward**: Use standard React testing patterns with React Testing Library

The React Components library provides a much better developer experience than using the raw web components, with proper React integration, TypeScript support, and familiar patterns. Remember that **fonts and icons are essential dependencies**, not optional additions.
