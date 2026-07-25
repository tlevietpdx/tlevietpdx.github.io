# Dark Mode Discrepancies Audit

## Overview
This document quantifies all remaining discrepancies in the dark mode implementation where colors are still hardcoded instead of using CSS variables, causing poor contrast or inconsistent theming.

---

## Category 1: Timeline Icon Colors (5 hardcoded colors)

**Location**: [`css/style.css:729-736`](css/style.css:729)

| Line | Element | Hardcoded Color | Issue |
|------|---------|-----------------|-------|
| 730 | `.timeline-icon.color-2` | `#ec5453` (red) | Static color, doesn't adapt to dark mode |
| 732 | `.timeline-icon.color-3` | `#f9bf3f` (gold) | Static color, doesn't adapt to dark mode |
| 734 | `.timeline-icon.color-4` | `#a84cb8` (purple) | Static color, doesn't adapt to dark mode |
| 736 | `.timeline-icon.color-5` | `#2fa499` (teal) | Static color, doesn't adapt to dark mode |

**Impact**: Low - These are accent colors for timeline entries. They remain the same in both modes which is acceptable for brand colors, but could benefit from slight dark mode adjustments for better harmony.

---

## Category 2: Services Border/Icon Colors (8 hardcoded colors)

**Location**: [`css/style.css:803-906`](css/style.css:803)

### Services .color-2 through .color-6 (Border Bottom + Icon2)
| Line | Element | Hardcoded Color | Issue |
|------|---------|-----------------|-------|
| 804 | `.services.color-2` border | `#ec5453` | Static border color |
| 806 | `.services.color-2 .icon2 i` | `#ec5453` | Static icon color |
| 808 | `.services.color-3` border | `#f9bf3f` | Static border color |
| 810 | `.services.color-3 .icon2 i` | `#f9bf3f` | Static icon color |
| 812 | `.services.color-4` border | `#a84cb8` | Static border color |
| 814 | `.services.color-4 .icon2 i` | `#a84cb8` | Static icon color |
| 816 | `.services.color-5` border | `#2fa499` | Static border color |
| 818 | `.services.color-6` border | `#4054b2` | Static border color |

### Services .icon Background/Borders (12 hardcoded colors)
| Line | Element | Hardcoded Color | Issue |
|------|---------|-----------------|-------|
| 878 | `.services.color-2 .icon` bg | `#ec5453` | Static background |
| 880 | `.services.color-2 .icon:before` border | `#ec5453` | Static border |
| 882 | `.services.color-2 .icon:after` border | `#ec5453` | Static border |
| 884 | `.services.color-3 .icon` bg | `#f9bf3f` | Static background |
| 886 | `.services.color-3 .icon:before` border | `#f9bf3f` | Static border |
| 888 | `.services.color-3 .icon:after` border | `#f9bf3f` | Static border |
| 890 | `.services.color-4 .icon` bg | `#a84cb8` | Static background |
| 892 | `.services.color-4 .icon:before` border | `#a84cb8` | Static border |
| 894 | `.services.color-4 .icon:after` border | `#a84cb8` | Static border |
| 896 | `.services.color-5 .icon` bg | `#2fa499` | Static background |
| 898 | `.services.color-5 .icon:before` border | `#2fa499` | Static border |
| 900 | `.services.color-5 .icon:after` border | `#2fa499` | Static border |
| 902 | `.services.color-6 .icon` bg | `#4054b2` | Static background |
| 904 | `.services.color-6 .icon:before` border | `#4054b2` | Static border |
| 906 | `.services.color-6 .icon:after` border | `#4054b2` | Static border |

**Impact**: Medium - Service cards have colored icons that don't adapt. These are brand/accent colors so keeping them static is acceptable, but the text ON these colored backgrounds needs verification for contrast.

---

## Category 3: Progress Bar Colors (12 hardcoded colors)

**Location**: [`css/style.css:951-978`](css/style.css:951)

| Line | Element | Hardcoded Color | Issue |
|------|---------|-----------------|-------|
| 952 | `.progress-bar.color-1` bg | `#2c98f0` | Static bar color |
| 954 | `.progress-bar.color-1:after` bg | `#2c98f0` | Static dot color |
| 956 | `.progress-bar.color-1 span` text | `#2c98f0` | Static text color |
| 958 | `.progress-bar.color-2` bg | `#ec5453` | Static bar color |
| 960 | `.progress-bar.color-2:after` bg | `#ec5453` | Static dot color |
| 962 | `.progress-bar.color-2 span` text | `#ec5453` | Static text color |
| 964 | `.progress-bar.color-3` bg | `#f9bf3f` | Static bar color |
| 966 | `.progress-bar.color-3:after` bg | `#f9bf3f` | Static dot color |
| 968 | `.progress-bar.color-3 span` text | `#f9bf3f` | Static text color |
| 970 | `.progress-bar.color-4` bg | `#a84cb8` | Static bar color |
| 972 | `.progress-bar.color-4:after` bg | `#a84cb8` | Static dot color |
| 974 | `.progress-bar.color-4 span` text | `#a84cb8` | Static text color |

**Impact**: High - Progress bar text colors (`span`) on dark background have POOR CONTRAST. The colored text on dark background may not meet WCAG AA contrast requirements.

---

## Category 4: Bootstrap Button Colors (36 hardcoded colors)

**Location**: [`css/style.css:1379-1437`](css/style.css:1379)

### .btn-success
| Line | Element | Hardcoded Color | Issue |
|------|---------|-----------------|-------|
| 1380 | `.btn-success` bg | `#5cb85c` | Static green |
| 1381 | `.btn-success` text | `#fff` | White text on green - OK |
| 1382 | `.btn-success` border | `#5cb85c` | Static green |
| 1384 | `.btn-success:hover` bg | `#4cae4c` | Static darker green |
| 1385 | `.btn-success:hover` border | `#4cae4c` | Static darker green |
| 1388 | `.btn-success.btn-outline` text | `#5cb85c` | Green text on transparent - POOR contrast on dark bg |
| 1389 | `.btn-success.btn-outline` border | `#5cb85c` | Static green |
| 1391 | `.btn-success.btn-outline:hover` bg | `#5cb85c` | Static green |
| 1392 | `.btn-success.btn-outline:hover` text | `#fff` | White on green - OK |

### .btn-info
| Line | Element | Hardcoded Color | Issue |
|------|---------|-----------------|-------|
| 1395 | `.btn-info` bg | `#5bc0de` | Static blue |
| 1396 | `.btn-info` text | `#fff` | White text on blue - OK |
| 1397 | `.btn-info` border | `#5bc0de` | Static blue |
| 1399 | `.btn-info:hover` bg | `#46b8da` | Static darker blue |
| 1400 | `.btn-info:hover` border | `#46b8da` | Static darker blue |
| 1403 | `.btn-info.btn-outline` text | `#5bc0de` | Blue text on transparent - POOR contrast on dark bg |
| 1404 | `.btn-info.btn-outline` border | `#5bc0de` | Static blue |
| 1406 | `.btn-info.btn-outline:hover` bg | `#5bc0de` | Static blue |
| 1407 | `.btn-info.btn-outline:hover` text | `#fff` | White on blue - OK |

### .btn-warning
| Line | Element | Hardcoded Color | Issue |
|------|---------|-----------------|-------|
| 1410 | `.btn-warning` bg | `#f0ad4e` | Static orange |
| 1411 | `.btn-warning` text | `#fff` | White text on orange - LOW contrast |
| 1412 | `.btn-warning` border | `#f0ad4e` | Static orange |
| 1414 | `.btn-warning:hover` bg | `#eea236` | Static darker orange |
| 1415 | `.btn-warning:hover` border | `#eea236` | Static darker orange |
| 1418 | `.btn-warning.btn-outline` text | `#f0ad4e` | Orange text on transparent - POOR contrast on dark bg |
| 1419 | `.btn-warning.btn-outline` border | `#f0ad4e` | Static orange |
| 1421 | `.btn-warning.btn-outline:hover` bg | `#f0ad4e` | Static orange |
| 1422 | `.btn-warning.btn-outline:hover` text | `#fff` | White on orange - LOW contrast |

### .btn-danger
| Line | Element | Hardcoded Color | Issue |
|------|---------|-----------------|-------|
| 1425 | `.btn-danger` bg | `#d9534f` | Static red |
| 1426 | `.btn-danger` text | `#fff` | White text on red - OK |
| 1427 | `.btn-danger` border | `#d9534f` | Static red |
| 1429 | `.btn-danger:hover` bg | `#d43f3a` | Static darker red |
| 1430 | `.btn-danger:hover` border | `#d43f3a` | Static darker red |
| 1433 | `.btn-danger.btn-outline` text | `#d9534f` | Red text on transparent - POOR contrast on dark bg |
| 1434 | `.btn-danger.btn-outline` border | `#d9534f` | Static red |
| 1436 | `.btn-danger.btn-outline:hover` bg | `#d9534f` | Static red |
| 1437 | `.btn-danger.btn-outline:hover` text | `#fff` | White on red - OK |

**Impact**: High - Outline buttons have colored text on transparent background. In dark mode, the colored text becomes invisible or very hard to read. `.btn-warning` has low contrast even in light mode.

---

## Category 5: Image/Background Issues

### Hero Section Background Images
**Location**: [`index.html:115-129`](index.html:115)

- Background images (`img_bg_1.png`, `img_bg_2.png`) have overlay text that may have contrast issues
- Text overlay uses white text with dark overlay (`rgba(0,0,0,0.4)`) which should be OK
- Need to verify the overlay opacity is sufficient in both modes

### Project Images with Overlay
**Location**: [`css/style.css:1105`](css/style.css:1105)

- Project overlay uses `var(--bg-overlay-dark)` which is good
- White text on colored overlay should be OK

---

## Category 6: Form Input Placeholder Text

**Location**: [`css/style.css`](css/style.css)

- Placeholder text uses `--text-placeholder` variable which is set correctly
- Need to verify visibility in dark mode

---

## Summary of Issues by Priority

### Critical (Must Fix)
1. **Progress Bar Text Colors** (12 colors) - Colored text on dark background has poor contrast
2. **Outline Button Text Colors** (8 colors) - Colored text on transparent is invisible on dark background
3. **Button Warning Contrast** - `#f0ad4e` with `#fff` text fails WCAG AA

### High (Should Fix)
4. **Timeline Icon Colors** (4 colors) - Could adapt for better dark mode harmony
5. **Service Icon Colors** (20 colors) - Brand colors, static is acceptable but could enhance

### Medium (Nice to Have)
6. **Hero Section Overlay** - Verify overlay opacity is sufficient
7. **Form Placeholders** - Verify visibility

---

## Recommended Approach

### Option A: Full Variable Migration (Comprehensive)
- Create dark-mode variants for ALL accent colors
- Total new variables needed: ~30
- Total color migrations needed: ~70

### Option B: Targeted Contrast Fixes (Minimal)
- Fix only the critical contrast issues (progress bars, outline buttons)
- Keep brand/accent colors static
- Total new variables needed: ~5
- Total color migrations needed: ~20

### Option C: Hybrid Approach (Recommended)
- Fix critical contrast issues
- Add dark-mode adjustments for progress bars
- Keep brand colors static but ensure text ON them has good contrast
- Total new variables needed: ~10
- Total color migrations needed: ~35

---

## Estimated Effort

| Task | Lines Affected | Complexity |
|------|----------------|------------|
| Add new CSS variables | ~30 lines | Low |
| Migrate progress bar colors | ~12 lines | Low |
| Migrate button colors | ~36 lines | Medium |
| Migrate service colors | ~20 lines | Low |
| Migrate timeline colors | ~4 lines | Low |
| Test contrast ratios | N/A | Medium |
| **Total** | **~102 lines** | **Medium** |

---

## Next Steps

1. Choose approach (A, B, or C)
2. Define new CSS variables for dark mode
3. Migrate hardcoded colors to variables
4. Test WCAG AA contrast compliance
5. Verify visual appearance in both modes