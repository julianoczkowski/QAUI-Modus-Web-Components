##

CSS file uses a multi-layered system with a base color palette and then applies those colors to semantic names based on the selected theme (e.g., `modus-classic-light`, `modus-classic-dark`).

Here is a breakdown of the colors, organized for use cases.

### 1. Base Color Palette

These are the foundational colors defined in the file. The thematic colors below will reference these variables.

```css
/* --- White / Grays / Black --- */
--modus-wc-color-white: #fff;
--modus-wc-color-gray-light: #f1f1f6;
--modus-wc-color-gray-0: #e0e1e9;
--modus-wc-color-gray-1: #cbcdd6;
--modus-wc-color-gray-2: #b7b9c3;
--modus-wc-color-gray-3: #a3a6b1;
--modus-wc-color-gray-4: #90939f;
--modus-wc-color-gray-5: #7d808d;
--modus-wc-color-gray-6: #6a6e79;
--modus-wc-color-gray-7: #585c65;
--modus-wc-color-gray-8: #464b52;
--modus-wc-color-gray-9: #353a40;
--modus-wc-color-gray-10: #171c1e;
--modus-wc-color-trimble-gray: #252a2e;
--modus-wc-color-black: #000;

/* --- Blues --- */
--modus-wc-color-blue-pale: #dcedf9;
--modus-wc-color-highlight-blue: #019aeb;
--modus-wc-color-blue-light: #217cbb;
--modus-wc-color-trimble-blue: #0063a3;
--modus-wc-color-blue-dark: #0e416c;

/* --- Yellows --- */
--modus-wc-color-yellow-pale: #fff5e4;
--modus-wc-color-yellow-light: #fec157;
--modus-wc-color-yellow: #fbad26;
--modus-wc-color-yellow-dark: #e49325;

/* --- Reds --- */
--modus-wc-color-red-pale: #fbd4d7;
--modus-wc-color-red-light: #e86363;
--modus-wc-color-red: #da212c;
--modus-wc-color-red-dark: #ab1f26;

/* --- Greens --- */
--modus-wc-color-green-pale: #e0eccf;
--modus-wc-color-green-light: #4ea646;
--modus-wc-color-green: #1e8a44;
--modus-wc-color-green-dark: #006638;

/* --- Special In-Field Colors --- */
--modus-wc-in-field-success-dark-bg: #00fe00;
--modus-wc-in-field-success-light-bg: #00d22f;
--modus-wc-in-field-warning: #ff8b00;
--modus-wc-in-field-error: #da212c;
--modus-wc-in-field-info: #019aeb;
--modus-wc-in-field-avoidance: #df4eb2;
--modus-wc-in-field-black: #000;
```

### 2. Thematic Colors (Resolved Values)

This is how the semantic color names (like `--modus-wc-color-primary`) are defined for each theme.

#### Theme: `modus-modern-light`

```css
--modus-wc-color-base-page: #fff;
--modus-wc-color-base-100: #f1f1f6; /* was var(--modus-wc-color-gray-light) */
--modus-wc-color-base-200: #e0e1e9; /* was var(--modus-wc-color-gray-0) */
--modus-wc-color-base-300: #cbcdd6; /* was var(--modus-wc-color-gray-1) */
--modus-wc-color-base-content: #171c1e; /* was var(--modus-wc-color-gray-10) */
--modus-wc-color-primary: #0063a3; /* was var(--modus-wc-color-trimble-blue) */
--modus-wc-color-primary-content: #fff; /* was var(--modus-wc-color-white) */
```

#### Theme: `modus-modern-dark`

```css
--modus-wc-color-base-page: #000;
--modus-wc-color-base-100: #252a2e; /* was var(--modus-wc-color-trimble-gray) */
--modus-wc-color-base-200: #353a40; /* was var(--modus-wc-color-gray-9) */
--modus-wc-color-base-300: #171c1e; /* was var(--modus-wc-color-gray-10) */
--modus-wc-color-base-content: #cbcdd6; /* was var(--modus-wc-color-gray-1) */
--modus-wc-color-primary: #019aeb; /* was var(--modus-wc-color-highlight-blue) */
--modus-wc-color-primary-content: #000; /* was var(--modus-wc-color-black) */
```

#### Theme: `modus-classic-light`

```css
--modus-wc-color-base-page: #fff;
--modus-wc-color-base-100: #f1f1f6; /* was var(--modus-wc-color-gray-light) */
--modus-wc-color-base-200: #cbcdd6; /* was var(--modus-wc-color-gray-1) */
--modus-wc-color-base-300: #b7b9c3; /* was var(--modus-wc-color-gray-2) */
--modus-wc-color-base-content: #171c1e; /* was var(--modus-wc-color-gray-10) */
--modus-wc-color-info: #0063a3; /* was var(--modus-wc-color-trimble-blue) */
--modus-wc-color-success: #1e8a44; /* was var(--modus-wc-color-green) */
--modus-wc-color-error: #da212c; /* was var(--modus-wc-color-red) */
--modus-wc-color-warning: #fbad26; /* was var(--modus-wc-color-yellow) */
```

#### Theme: `modus-classic-dark`

```css
--modus-wc-color-base-page: #000;
--modus-wc-color-base-100: #252a2e; /* was var(--modus-wc-color-trimble-gray) */
--modus-wc-color-base-200: #464b52; /* was var(--modus-wc-color-gray-8) */
--modus-wc-color-base-300: #353a40; /* was var(--modus-wc-color-gray-9) */
--modus-wc-color-base-content: #cbcdd6; /* was var(--modus-wc-color-gray-1) */
--modus-wc-color-info: #0063a3; /* was var(--modus-wc-color-trimble-blue) */
--modus-wc-color-success: #1e8a44; /* was var(--modus-wc-color-green) */
--modus-wc-color-error: #da212c; /* was var(--modus-wc-color-red) */
--modus-wc-color-warning: #fbad26; /* was var(--modus-wc-color-yellow) */
```

### 3. Fallback Colors (for older browsers)

These are defined inside an `@supports not (color:oklch(0% 0 0))` block, meaning they are for browsers that don't support the `oklch` color function.

#### Fallback Light Theme

```css
--fallback-p: #491eff;
--fallback-pc: #d4dbff;
--fallback-s: #ff41c7;
--fallback-sc: #fff9fc;
--fallback-a: #00cfbd;
--fallback-ac: #00100d;
--fallback-n: #2b3440;
--fallback-nc: #d7dde4;
--fallback-b1: #fff;
--fallback-b2: #e5e6e6;
--fallback-b3: #e5e6e6;
--fallback-bc: #1f2937;
--fallback-in: #00b3f0;
--fallback-inc: #000;
--fallback-su: #00ca92;
--fallback-suc: #000;
--fallback-wa: #ffc22d;
--fallback-wac: #000;
--fallback-er: #ff6f70;
--fallback-erc: #000;
```

#### Fallback Dark Theme

```css
--fallback-p: #7582ff;
--fallback-pc: #050617;
--fallback-s: #ff71cf;
--fallback-sc: #190211;
--fallback-a: #00c7b5;
--fallback-ac: #000e0c;
--fallback-n: #2a323c;
--fallback-nc: #a6adbb;
--fallback-b1: #1d232a;
--fallback-b2: #191e24;
--fallback-b3: #15191e;
--fallback-bc: #a6adbb;
--fallback-in: #00b3f0;
--fallback-inc: #000;
--fallback-su: #00ca92;
--fallback-suc: #000;
--fallback-wa: #ffc22d;
--fallback-wac: #000;
--fallback-er: #ff6f70;
--fallback-erc: #000;
```
