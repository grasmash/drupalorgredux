# Drupal Logo SVG Findings

## 1. Current Usage in index.html

The page uses a very simplified single-path drop at two locations (header logo and center node in diagram):

```
M16 0S0 16 0 28c0 8.8 7.2 16 16 16s16-7.2 16-16C32 16 16 0 16 0z
```

This is a basic teardrop shape with no internal detail -- it lacks the "Community Drop" and "Individual Drop" elements that are part of the official brand.

---

## 2. Official Detailed Drop Logo -- Available Locally

A much more detailed, official Drupal Drop SVG exists at:

```
assets/logos/Original/Drupal Drop_Blue.svg
```

This is an Adobe Illustrator export (viewBox `0 0 1000 1000`) containing a single `<path>` with the full multi-element drop design. It includes:

- **The Greater Drop** (outer drop silhouette)
- **The Community Drop** (middle teardrop cutout)
- **The Individual Drop** (small inner element, upper-left area)

All three sub-shapes are combined into one compound path. Color: `#009CDE` (Drupal Blue).

**Other color variants available (drop only, no wordmark):**

| File | Color |
|------|-------|
| `assets/logos/Original/Drupal Drop_Blue.svg` | #009CDE |
| `assets/logos/Original/Drupal Drop_Navy.svg` | #12285F |
| `assets/logos/Original/Drupal Drop_White.svg` | #FFFFFF |
| `assets/logos/Original/Drupal Drop_Black.svg` | #000000 |

---

## 3. Horizontal and Vertical Drupal Logos (Drop + Wordmark)

Both layouts are available with the "Drupal" wordmark (set in ZT Gatha font, rendered as paths). Each contains the detailed drop plus the wordmark plus a small "TM" superscript.

### Horizontal (drop beside text)

Path: `assets/logos/Original/Drupal Logo_Horizontal_Blue.svg`
- viewBox: `0 0 515.7 179.7`
- Contains: detailed drop paths + "Drupal" wordmark paths + "TM" paths
- Color variants: Blue, Navy, White, Black

### Vertical (drop above text)

Path: `assets/logos/Original/Drupal Logo_Vertical_Blue.svg`
- viewBox: `0 0 349.5 291.1`
- Contains: same detailed drop + wordmark below + "TM"
- Color variants: Blue, Navy, White, Black

---

## 4. Drupal CMS Product Logos -- Available Locally

Full set of Drupal CMS product logos exists at:

```
assets/product-logos/Original/
```

### With Wordmark (Primary usage)

| File | Layout | Color |
|------|--------|-------|
| `Drupal Product Logo-CMS-Horizontal-Wordmark-Blue.svg` | Horizontal | Blue |
| `Drupal Product Logo-CMS-Horizontal-Wordmark-White.svg` | Horizontal | White |
| `Drupal Product Logo-CMS-Vertical-Wordmark-Blue.svg` | Vertical | Blue |
| `Drupal Product Logo-CMS-Vertical-Wordmark-White.svg` | Vertical | White |

The horizontal wordmark version (`*-Horizontal-Wordmark-Blue.svg`, viewBox `0 0 823 201`) contains:
- The detailed Drupal drop (same compound path as the standalone drop)
- "Drupal" wordmark paths
- "TM" mark
- "CMS" text rendered as separate paths (large, bold letters)

### Without Wordmark (Secondary, permission required)

| File | Layout | Color |
|------|--------|-------|
| `Drupal Product Logo-CMS-Horizontal-No Wordmark-Blue.svg` | Horizontal | Blue |
| `Drupal Product Logo-CMS-Horizontal-No Wordmark-White.svg` | Horizontal | White |
| `Drupal Product Logo-CMS-Vertical-No Wordmark-Blue.svg` | Vertical | Blue |
| `Drupal Product Logo-CMS-Vertical-No Wordmark-White.svg` | Vertical | White |

---

## 5. Drupal CMS Logo in Downloads (from drupal-cms project)

An additional Drupal CMS logo SVG was found at:

```
~/Downloads/drupal-cms 2/web/profiles/drupal_cms_installer/images/drupal-cms-logo.svg
```

This is a compact version (254x71, no XML preamble) containing the drop + "Drupal" wordmark + "CMS" text. Uses `#009BDD` (very close to but not exactly `#009CDE`). This appears to be the installer/product logo used within the Drupal CMS application itself.

---

## 6. Legacy "Evergreen" Druplicon Logo (drupalorg site)

An older-style Drupal logo library exists at:

```
~/Sites/drupalorg/playground/assets/Drupal Logo Library/RGB/
```

Contains:
- `Evergreen logo/EL_blue_RGB.svg` -- The classic Druplicon-style drop (single raindrop with internal cutouts for face-like shapes). viewBox 186x243. This is the **previous generation** logo, not the current brand.
- `Wordmark 1/` and `Wordmark 2/` variants (blue and white)

This is NOT the current official brand logo. The current brand uses the multi-element drop described in sections 2-4 above.

---

## 7. Summary and Recommendations

| Need | Best Source | Path |
|------|-----------|------|
| Detailed drop (icon only) | Official asset | `assets/logos/Original/Drupal Drop_Blue.svg` |
| Drupal logo horizontal | Official asset | `assets/logos/Original/Drupal Logo_Horizontal_Blue.svg` |
| Drupal logo vertical | Official asset | `assets/logos/Original/Drupal Logo_Vertical_Blue.svg` |
| Drupal CMS logo horizontal | Official asset | `assets/product-logos/Original/Drupal Product Logo-CMS-Horizontal-Wordmark-Blue.svg` |
| Drupal CMS logo vertical | Official asset | `assets/product-logos/Original/Drupal Product Logo-CMS-Vertical-Wordmark-Blue.svg` |

**The simplified drop path currently in `index.html` should be replaced with the official detailed drop from `assets/logos/Original/Drupal Drop_Blue.svg`** to properly represent the brand. The official drop contains three nested elements (Greater Drop, Community Drop, Individual Drop) as specified in the brand guidelines.

All official SVGs use `#009CDE` as Drupal Blue. The brand guidelines document color variants (Navy `#12285F`, White `#FFFFFF`, Black `#000000`) with rules for which to use on which backgrounds.
