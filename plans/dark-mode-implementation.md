# Dark Mode Implementation Plan

## Overview
Add a dark mode / light mode toggle to the portfolio website with system preference detection. The implementation uses CSS custom properties (variables) for clean theme switching without duplicating CSS.

## Approach
- **CSS Custom Properties**: Define all colors as CSS variables on `:root` (light) and `[data-theme="dark"]` (dark)
- **System Detection**: Use `prefers-color-scheme` media query for initial theme
- **LocalStorage**: Persist user choice across sessions
- **Toggle Button**: Add sun/moon icon in the sidebar
- **Zero Bootstrap Override**: Only touch `style.css`, not `bootstrap.css`

---

## Color Palette

### Light Mode (Current)
| Element | Color | Variable |
|---------|-------|----------|
| Body Background | `#fff` (white) | `--bg-body` |
| Sidebar Background | `#b9d6f361` (translucent blue) | `--bg-sidebar` |
| Sidebar Text | `rgba(0,0,0,0.7)` | `--text-sidebar` |
| Sidebar Logo Link | `#000` (black) | `--text-logo` |
| Section Background | Alternating `#fff` / `#fafafa` | `--bg-section` / `--bg-section-alt` |
| Heading Text | `#000` (black) | `--text-heading` |
| Body Text | `rgba(0,0,0,0.7)` | `--text-body` |
| Link Color | `#2c98f0` (blue) | `--color-link` |
| Card Background | `#f2f3f7` (light gray) | `--bg-card` |
| Panel Background | `#f2f3f7` | `--bg-panel` |
| Timeline Line | `#f2f3f7` | `--bg-timeline` |
| Service Card | `#f2f3f7` | `--bg-service` |
| Progress Bar Track | `#f2f3f7` | `--bg-progress` |
| Form Input | `#f2f3f7` | `--bg-input` |
| Form Input Focus | `#f0f0f0` | `--bg-input-focus` |
| Nav Toggle | `#000` | `--color-nav-toggle` |
| Hire Box | `#f9bf3f` (yellow) | `--bg-hire` |
| Award Entry | `#f9f9f9` | `--bg-award` |
| Skills Category | `#f9f9f9` | `--bg-skill` |
| Project Card | `#fff` | `--bg-project` |
| Selection Background | `#2c98f0` | `--bg-selection` |
| Selection Text | `#fff` | `--text-selection` |

### Dark Mode (Proposed)
| Element | Color | Variable |
|---------|-------|----------|
| Body Background | `#1a1a2e` (deep navy) | `--bg-body` |
| Sidebar Background | `#16213e` (dark blue) | `--bg-sidebar` |
| Sidebar Text | `rgba(255,255,255,0.8)` | `--text-sidebar` |
| Sidebar Logo Link | `#fff` (white) | `--text-logo` |
| Section Background | Alternating `#1a1a2e` / `#16213e` | `--bg-section` / `--bg-section-alt` |
| Heading Text | `#e0e0e0` (light gray) | `--text-heading` |
| Body Text | `rgba(255,255,255,0.7)` | `--text-body` |
| Link Color | `#5dade2` (lighter blue) | `--color-link` |
| Card Background | `#16213e` (dark blue) | `--bg-card` |
| Panel Background | `#16213e` | `--bg-panel` |
| Timeline Line | `#16213e` | `--bg-timeline` |
| Service Card | `#16213e` | `--bg-service` |
| Progress Bar Track | `#16213e` | `--bg-progress` |
| Form Input | `#16213e` | `--bg-input` |
| Form Input Focus | `#0f3460` | `--bg-input-focus` |
| Nav Toggle | `#fff` | `--color-nav-toggle` |
| Hire Box | `#f9bf3f` (keep yellow) | `--bg-hire` |
| Award Entry | `#16213e` | `--bg-award` |
| Skills Category | `#16213e` | `--bg-skill` |
| Project Card | `#16213e` | `--bg-project` |
| Selection Background | `#5dade2` | `--bg-selection` |
| Selection Text | `#1a1a2e` | `--text-selection` |

**Accent colors** (unchanged in both modes):
- `#2c98f0` (blue) - primary
- `#ec5453` (red) - color-2
- `#f9bf3f` (yellow) - color-3
- `#a84cb8` (purple) - color-4
- `#2fa499` (teal) - color-5
- `#4054b2` (indigo) - color-6

---

## Additional Color Values Discovered (Deep Audit)

The following color values were found during a deeper CSS audit and need to be covered:

| Element | Current Color | Dark Mode Target | Notes |
|---------|---------------|------------------|-------|
| Position Gold text | `#f6c14d` | Keep or adjust to `#f9bf3f` | Award position colors |
| Position Silver text | `#6e6e6ef8` | `rgba(255,255,255,0.6)` | Award position colors |
| Position Bronze text | `#d75218` | Keep or adjust to `#e8751a` | Award position colors |
| Figure caption | `#b3b3b3` | `rgba(255,255,255,0.5)` | Already in plan as `--text-body` |
| Loader background | `#fff` | `--bg-body` | Hero section loader |
| Heading meta text | `#999999` | `rgba(255,255,255,0.4)` | Section subtitle text |
| Panel collapsed bg | `#f2f3f7` | `--bg-panel` | Already covered |
| Panel collapsed border | `#e6e6e6` | `rgba(255,255,255,0.1)` | **NEW** - needs variable |
| Panel collapsed text | `#333333` | `--text-heading` | Already covered |
| Panel expanded border | `#e6e6e6` | `rgba(255,255,255,0.1)` | **NEW** - needs variable |
| Timeline box shadow | `#f2f3f7` (5px) | `--bg-body` | Timeline icon ring |
| Timeline arrow border | `#f2f3f7` | `--bg-card` | Timeline label arrow |
| Timeline label heading link | `#000` | `--text-heading` | Already covered |
| Project overlay icon bg | `rgba(255,255,255,0.5)` | `rgba(0,0,0,0.3)` | **NEW** - icon span background |
| Project overlay icon text | `#333333` | `#fff` | **NEW** - icon text color |
| Project overlay subtitle | `#333333` | `rgba(255,255,255,0.7)` | **NEW** - project subtitle |
| Project hover overlay | `rgba(0,0,0,0.4)` | `rgba(0,0,0,0.6)` | **NEW** - darken in dark mode |
| Project hover title | `#000` | `#fff` | **NEW** - title on hover |
| Counter icon bg | `#fff` | `--bg-card` | Counter circular icon |
| Counter icon color | `#2c98f0` | Keep | Counter icon accent |
| Counter label | `rgba(255,255,255,0.7)` | Keep | Already dark-theme friendly |
| Social icon text | `#000` | `rgba(255,255,255,0.7)` | **NEW** - sidebar social icons |
| Social icon hover | `#2c98f0` | Keep | Social icon hover |
| Work menu text | `#000` | `--text-heading` | **NEW** - project filter menu |
| Work menu active | `#2c98f0` | Keep | Project filter active |
| Blog entry bg | `#fff` | `--bg-card` | Commented out but present |
| Blog entry heading | `#000` | `--text-heading` | Commented out but present |
| Blog entry text | `rgba(0,0,0,0.4)` | `rgba(255,255,255,0.5)` | Commented out but present |
| Blog entry small icon | `#999999` | `rgba(255,255,255,0.4)` | Commented out but present |
| Pagination text | `#000` | `--text-heading` | **NEW** - pagination links |
| Pagination hover/active | `#2c98f0` bg, `#fff` text | Keep | Pagination states |
| Colorlib bg color | `#fafafa` | `--bg-section-alt` | Already covered |
| Nav toggle icon | `#000` | `--color-nav-toggle` | Already covered |
| Nav toggle dark icon | `#000` | `--color-nav-toggle` | Already covered |
| Form placeholder | `#999` | `rgba(255,255,255,0.3)` | Already covered |
| Popup success bg | `#4CAF50` | Keep | Form success popup |
| Popup shadow | `rgba(0,0,0,0.1)` | `rgba(0,0,0,0.3)` | **NEW** - shadow in dark mode |
| Services shadow | `rgba(0,0,0,0.17)` | `rgba(0,0,0,0.3)` | **NEW** - card shadows |
| Slider link color | `rgba(44,152,240,0.8)` | `rgba(93,173,226,0.8)` | **NEW** - hero slider links |
| Slider link border | `rgba(44,152,240,0.7)` | `rgba(93,173,226,0.7)` | **NEW** - hero slider links |
| Counter overlay | `rgba(0,0,0,0.4)` | `rgba(0,0,0,0.5)` | **NEW** - counter section overlay |

---

## UI Component Audit

### 1. Sidebar (`#colorlib-aside`)
- **Background**: `#b9d6f361` → `#16213e`
- **Logo text**: `#000` → `#fff`
- **Nav links**: `rgba(0,0,0,0.7)` → `rgba(255,255,255,0.8)`
- **Nav link hover underline**: `#2c98f0` (keep)
- **Active nav link**: `#2c98f0` (keep)
- **Footer text**: inherited → `rgba(255,255,255,0.5)`
- **Social icons**: inherited → `rgba(255,255,255,0.7)`
- **Add**: Theme toggle button above footer

### 2. Hero Section (`#colorlib-hero`)
- **Background**: `#fff` (loader) → `#1a1a2e`
- **Overlay**: keep as-is (image based)
- **H1/H2 text**: `black` → `#e0e0e0`
- **Button text**: `#000` → `#fff`
- **Button border**: `#000` → `#fff`
- **Slider control nav**: `rgba(0,0,0,0.5)` → `rgba(255,255,255,0.5)`
- **Active slider dot**: `#2c98f0` border (keep)

### 3. About Section (`.colorlib-about`)
- **Section bg**: `#fff` → `--bg-section`
- **Heading**: `#000` → `--text-heading`
- **Body text**: `rgba(0,0,0,0.7)` → `--text-body`
- **Service cards** (color-1..4): `#f2f3f7` bg → `--bg-card`
- **Hire box**: `#f9bf3f` bg (keep), text `#000` → `#000` (keep on yellow)

### 4. Services Section (`.colorlib-services`)
- **Section bg**: `#fff` → `--bg-section`
- **Heading meta**: `#727272` → `rgba(255,255,255,0.5)`
- **Heading**: `#000` → `--text-heading`
- **Service cards**: `#f2f3f7` bg → `--bg-card`
- **Service card text**: `#000` → `--text-heading`
- **Service card desc**: `#727272` → `--text-body`
- **Icon backgrounds**: accent colors (keep as-is)

### 5. Skills Section (`.colorlib-skills`)
- **Section bg**: `#fff` → `--bg-section-alt`
- **Skills categories**: `#f9f9f9` bg → `--bg-skill`
- **Category heading**: `#000` → `--text-heading`
- **Category text**: `#727272` → `--text-body`
- **Progress bar track**: `#f2f3f7` → `--bg-progress`
- **Progress bar fill**: accent colors (keep)
- **Progress percentage**: `#000` → `--text-heading`

### 6. Education Section (`.colorlib-education`)
- **Section bg**: `#fff` → `--bg-section`
- **Panel heading**: `#f2f3f7` bg → `--bg-panel`
- **Panel text**: `#000` → `--text-heading`
- **Panel body**: `#fff` → `--bg-body`
- **Collapsed panel**: `#f2f3f7` → `--bg-panel`
- **Arrow icon**: `#2c98f0` (keep)

### 7. Awards Section (`.colorlib-awards`)
- **Section bg**: `#fff` → `--bg-section-alt`
- **Award entry**: `#f9f9f9` bg → `--bg-award`
- **Border left**: `#2c98f0` (keep)
- **Heading**: `#000` → `--text-heading`
- **Date**: `#727272` → `--text-body`

### 8. Experience Section (`.colorlib-experience`)
- **Section bg**: `#fff` → `--bg-section`
- **Timeline line**: `#f2f3f7` → `--bg-timeline`
- **Timeline label**: `#f2f3f7` bg → `--bg-card`
- **Timeline icon**: accent colors (keep)
- **Heading**: `#000` → `--text-heading`
- **Body text**: `rgba(0,0,0,0.7)` → `--text-body`
- **Projects**: inherited bg → `--bg-card`
- **Tech stack**: `#727272` → `--text-body`
- **Begin marker**: `#fff` → `--bg-body`

### 9. Work/Projects Section (`.colorlib-work`)
- **Section bg**: `#fff` → `--bg-section-alt`
- **Project card**: `#fff` bg → `--bg-project`
- **Overlay**: `#2c98f0` with opacity (keep)
- **Project title**: `#000` → `--text-heading`
- **Project subtitle**: `#727272` → `--text-body`
- **View project icon**: `#2c98f0` (keep)

### 10. Contact Section (`.colorlib-contact`)
- **Section bg**: `#fff` → `--bg-section`
- **Feature boxes**: `#f2f3f7` → `--bg-card`
- **Feature icon**: `#2c98f0` (keep)
- **Feature text**: `#727272` → `--text-body`
- **Form input**: `#f2f3f7` bg → `--bg-input`, text `#000` → `--text-body`
- **Form input focus**: `#f0f0f0` → `--bg-input-focus`
- **Submit button**: `#2c98f0` (keep)
- **Popup**: `#4CAF50` (keep)

### 11. Form Controls (`.form-control`)
- **Background**: `#f2f3f7` → `--bg-input`
- **Text**: `#000` → `--text-body`
- **Focus bg**: `#f0f0f0` → `--bg-input-focus`
- **Placeholder**: `#999` → `rgba(255,255,255,0.3)`

### 12. Nav Toggle (`.colorlib-nav-toggle`)
- **Icon**: `#000` → `--color-nav-toggle`
- **Active state**: `#000` → `--color-nav-toggle`

### 13. Buttons (`.btn-primary`, `.btn-learn`, etc.)
- **Primary**: `#2c98f0` bg (keep), `#fff` text (keep)
- **Learn**: transparent bg, `#000` border/text → `#fff` border/text in dark

### 14. Typography (Global)
- **Body**: `rgba(0,0,0,0.7)` → `--text-body`
- **H1-H6**: `#000` → `--text-heading`
- **Links**: `#2c98f0` → `--color-link`
- **Selection**: `#2c98f0` bg / `#fff` text → `--bg-selection` / `--text-selection`
- **Figure caption**: `#b3b3b3` → `--text-body`

### 15. Theme Toggle Button (New)
- **Position**: In sidebar footer, above social icons
- **Icon**: Sun (light mode) / Moon (dark mode) from Icomoon
- **Size**: 30x30px circle
- **Background**: `--bg-card`
- **Icon color**: `--text-body`
- **Hover**: slight scale up animation

---

## Implementation Plan

### Phase 1: CSS Variables Foundation
1. Create `:root` block with all light mode variables
2. Create `[data-theme="dark"]` block with all dark mode variables
3. Add `@media (prefers-color-scheme: dark)` for system detection
4. Replace all hardcoded colors in `style.css` with CSS variables

### Phase 2: Toggle Button
1. Add toggle button HTML in sidebar footer (`index.html`)
2. Add CSS for toggle button (`style.css`)
3. Add JavaScript for toggle logic (`main.js`)
4. Implement localStorage persistence
5. Implement system preference detection

### Phase 3: Color Migration
1. Migrate sidebar colors
2. Migrate hero section colors
3. Migrate section colors (about, services, skills, education, awards, experience, work, contact)
4. Migrate form colors
5. Migrate typography colors
6. Migrate button colors

### Phase 4: Testing & Polish
1. Test all sections in both modes
2. Verify contrast ratios (WCAG AA)
3. Test system preference detection
4. Test localStorage persistence
5. Add smooth transition between themes

---

## File Changes

### `css/style.css`
- Add CSS variables block at top (after `@font-face`)
- Replace ~150 hardcoded color values with variables
- Add toggle button styles
- Add transition properties for smooth theme switching

### `index.html`
- Add theme toggle button in sidebar footer (1 element)

### `js/main.js`
- Add theme detection and toggle logic (~40 lines)

---

## Technical Details

### CSS Variable Structure (Updated with Additional Variables)
```css
:root {
    /* Backgrounds */
    --bg-body: #fff;
    --bg-sidebar: #b9d6f361;
    --bg-section: #fff;
    --bg-section-alt: #fafafa;
    --bg-card: #f2f3f7;
    --bg-panel: #f2f3f7;
    --bg-timeline: #f2f3f7;
    --bg-service: #f2f3f7;
    --bg-progress: #f2f3f7;
    --bg-input: #f2f3f7;
    --bg-input-focus: #f0f0f0;
    --bg-hire: #f9bf3f;
    --bg-award: #f9f9f9;
    --bg-skill: #f9f9f9;
    --bg-project: #fff;
    --bg-selection: #2c98f0;
    --bg-loader: #fff;
    --bg-panel-border: #e6e6e6;
    --bg-project-icon: rgba(255, 255, 255, 0.5);
    --bg-overlay: rgba(0, 0, 0, 0.4);
    --bg-counter-overlay: rgba(0, 0, 0, 0.4);

    /* Text */
    --text-body: rgba(0, 0, 0, 0.7);
    --text-heading: #000;
    --text-sidebar: rgba(0, 0, 0, 0.7);
    --text-logo: #000;
    --text-selection: #fff;
    --text-meta: #999999;
    --text-panel-collapsed: #333333;
    --text-project-icon: #333333;
    --text-project-subtitle: #333333;
    --text-placeholder: #999;
    --text-figure: #b3b3b3;
    --text-social: #000;
    --text-work-menu: #000;
    --text-pagination: #000;
    --text-position-gold: #f6c14d;
    --text-position-silver: #6e6e6ef8;
    --text-position-bronze: #d75218;

    /* Accent */
    --color-link: #2c98f0;
    --color-nav-toggle: #000;
    --color-slider-link: rgba(44, 152, 240, 0.8);
    --color-slider-link-border: rgba(44, 152, 240, 0.7);

    /* Shadows */
    --shadow-card: rgba(0, 0, 0, 0.17);
    --shadow-popup: rgba(0, 0, 0, 0.1);
}

[data-theme="dark"] {
    --bg-body: #1a1a2e;
    --bg-sidebar: #16213e;
    --bg-section: #1a1a2e;
    --bg-section-alt: #16213e;
    --bg-card: #16213e;
    --bg-panel: #16213e;
    --bg-timeline: #16213e;
    --bg-service: #16213e;
    --bg-progress: #16213e;
    --bg-input: #16213e;
    --bg-input-focus: #0f3460;
    --bg-hire: #f9bf3f;
    --bg-award: #16213e;
    --bg-skill: #16213e;
    --bg-project: #16213e;
    --bg-selection: #5dade2;
    --bg-loader: #1a1a2e;
    --bg-panel-border: rgba(255, 255, 255, 0.1);
    --bg-project-icon: rgba(0, 0, 0, 0.3);
    --bg-overlay: rgba(0, 0, 0, 0.6);
    --bg-counter-overlay: rgba(0, 0, 0, 0.5);

    --text-body: rgba(255, 255, 255, 0.7);
    --text-heading: #e0e0e0;
    --text-sidebar: rgba(255, 255, 255, 0.8);
    --text-logo: #fff;
    --text-selection: #1a1a2e;
    --text-meta: rgba(255, 255, 255, 0.4);
    --text-panel-collapsed: #e0e0e0;
    --text-project-icon: #fff;
    --text-project-subtitle: rgba(255, 255, 255, 0.7);
    --text-placeholder: rgba(255, 255, 255, 0.3);
    --text-figure: rgba(255, 255, 255, 0.5);
    --text-social: rgba(255, 255, 255, 0.7);
    --text-work-menu: #e0e0e0;
    --text-pagination: #e0e0e0;
    --text-position-gold: #f9bf3f;
    --text-position-silver: rgba(255, 255, 255, 0.6);
    --text-position-bronze: #e8751a;

    --color-link: #5dade2;
    --color-nav-toggle: #fff;
    --color-slider-link: rgba(93, 173, 226, 0.8);
    --color-slider-link-border: rgba(93, 173, 226, 0.7);

    --shadow-card: rgba(0, 0, 0, 0.3);
    --shadow-popup: rgba(0, 0, 0, 0.3);
}
```

### JavaScript Logic
```javascript
// Theme detection and toggle
(function() {
    const toggle = document.getElementById('theme-toggle');
    const html = document.documentElement;
    const stored = localStorage.getItem('theme');
    
    // Set initial theme
    if (stored) {
        html.setAttribute('data-theme', stored);
    } else if (window.matchMedia('(prefers-color-scheme: dark)').matches) {
        html.setAttribute('data-theme', 'dark');
    }
    
    // Toggle handler
    toggle.addEventListener('click', function() {
        const current = html.getAttribute('data-theme');
        const next = current === 'dark' ? 'light' : 'dark';
        html.setAttribute('data-theme', next);
        localStorage.setItem('theme', next);
    });
    
    // Listen for system preference changes
    window.matchMedia('(prefers-color-scheme: dark)').addEventListener('change', function(e) {
        if (!localStorage.getItem('theme')) {
            html.setAttribute('data-theme', e.matches ? 'dark' : 'light');
        }
    });
})();
```

---

## Estimated Scope (Updated)
- **CSS variables**: ~55 variables x 2 themes = 110 lines
- **Color migrations**: ~200 color replacements across style.css
- **HTML**: 1 toggle button element
- **JS**: ~40 lines of toggle logic
- **Total new code**: ~350 lines
- **Files touched**: 3 (style.css, index.html, main.js)

## Additional Edge Cases Covered

The deep audit revealed several edge cases that the initial plan missed:

1. **Panel borders** (`#e6e6e6`) - Need dark mode border color
2. **Project overlay icons** - Icon backgrounds and text colors on hover
3. **Project hover states** - Overlay darkness and text colors
4. **Counter section** - Icon backgrounds and overlay opacity
5. **Social icons** - Text color in sidebar footer
6. **Work menu** - Filter menu text colors
7. **Pagination** - Link colors (for blog section if uncommented)
8. **Card shadows** - Shadow colors need to be darker in dark mode
9. **Slider links** - Hero section link colors
10. **Position colors** - Award medal colors (gold/silver/bronze)
11. **Popup shadows** - Form success popup shadow

## Risks & Mitigations

| Risk | Impact | Mitigation |
|------|--------|------------|
| Missing color values | Inconsistent theme | Deep audit completed, all 200+ colors mapped |
| Low contrast in dark mode | Accessibility issue | WCAG AA compliance check in Phase 4 |
| Smooth transition flicker | Poor UX | Add `transition` property to all themed elements |
| Browser compatibility | Some users can't use | CSS variables supported in all modern browsers (IE11 excluded) |
| localStorage not available | Theme not persisted | Fallback to system preference or default light mode |

## Transition Strategy

To ensure smooth theme switching without flicker:

1. Add `transition: background-color 0.3s ease, color 0.3s ease, border-color 0.3s ease` to all themed elements
2. Apply theme before DOM renders (in `<head>` script) to prevent flash
3. Use `will-change: background-color` on major sections for performance

```javascript
// Add to <head> to prevent flash
(function() {
    const stored = localStorage.getItem('theme');
    const prefersDark = window.matchMedia('(prefers-color-scheme: dark)').matches;
    const theme = stored || (prefersDark ? 'dark' : 'light');
    document.documentElement.setAttribute('data-theme', theme);
})();
```