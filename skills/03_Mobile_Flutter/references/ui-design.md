# Flutter UI/UX Design Guidelines

This document outlines the standards for creating high-quality, beautiful, and accessible Flutter widgets.

## 1. Design System (Material 3)

### Core Tokens
- **Spacing**: 8, 12, 16, 20, 24, 32px (Use 4px grid).
- **Radius**: 4 (XS), 8 (S), 12 (M), 16 (L), 28 (XL).
- **Typography**: Use `Theme.of(context).textTheme`.

### Colors
- Always use `Theme.of(context).colorScheme`.
- Support **Light** and **Dark** modes automatically.
- Never hardcode colors (e.g., `Colors.blue`), use semantic names (`primary`, `onPrimary`, `surface`).

## 2. Widget Implementation Rules

### Performance
- **const**: Use `const` constructors everywhere possible.
- **Lists**: Always use `ListView.builder` for dynamic lists.
- **RepaintBoundary**: Wrap complex animations or static sub-trees in `RepaintBoundary`.
- **Optimization**: Avoid complex calculations in `build()`.

### Interaction
- **Feedback**: All tappable elements MUST have ripple effects (`InkWell` or `ButtonStyle`).
- **Animation**: Use `AnimatedContainer`, `TweenAnimationBuilder`, or `Hero` for smooth transitions.
- **Responsiveness**: Use `MediaQuery` or `LayoutBuilder` to adapt to screen sizes.

### Accessibility
- **Semantics**: Use `Semantics` widget for complex custom controls.
- **Tooltips**: Add `Tooltip` to all icon buttons.
- **Contrast**: Ensure text contrast ratio is ≥ 4.5:1.

## 3. Widget Template

```dart
/// [WidgetName]
///
/// A [description] widget that [functionality].
///
/// Example:
/// ```dart
/// [WidgetName](
///   title: 'Hello',
///   onTap: () {},
/// )
/// ```
class [WidgetName] extends StatelessWidget {
  final String title;
  final VoidCallback? onTap;

  const [WidgetName]({
    Key? key,
    required this.title,
    this.onTap,
  }) : super(key: key);

  @override
  Widget build(BuildContext context) {
    final theme = Theme.of(context);
    final colors = theme.colorScheme;

    return InkWell(
      onTap: onTap,
      borderRadius: BorderRadius.circular(12),
      child: Container(
        padding: const EdgeInsets.all(16),
        decoration: BoxDecoration(
          color: colors.surface,
          borderRadius: BorderRadius.circular(12),
          border: Border.all(color: colors.outlineVariant),
        ),
        child: Text(
          title,
          style: theme.textTheme.bodyLarge?.copyWith(
            color: colors.onSurface,
          ),
        ),
      ),
    );
  }
}
```
