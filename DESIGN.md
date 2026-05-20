# Design

## Source of truth
- Status: Active
- Last refreshed: 2026-05-20
- Primary product surfaces: `index.html` 신규기사님 가이드, in-page media viewer, GitHub Pages deployment.
- Evidence reviewed: `README.md`, `index.html`, `assets/item-*.mp4`, `assets/item-4.jpg`, `assets/logi-guide/page-*.jpg`.
- Source brief: Genesis, provided by the user on 2026-05-20.

## Brand
- Personality: quietly confident, professional, modern, precise, editorial.
- Trust signals: clear Korean labels, direct guide titles, stable in-page viewing, restrained interface chrome.
- Avoid: decorative gradients, sterile empty layouts, noisy labels, file-type clutter, more than one filled primary action in a section.

## Product goals
- Goals: help new DriveGo drivers quickly discover and open guide materials on mobile.
- Non-goals: public marketing, community browsing, account flows, uploads, comments, ratings.
- Success signals: first-screen list is scannable, media opens in-page, PDF material remains readable on mobile, back navigation is obvious.

## Personas and jobs
- Primary personas: 신규 기사님 using a phone while preparing to start work.
- User jobs: understand탁송 basics, read caution rules, learn Logi usage, learn icon/app installation.
- Key contexts of use: mobile web, weak networks, quick reference, repeated reopening of the same guide items.

## Information architecture
- Primary navigation: a single sticky top bar with the DriveGo label.
- Core routes/screens: guide list, detail viewer for video/image/page stacks.
- Content hierarchy: brand label, main title, gallery card list, detail title, viewer surface.

## Design principles
- Principle 1: show the actual guide material as the interface, not explanatory filler.
- Principle 2: use editorial spacing and framed surfaces while keeping the tap target large.
- Tradeoffs: visual polish must not add heavy media loading to the first screen; use image previews instead of autoplay/video previews.

## Visual language
- Color: use `#FAFAFA` background, `#FFFFFF` surfaces, `#0A0A0A` primary text, `#6B6B6B` secondary text, `#E8E8EC` borders, `#6366F1` only for interactive states.
- Typography: General Sans for display and headings, DM Sans for body/UI, JetBrains Mono for code if added later.
- Spacing/layout rhythm: 4px base grid; 24px mobile container padding where space allows; 20-24px card gaps.
- Shape/radius/elevation: 12px gallery cards, 6px buttons, 8px panels, minimal static shadows, hover lift only.
- Motion: 200ms transitions for card lift and interactive states; no decorative animation.
- Imagery/iconography: actual guide previews are used as the visual asset; no decorative illustration layer.

## Components
- Existing components to reuse: in-page viewer, hash-based navigation, generated Logi guide page images.
- New/changed components: sticky nav, editorial page header, gallery guide cards, framed detail viewer.
- Variants and states: card hover/focus, secondary back button, page-stack viewer, video poster viewer.
- Token/component ownership: CSS custom properties in `index.html` are the canonical tokens for this static page.

## Accessibility
- Target standard: practical WCAG 2.1 AA for text contrast, focus visibility, and semantic structure.
- Keyboard/focus behavior: cards and back button are keyboard-focusable with a 3px indigo focus ring.
- Contrast/readability: near-black text on white/light warm gray surfaces; muted text only for secondary metadata.
- Screen-reader semantics: `main`, `nav`, `section`, headings, and image alt text are required.
- Reduced motion and sensory considerations: hover transitions only; no autoplay.

## Responsive behavior
- Supported breakpoints/devices: mobile-first phones, tablet, desktop up to a 1280px max content container.
- Layout adaptations: stacked cards on mobile, grid cards on wider screens, detail viewer uses full available width.
- Touch/hover differences: entire card is the tap target; hover lift is enhancement only.

## Interaction states
- Loading: static image previews should appear before heavy media loads.
- Empty: not applicable while the guide has four fixed items.
- Error: not currently implemented; broken assets should still leave the title and back button visible.
- Success: content appears in the detail viewer without leaving the page.
- Disabled: not applicable.
- Offline/slow network: first screen must avoid loading MP4 files until a video card is opened.

## Content voice
- Tone: direct Korean operational labels.
- Terminology: use `드라이브고`, `신규기사님 가이드`, `탁송`, `로지`.
- Microcopy rules: avoid explanatory paragraphs on the main screen; labels should be short and actionable.

## Implementation constraints
- Framework/styling system: single static `index.html`, no build pipeline.
- Design-token constraints: use local CSS custom properties mapped to Genesis colors.
- Performance constraints: do not load MP4s on the list screen; keep PDF converted page images lazy after the first two pages.
- Compatibility constraints: GitHub Pages static hosting, mobile browser media behavior, no server-side transforms.
- Test/screenshot expectations: run syntax checks and capture mobile/desktop screenshots after visual changes.

## Genesis brief

### Overview
An editorial precision interface for a community platform where developers discover, share, and download design system files. The aesthetic is quietly confident - bold display typography, generous spacing, and gallery-frame card surfaces. The mood is professional and modern without being sterile. High information density balanced by breathing room.

### Colors
- Primary `#6366F1`
- Primary Hover `#4F46E5`
- Secondary `#20970B`
- Neutral `#9C9C9C`
- Background `#FAFAFA`
- Surface `#FFFFFF`
- Text Primary `#0A0A0A`
- Text Secondary `#6B6B6B`
- Border `#E8E8EC`
- Success `#10B981`
- Warning `#F59E0B`
- Error `#EF4444`

### Typography
- Display Font: General Sans, loaded from Fontshare.
- Body Font: DM Sans, loaded from Google Fonts.
- Code Font: JetBrains Mono, loaded from Google Fonts.
- Type scale: display 72px, headline 60px, section heading 32px, subhead 24px, body 15px, small 13px, caption 12px, overline 11px uppercase.

### Elevation
- Cards rest flat with a 1px border and gain subtle hover elevation.
- Primary buttons gain a tinted glow shadow on hover.
- Nav uses backdrop blur and a bottom border.
- Focus states use a 3px indigo ring.

### Components
- Buttons: 6px radius, medium weight, small 32px, medium 38px, large 44px.
- Cards: white surface, subtle border, 12px radius, overflow hidden, 200px preview area.
- Inputs: 6px radius, 14px font, indigo focus ring.
- Chips: pill shape, 12px font.
- Lists: stacked rows with dividers.
- Checkboxes: 20px rounded-full.
- Tooltips: native browser `title` attributes.
- Navigation: sticky 56px top nav with backdrop blur.
- Search: rounded-xl bar with magnifying glass and shortcut badge when needed.

### Spacing
- Base unit: 4px.
- Scale: 4, 8, 12, 16, 20, 24, 32, 40, 48, 64, 80, 96px.
- Container max width: 1280px with 24px horizontal padding.
- Card grid gap: 20-24px.

### Border radius
- 4px: tags, chips, badges, inline code.
- 6px: buttons, inputs, selects.
- 8px: metadata cards, dropdowns, panels.
- 12px: kit preview cards, search bar, featured sections.
- 9999px: avatars, status dots, pill badges.

## Open questions
- [ ] Whether a future download link should be reintroduced for desktop users / owner: product / impact: optional secondary action.
