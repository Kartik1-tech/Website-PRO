# THE TRANSITION LIBRARY (18 Patterns)

> Reference for KINETIC agent. Every pattern is self-contained, CSS-first, tunable via custom properties, and ships with a reduced-motion guard.

## How to Use

Every transition follows this structure:
- `:root` custom properties for tunability (duration, distance, easing)
- `t-*` namespaced class names
- `@media (prefers-reduced-motion: reduce)` guard (mandatory)
- Only animates `transform` and `opacity` (GPU-safe)

```css
/* Base tokens applied to every transition */
:root {
  --t-duration: 300ms;
  --t-duration-slow: 700ms;
  --t-ease: cubic-bezier(0.32, 0.72, 0, 1);
  --t-ease-out: cubic-bezier(0.16, 1, 0.3, 1);
  --t-spring: cubic-bezier(0.34, 1.56, 0.64, 1);
  --t-distance: 8px;
}

@media (prefers-reduced-motion: reduce) {
  *, *::before, *::after {
    animation-duration: 0.01ms !important;
    transition-duration: 0.01ms !important;
  }
}
```

---

## 01. Card Resize
Smooth dimensional change when card content expands.

```css
.t-card-resize {
  transition:
    width var(--t-duration-slow) var(--t-ease),
    height var(--t-duration-slow) var(--t-ease);
}
/* Motion library: layout prop | CSS: interpolate-size (progressive) */
```

## 02. Number Pop-In
Digit flip with blur and stagger (counters, stats, pricing).

```css
@keyframes t-number-pop {
  0%   { opacity: 0; transform: translateY(var(--t-distance)) scale(0.9); filter: blur(4px); }
  100% { opacity: 1; transform: translateY(0) scale(1); filter: blur(0); }
}
.t-number-pop { animation: t-number-pop var(--t-duration) var(--t-spring) both; }
.t-number-pop:nth-child(n) { animation-delay: calc(var(--index, 0) * 60ms); }
```

## 03. Notification Badge
Diagonal slide with spring pop-in (badges, alerts).

```css
@keyframes t-badge-in {
  0%   { opacity: 0; transform: translate(4px, -4px) scale(0); }
  70%  { transform: translate(-1px, 1px) scale(1.1); }
  100% { opacity: 1; transform: translate(0, 0) scale(1); }
}
.t-badge { animation: t-badge-in 450ms var(--t-spring) both; }
```

## 04. Text States Swap
Crossfade with blur (labels changing, status text).

```css
.t-text-swap { position: relative; }
.t-text-swap[data-state] {
  animation: t-swap-out 200ms var(--t-ease) forwards;
}
@keyframes t-swap-out {
  to { opacity: 0; filter: blur(4px); transform: translateY(-4px); }
}
.t-text-swap[data-state].t-in {
  animation: t-swap-in 250ms var(--t-ease-out) forwards;
}
@keyframes t-swap-in {
  from { opacity: 0; filter: blur(4px); transform: translateY(4px); }
}
```

## 05. Menu Dropdown
Origin-aware open/close (knows where it opens from).

```css
.t-dropdown {
  transform-origin: top right; /* set per-instance */
  transition:
    opacity var(--t-duration) var(--t-ease),
    transform var(--t-duration) var(--t-ease),
    scale var(--t-duration) var(--t-ease);
}
.t-dropdown[data-open="false"] {
  opacity: 0;
  transform: scaleY(0.9) translate(var(--t-origin-x, 0), var(--t-origin-y, -4px));
  pointer-events: none;
}
.t-dropdown[data-open="true"] {
  opacity: 1;
  transform: scaleY(1) translate(0, 0);
}
```

## 06. Modal Open/Close
Scale + backdrop fade (dialogs, confirmations).

```css
.t-modal-backdrop {
  transition: opacity var(--t-duration) var(--t-ease);
}
.t-modal-panel {
  transition:
    opacity var(--t-duration) var(--t-ease),
    scale var(--t-duration-slow) var(--t-spring),
    translate var(--t-duration-slow) var(--t-spring);
}
.t-modal[data-open="false"] .t-modal-panel {
  opacity: 0; scale: 0.95; translate: 0 8px;
}
.t-modal[data-open="true"] .t-modal-panel {
  opacity: 1; scale: 1; translate: 0 0;
}
```

## 07. Panel Reveal
Slide + spring settle (side sheets, drawers).

```css
.t-panel {
  transition: translate var(--t-duration-slow) var(--t-spring);
}
.t-panel[data-open="false"] { translate: 100% 0; }
.t-panel[data-open="true"]  { translate: 0 0; }
```

## 08. Page Transition
Directional forward/back slide (route changes).

```css
.t-page-enter   { animation: t-page-in var(--t-duration-slow) var(--t-ease-out) both; }
.t-page-exit    { animation: t-page-out var(--t-duration) var(--t-ease) both; }
@keyframes t-page-in {
  from { opacity: 0; transform: translateX(24px); }
}
@keyframes t-page-out {
  to { opacity: 0; transform: translateX(-24px) scale(0.98); }
}
```

## 09. Icon Swap
Scale + blur (theme toggle, icon state changes).

```css
.t-icon-swap {
  transition: opacity 150ms var(--t-ease), scale 200ms var(--t-spring), rotate 200ms var(--t-spring), filter 150ms var(--t-ease);
}
.t-icon-swap[data-swap="true"] {
  opacity: 0; scale: 0.6; rotate: 15deg; filter: blur(3px);
}
```

## 10. Success Checkmark
SVG path draw + rotate + fade + Y-bob (form success).

```css
.t-check-path {
  stroke-dasharray: 1;
  stroke-dashoffset: 1;
  transition: stroke-dashoffset 500ms var(--t-ease-out) 100ms;
}
.t-check[data-done="true"] .t-check-path { stroke-dashoffset: 0; }
.t-check[data-done="true"] {
  animation: t-check-bob 600ms var(--t-spring) 100ms both;
}
@keyframes t-check-bob {
  0% { translate: 0 0; } 40% { translate: 0 -6px; } 100% { translate: 0 0; }
}
```

## 11. Avatar Group Hover
Hovered avatar springs up, neighbors follow with falloff.

```css
.t-avatar-group:hover .t-avatar { translate: 0 0; }
.t-avatar-group .t-avatar:nth-child(1):hover { translate: 0 -6px; z-index: 10; }
.t-avatar-group .t-avatar:nth-child(1):hover ~ .t-avatar:nth-child(2) { translate: 0 -3px; }
.t-avatar-group .t-avatar:nth-child(1):hover ~ .t-avatar:nth-child(3) { translate: 0 -1px; }
.t-avatar { transition: translate 300ms var(--t-spring); }
```

## 12. Error State Shake
Input shake on validation error with auto-revert.

```css
@keyframes t-shake {
  0%, 100% { translate: 0 0; }
  20% { translate: -6px 0; } 40% { translate: 5px 0; }
  60% { translate: -3px 0; } 80% { translate: 2px 0; }
}
.t-input-error { animation: t-shake 400ms var(--t-ease); }
```

## 13. Skeleton Shimmer
Light sweep across placeholder (loading states).

```css
@keyframes t-shimmer {
  from { background-position: 200% 0; }
  to { background-position: -200% 0; }
}
.t-skeleton {
  background: linear-gradient(
    90deg,
    var(--surface-raised) 25%,
    var(--surface-elevated) 50%,
    var(--surface-raised) 75%
  );
  background-size: 200% 100%;
  animation: t-shimmer 1.8s linear infinite;
  border-radius: inherit;
}
```

## 14. Directional Fill
Button fill enters from cursor's exact side.

```css
.t-fill-btn { position: relative; overflow: hidden; }
.t-fill-btn::before {
  content: "";
  position: absolute; inset: 0;
  background: var(--fill-color);
  translate: var(--enter-x, 0) var(--enter-y, 0);
  transition: translate 400ms var(--t-ease-out);
}
.t-fill-btn:hover::before { translate: 0 0; }
/* JS sets --enter-x/--enter-y from mouseenter event coordinates */
```

## 15. Ripple Click
Wave from exact click coordinates.

```css
.t-ripple-host { position: relative; overflow: hidden; }
.t-ripple {
  position: absolute;
  border-radius: 50%;
  background: currentColor;
  opacity: 0.25;
  animation: t-ripple 600ms var(--t-ease-out) forwards;
  pointer-events: none;
}
@keyframes t-ripple {
  from { scale: 0; opacity: 0.25; }
  to { scale: 4; opacity: 0; }
}
```

## 16. Staggered Cascade
List items enter with sequential delay.

```css
.t-stagger {
  opacity: 0;
  animation: t-rise var(--t-duration) var(--t-ease-out) forwards;
  animation-delay: calc(var(--index, 0) * 70ms);
}
@keyframes t-rise {
  from { opacity: 0; translate: 0 16px; filter: blur(4px); }
  to { opacity: 1; translate: 0 0; filter: blur(0); }
}
```

## 17. Magnetic Pull
Elements follow cursor within radius (use Motion useMotionValue, never useState).

```tsx
"use client";
import { motion, useMotionValue, useSpring, useTransform } from "motion/react";

function Magnetic({ children }: { children: React.ReactNode }) {
  const x = useMotionValue(0);
  const y = useMotionValue(0);
  const sx = useSpring(x, { stiffness: 100, damping: 20 });
  const sy = useSpring(y, { stiffness: 100, damping: 20 });

  return (
    <motion.div
      style={{ x: sx, y: sy }}
      onMouseMove={(e) => {
        const r = e.currentTarget.getBoundingClientRect();
        x.set((e.clientX - r.left - r.width / 2) * 0.3);
        y.set((e.clientY - r.top - r.height / 2) * 0.3);
      }}
      onMouseLeave={() => { x.set(0); y.set(0); }}
    >
      {children}
    </motion.div>
  );
}
```

## 18. Curtain Reveal
Content parts like theater curtains (hero entrances, section reveals).

```css
@keyframes t-curtain-left { from { translate: -100% 0; } to { translate: 0 0; } }
@keyframes t-curtain-right { from { translate: 100% 0; } to { translate: 0 0; } }
.t-curtain-l { animation: t-curtain-left var(--t-duration-slow) var(--t-ease) both; }
.t-curtain-r { animation: t-curtain-right var(--t-duration-slow) var(--t-ease) both; }
.t-curtain-host { overflow: hidden; } /* parent clips */
```

---

## Easing Token Reference

| Token | Curve | Feel |
|---|---|---|
| `--t-ease` | cubic-bezier(0.32, 0.72, 0, 1) | Smooth premium glide |
| `--t-ease-out` | cubic-bezier(0.16, 1, 0.3, 1) | Fast start, soft land |
| `--t-spring` | cubic-bezier(0.34, 1.56, 0.64, 1) | Playful overshoot |
| Motion spring | stiffness: 100, damping: 20 | Physical weight |

## Duration Rules

| Interaction | Duration |
|---|---|
| Hover states | 150-250ms |
| Button presses / toggles | 200-300ms |
| Modals, panels, dropdowns | 300-450ms |
| Page transitions, reveals | 500-800ms |
| Ambient/looping | 3-20s |

BANNED: `linear` easing on UI, `ease-in-out` as default, instant state changes, durations above 1s for interactive feedback.
