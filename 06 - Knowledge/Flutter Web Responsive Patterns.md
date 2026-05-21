---
type: knowledge
category: patterns
tags: [flutter, web, responsive, mobile]
---

# Flutter Web Responsive Patterns

> Patterns for making Flutter web apps responsive across desktop and mobile.

## 🔗 Connections

- **Used in:** [[FinTra - Admin Dashboard]]

---

## 📐 Key Patterns

### Navigation Breakpoint: 768px
- **Above:** Full sidebar with icons + labels
- **Below:** Bottom navigation bar with icons only

### DesktopPageHeader
- Responsive text sizes (larger on desktop, smaller on mobile)
- Adapts padding and layout

### Table → Card Layout
- Desktop: Full table with columns
- Mobile: Card layout with stacked fields

### Email Visualizer
- Desktop/Tablet/Phone device frame switching
- Smooth animated transitions between sizes

```dart
final isMobile = MediaQuery.of(context).size.width < 768;
```

---

## 📋 Related

- [[ADR-003 — Flutter Web for Admin Dashboard]]