---
name: Flutter Performance Optimization
description: Master Flutter performance profiling and optimization techniques including DevTools, repainting boundaries, const constructors, and isolate usage. Use when fixing jank, reducing app size, or improving startup time.
---

# Flutter Performance Optimization

Techniques and tools to diagnose, profile, and fix performance issues in Flutter applications to ensure 60fps (or 120fps) rendering.

## When to Use This Skill

- Users complain about "jank" or stuttering scrolling
- App startup time is slow
- High battery consumption or CPU usage
- Debugging memory leaks
- Preparing an app for production release

## Key Techniques

### 1. Rendering Performance
- **Const Constructors**: Use `const` widgets wherever possible to allow Flutter to reuse widgets.
- **RepaintBoundary**: Wrap widgets that repaint frequently (like spinners or progress bars) in `RepaintBoundary` to isolate them from the rest of the UI.
- **ListView.builder**: Always use `.builder` or `.separated` for long lists instead of standard `ListView` or `Column`.
- **Avoid Opacity**: Use `Opacity` widget sparingly; prefer `AnimatedOpacity` or providing a transparent color to `Container`.

### 2. Build Method Optimization
- **Keep it simple**: Avoid complex logic in `build()` methods. Move logic to BLoC/Provider.
- **Extract Widgets**: Break down large build methods into smaller stateless widgets to take advantage of Flutter's caching mechanisms (don't just use helper methods).

### 3. Asynchronous Operations
- **Isolates**: Move heavy computation (JSON parsing of large files, image processing) to background Isolates using `compute()` or `Isolate.spawn()`.
- **Async/Await**: Ensure UI thread is never blocked.

### 4. Memory Management
- **Image Caching**: Use `cached_network_image` and properly size images (`cacheWidth`/`cacheHeight`).
- **Dispose**: Always dispose Controllers (AnimationController, TextEditingController, ScrollController) in `dispose()`.

## Tools

- **Flutter DevTools**:
    - **Performance View**: Check UI and Raster thread times.
    - **Widget Inspector**: Visualize rebuild counts.
    - **Memory View**: Detect leaks.
- **Profile Mode**: ALWAYS profile in Profile mode (`flutter run --profile`), never in Debug mode.
