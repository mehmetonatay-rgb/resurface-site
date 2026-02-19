# Resurface App — UI Specification for Website Mockups

> Extracted from the Resurface iOS app codebase (Expo 54 + React Native).
> All values are **light mode** unless noted. Font is **system font (SF Pro)** throughout.

---

## 1. Design Tokens

### Colors

```json
{
  "colors": {
    "primary": "#FF8C00",
    "primaryLight": "#FFB347",
    "primaryDark": "#E67E00",
    "accent": "#2563EB",

    "background": "#FAFAF8",
    "backgroundSecondary": "#F5F0E8",
    "backgroundTertiary": "#EDE7DB",
    "surface": "#FFFFFF",
    "surfaceElevated": "#FFFFFF",

    "text": "#111110",
    "textSecondary": "#555550",
    "textTertiary": "#8A8A82",
    "textInverse": "#FFFFFF",

    "success": "#22C55E",
    "warning": "#FF9500",
    "error": "#FF3B30",
    "info": "#5AC8FA",

    "border": "rgba(0,0,0,0.06)",
    "borderLight": "#F0E8DA",
    "divider": "#DDD3C2",
    "shadow": "rgba(139,90,43,0.08)",
    "overlay": "rgba(45,35,25,0.4)",

    "glass": "rgba(251,248,243,0.85)",
    "glassLight": "rgba(251,248,243,0.95)",
    "glassBorder": "rgba(232,223,208,0.5)",

    "cardBackground": "#FFFFFF",
    "cardBorder": "#EDE7DB",

    "tabBarBackground": "#FBF8F3",
    "tabBarActive": "#FF8C00",
    "tabBarInactive": "#B8AD9E",

    "proGold": "#FFD700"
  }
}
```

### Category Colors

```json
{
  "Tech": "#6366F1",
  "Business": "#10B981",
  "Health": "#F43F5E",
  "Entertainment": "#FF8C00",
  "Education": "#8B5CF6",
  "News": "#3B82F6",
  "Creative": "#EC4899",
  "Personal Development": "#14B8A6",
  "Other": "#8B7E6A"
}
```

### Dark Mode Colors (for reference)

```json
{
  "background": "#1A1612",
  "backgroundSecondary": "#252019",
  "surface": "#252019",
  "text": "#F5F0E8",
  "textSecondary": "#B8AD9E",
  "primary": "#4A6FA5",
  "primaryLight": "#6B8FC0",
  "tabBarBackground": "#1A1612",
  "tabBarActive": "#4A6FA5",
  "cardBackground": "#252019",
  "cardBorder": "#3D3428"
}
```

### Typography (Apple HIG scale, SF Pro)

| Name         | Size | Weight | Line Height | Letter Spacing |
|-------------|------|--------|-------------|----------------|
| display     | 40   | 800    | 48          | -1             |
| largeTitle  | 34   | 700    | 41          | -0.5           |
| title1      | 28   | 700    | 34          | -0.3           |
| title2      | 22   | 700    | 28          | -0.2           |
| title3      | 20   | 600    | 25          | —              |
| headline    | 17   | 600    | 22          | —              |
| body        | 17   | 400    | 22          | —              |
| callout     | 16   | 400    | 21          | —              |
| subhead     | 15   | 500    | 20          | —              |
| footnote    | 13   | 400    | 18          | —              |
| caption1    | 12   | 500    | 16          | —              |
| caption2    | 11   | 500    | 14          | —              |

### Spacing (4pt base)

| Token | Value |
|-------|-------|
| xxs   | 2     |
| xs    | 4     |
| sm    | 8     |
| md    | 12    |
| base  | 16    |
| lg    | 20    |
| xl    | 24    |
| xxl   | 32    |
| xxxl  | 48    |

### Border Radius

| Token   | Value |
|---------|-------|
| xs      | 6     |
| sm      | 12    |
| md      | 16    |
| lg      | 20    |
| xl      | 24    |
| xxl     | 28    |
| xxxl    | 32    |
| full    | 9999  |

### Shadows

| Preset | Color   | Offset   | Opacity | Radius |
|--------|---------|----------|---------|--------|
| sm     | #5C3D2E | 0, 1     | 0.04    | 2      |
| md     | #5C3D2E | 0, 2     | 0.06    | 8      |
| lg     | #5C3D2E | 0, 4     | 0.10    | 16     |
| xl     | #5C3D2E | 0, 8     | 0.14    | 24     |
| card   | #000    | 0, 1     | 0.04    | 8      |
| hero   | #000    | 0, 4     | 0.12    | 24     |

### Illustration Palette

```json
{
  "serenity": "#E8E4DF",
  "wisdom": "#C4B8A8",
  "focus": "#9E9282",
  "clarity": "#FBF8F3",
  "depth": "#2D2319",
  "accent": "#FF8C00"
}
```

---

## 2. App Logo

- **Source**: `assets/images/icon.png` (1080x1080 RGBA PNG)
- **Shape**: Rounded-square with orange background and upward arrow/mountain symbol
- **No SVG exists** in the codebase
- **Splash screen**: Orange background (#FF8C00) with centered icon
- **Exports provided**:
  - `logo.png` — 512x512
  - `logo-small.png` — 64x64

---

## 3. Home Screen (Today Tab)

### Greeting Section
```
Morning, reader       [Avatar Button]
```
- Time-based greeting: "Morning" (< 12), "Afternoon" (< 17), "Evening" (>= 17)
- User name defaults to "reader" if not set
- Name portion is colored `#FF8C00` (primary)
- Font: 32px, weight 700, letter-spacing -0.6
- Avatar button: 42x42px circle, person icon (19px, primary color), light gray bg

### Progress Bar (Linear)
```
[████████░░░░░░░░] 5/10
5 done · 5 to go
```
- Thin horizontal bar (5px height, 2px radius)
- Fill gradient: `#FF8C00` → `#FFB040`
- Animation: 800ms ease-out, 300ms delay
- Fraction label: 12px weight 600, textSecondary
- Subtext: 13px, textTertiary

### Featured Hero Card
```
┌─────────────────────────────────────────┐
│  [TECH]          [Medium · 8 min]       │
│                                         │
│        Full Background Image            │
│        (280px height)                   │
│                                         │
│  ┌─ Frosted Glass Panel ──────────────┐ │
│  │ Article Title (max 3 lines)        │ │
│  │ [      Read Now      ]             │ │
│  └────────────────────────────────────┘ │
└─────────────────────────────────────────┘
```
- Height: 280px, borderRadius: 20px
- Category badge: uppercase, 11px bold, primary bg, white text, pill shape
- Source badge: "Source · X min", dark semi-transparent bg `rgba(0,0,0,0.65)`
- Frosted glass: BlurView intensity 40, 1px semi-transparent white border
- Title: 20px bold, white, line-height 24, letter-spacing -0.4
- "Read Now" button: primary bg, 12px padding, 14px bold white text, 12px radius
- Selects shortest pending item

### Up Next Section
```
Up Next                            See all →
┌──────────┐  ┌──────────┐  ┌──────────┐
│ Thumbnail │  │ Thumbnail │  │ Thumbnail │
│ [8 min]   │  │ [5 min]   │  │ [12 min]  │
├──────────┤  ├──────────┤  ├──────────┤
│ Title     │  │ Title     │  │ Title     │
│ Src · Cat │  │ Src · Cat │  │ Src · Cat │
└──────────┘  └──────────┘  └──────────┘
```
- Horizontal scrolling FlatList
- Card width: ~50% screen (2-column responsive)
- Thumbnail: 110px height, 14px radius
- Time badge: bottom-right, white pill `rgba(255,255,255,0.92)`, 11px bold
- No thumbnail fallback: gradient bg with source icon (28px)
- Title: 14px weight 600, max 2 lines
- Meta: 12px, textTertiary, "Source · Category"
- Max 8 items shown

### Creations Section
```
Your Creations                     See all →
┌───────────┐  ┌───────────┐
│ [PODCAST] │  │ [SUMMARY] │
│ Thumbnail │  │ Thumbnail │
├───────────┤  ├───────────┤
│ Title     │  │ Title     │
│ 3 min     │  │ 2 min read│
└───────────┘  └───────────┘
```
- 2-column grid, 8px gap
- Thumbnail: 95px height, 16px radius
- Type badge: top-left, uppercase 10px bold, pill
  - Podcast: `rgba(255,140,0,0.9)`
  - Summary: `rgba(34,197,94,0.9)`
  - Briefing: `rgba(139,92,246,0.9)`
  - Recap: `rgba(99,102,241,0.9)`
- Title: 13px weight 600, max 2 lines
- Subtitle: 11px, textTertiary
- Max 4 cards shown

### Empty State
- Shown when 0 items and 0 creations
- Custom `<HomeEmptyState />` component
- Floating callout: "Or paste a link here"
- Pulsing add button with animated ring (scale 1.0 → 1.15, 2s cycle)

### Weekly Recap Card (Sundays only)
- Pro version: shows current recap
- Free version: locked card with completed count from past 7 days

---

## 4. Library Screen

### Header
- Title: "Library" (34px, weight 700, letter-spacing -0.8)
- Subtitle: "{count} saved · {time} to go" (queue) or "{count} completed · {time} read" (archive)
- Two circular action buttons (42x42px, borderRadius 21):
  - Search icon (search-outline)
  - Filter icon (funnel-outline)
  - Both show orange dot indicator when active

### Search Bar (togglable)
- Placeholder: "Search your library..."
- Search icon on left, clear button (X) when text entered
- Hidden by default, slides in from top

### Segmented Control (Queue / Archive)
```
┌──────────────────────────────────┐
│  [ Queue (12) ]  [ Archive (5) ] │
└──────────────────────────────────┘
```
- Rounded pill container (20px radius) with 4px padding
- Background: secondary color
- Animated white indicator slides between tabs (250ms cubic ease)
- Count badges next to labels, primary color when selected

### Advanced Filters (Modal)

| Category        | Options                                                |
|-----------------|--------------------------------------------------------|
| Sort            | Date Added, Reading Time, Type, Title (toggle asc/desc) |
| Content Type    | Article, Video, Podcast, Newsletter, Other             |
| Platform        | YouTube, Twitter, Reddit, TikTok, HackerNews, GitHub, Instagram, Newsletter |
| Reading Length  | < 5m, 5-15m, 15-30m, 30m+                            |
| Date Added      | Today, This Week, This Month                          |
| Tags            | Up to 15 dynamic tags with # prefix                   |

- Filter chips: selected = `#FF8C00`, unselected = light gray
- Instant-apply with haptic feedback
- "Done" and "Clear" buttons in header

### Content Card (`EnhancedContentCard`)
```
┌─ 3px Category Accent Bar ──────────────────────┐
│                                                  │
│  ┌──────────┐  [TECH]                           │
│  │Thumbnail │  Article Title (max 2 lines)      │
│  │ 90x90    │  Medium · 7 min                   │
│  │ [src]    │                                    │
│  └──────────┘                                    │
└──────────────────────────────────────────────────┘
```
- 3px vertical category color bar on left edge
- Thumbnail: 90x90px, 14px radius
- Source badge: platform icon (22x22, dark bg) at thumbnail bottom-right
- Category chip: uppercase, category color bg at 10% opacity
- Title: 15.5px, weight 600, max 2 lines
- Meta: "Source · X min", 13px, textSecondary

### Queue Grouping (Section Headers)
- **TODAY** | 3 items
- **THIS WEEK** | 5 items
- **EARLIER** | 12 items
- Uppercase labels with horizontal rule and item count

### Empty States

**Queue empty:**
- Title: "Your queue is empty"
- Subtitle: "Save articles, videos, and more to start building your library"
- CTA: "Add Content" button

**Archive empty:**
- Title: "Nothing archived yet"
- Subtitle: "Completed items will appear here"

**No search results:**
- Icon: bookmark-outline (queue) or archive-outline (archive)
- Title: "No results found"
- Subtitle: "Try different keywords or clear your filters"

### Selection Mode
- Long press activates batch mode
- Checkbox: 26x26px rounded
- Header: "Cancel" | "{count} Selected" | "Select All"
- Batch actions: Archive, Delete, Tag, Cancel

---

## 5. Audio / Soundscape Player

> This is a **focus atmosphere** player (ambient loops), not a podcast player.

### Layout: Bottom Sheet Modal
- Border radius: 24px top corners
- Overlay: `rgba(0,0,0,0.4)`
- Handle bar: 40x4px, 2px radius
- Header: "Focus Atmosphere" (20px, weight 700) + close button

### Visualizer (Now Playing)
- 56x56px rounded square (16px radius)
- 4 animated waveform bars (white, 3px gap)
- Background gradient per soundscape:
  - Lo-Fi: `#8B5CF6 → #6366F1`
  - Binaural: `#6366F1 → #0EA5E9`
  - Rain: `#0EA5E9 → #14B8A6`
  - Forest: `#10B981 → #14B8A6`
  - Ocean: `#14B8A6 → #0EA5E9`
  - Fireplace: `#EF4444 → #F97316`
  - Silence: `#4B5563 → #374151`

### Soundscape Grid (Horizontal Scroll)
7 options, each 100x100px cards (16px radius):
1. **Silence** — "Pure focus, no distractions" (volume-mute)
2. **Lo-Fi Beats** — "Chill beats for concentration" (musical-notes)
3. **Binaural Beats** — "Brainwave entrainment for deep focus" (pulse)
4. **Rainy Window** — "Cozy rain sounds on glass" (rainy)
5. **Forest Ambience** — "Birds and rustling leaves" (leaf)
6. **Ocean Waves** — "Gentle waves on shore" (water)
7. **Crackling Fire** — "Warm fireplace ambience" (flame)

- Selected: gradient bg + 2px colored border + checkmark badge (20x20)
- Unselected: gray bg + 1px border

### Controls
- **Play/Pause**: 48x48px circle, soundscape color
- **Volume Slider**: 6px track, gradient fill, 24x24 thumb
- **Smart Fade-Out**: toggle switch + 4 duration options (3m, 5m, 10m, 15m)
- **Apply Button**: full-width, 16px padding, 16px radius, soundscape color bg

---

## 6. Paywall Screen

### Background
- LinearGradient: `#FFF3E0 → #FAFAF8` (light mode)

### Header
```
       [X close]

     ┌────────┐
     │  ICON  │ [PRO]
     │ 86x86  │
     └────────┘

  Never let a saved article
       go to waste.

 Try free for 3 days. Cancel anytime.
```
- App icon: 86x86px, 22px radius, heavy shadow
- PRO badge: absolute bottom-right, white bg, primary text, 9.5px bold
- Headline: 27px, weight 700, -0.3 letter-spacing, center
  - "saved article" highlighted in `#FF8C00`
- Trial subtext: 15px, textTertiary, center

### Feature List (4 items)
Each row: orange circle checkmark (26x26) + feature text (16px, weight 500)

1. "Turn any article into a podcast"
2. "AI summaries and themed briefings"
3. "Save unlimited articles, videos, and threads"
4. "Back up your library to the cloud"

Dividers: 1px, `rgba(232,223,208,0.4)`, 36px left margin

### Pricing Cards
```
┌─ SAVE 62% ────────────────┐  ┌────────────────────────┐
│                            │  │                        │
│  Yearly          (●)       │  │  Weekly          ( )   │
│                            │  │                        │
│  $XX.XX/year               │  │  $X.XX/week            │
│  Billed annually after     │  │  Billed weekly after   │
│  free trial                │  │  free trial            │
└────────────────────────────┘  └────────────────────────┘
```
- Side-by-side, 10px gap, each flex 1
- Selected: 2px primary border, subtle primary bg tint
- Unselected: 2px light border
- Radio indicators: 20x20 circle, filled with 7x7 white dot when selected
- Save badge: absolute top-left, primary bg, white text, 10px bold uppercase
- Price: 26px, weight 800
- Period: 14px, weight 500, textSecondary
- Note: 11px, textTertiary
- Loading: ActivityIndicator (small)
- Error: refresh icon + "Tap to retry"

### CTA Button
```
┌────────────────────────────────────┐
│       Start Your Free Trial        │
└────────────────────────────────────┘
  3-day free trial, then $XX billed
  annually. Cancel anytime.
  Auto-renews. Manage in Settings.
```
- Height: 54px, 16px radius, primary bg, medium shadow
- Text: 17px, weight 700, white
- Loading state: "Loading..."
- Disabled: opacity 0.5
- Pressed: scale 0.97, opacity 0.9
- Subtext: 11px, textTertiary, center

### Footer
```
Restore Purchase · Terms · Privacy
```
- 12px, textTertiary, centered row, 6px gap
- Terms → `/legal?type=terms`
- Privacy → `/legal?type=privacy`

### Close Button
- 32x32px circle, absolute top-right (20px inset)
- Icon: close, 18px, textTertiary

---

## 7. Tab Bar

- Background: `#FBF8F3`
- Active icon color: `#FF8C00`
- Inactive icon color: `#B8AD9E`
- Tabs: Home, Library, Add (+), Focus, Profile

---

## 8. Content Types & Sources

### Categories (9)
Tech, Business, Health, Entertainment, Education, News, Creative, Personal Development, Other

### Sources (15+)
YouTube, Vimeo, TikTok, Instagram, Twitter, Reddit, HackerNews, GitHub, LinkedIn, Facebook, Article, PDF, Document, Newsletter, Other

### Content Statuses
pending, in_progress, completed, archived

### Creation Types
podcast, summary, briefing, recap

---

## 9. Button Presets

| Type      | Height | Radius | H-Padding |
|-----------|--------|--------|-----------|
| primary   | 56     | 28     | 24        |
| secondary | 52     | 26     | 20        |
| small     | 40     | 20     | 16        |
| icon      | 44x44  | 22     | —         |
| iconSmall | 36x36  | 18     | —         |

---

## 10. Card Presets

| Type     | Radius | Padding |
|----------|--------|---------|
| default  | 20     | 20      |
| featured | 24     | 24      |
| compact  | 16     | 16      |
| glass    | 20     | 16      |

---

## 11. Key Dimensions

- Screen horizontal padding: 20px
- Tablet max width: 700px (centered)
- Input height: 52px (default), 44px (search)
- Icon sizes: xs=14, sm=18, md=22, lg=26, xl=32, xxl=40
- Avatar sizes: xs=24, sm=32, md=40, lg=56, xl=80
