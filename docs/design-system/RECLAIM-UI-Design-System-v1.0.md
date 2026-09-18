# RECLAIM UI Design System v1.0

**Status:** Foundation baseline

## Design philosophy

**Calm. Safe. Human. Hopeful.**

The UI should feel supportive rather than clinical, judgmental, or gamified. Mobile-first behavior is required even though the first production client is the Web MVP.

## Tokens

- Deep Teal primary family, centered on #123C3A
- Light Teal supportive surfaces, centered on #F0F8F7
- Warm Sand neutral/surface family
- Semantic success, warning, error and informational states
- Inter typography
- 4px base spacing scale
- restrained friendly radii
- purposeful subtle motion; respect prefers-reduced-motion
- mobile-first responsive breakpoints
- WCAG 2.2 AA target
- minimum 44x44px touch targets

## Icons

Lucide React is the baseline icon set. Meaningful icons require accessible names.

## Core components

Button, IconButton, Input, Textarea, Select, Checkbox, Radio, Toggle, FormField, Alert, Card, Modal, Drawer, Tabs, Badge, Progress, Avatar, EmptyState, LoadingState, ErrorState, Toast, AppShell, BottomNav.

## Component rules

Components consume design tokens and expose semantic variants. Page-specific styling must not duplicate global tokens.

## Accessibility

Use semantic HTML, visible keyboard focus, accessible labels and errors, sufficient contrast, and never rely on color alone.

## Future compatibility

The design system is Web-first but must preserve the visual language for a future native/mobile client. Shared semantic tokens and behavior should be documented independently from DOM-specific implementation details.