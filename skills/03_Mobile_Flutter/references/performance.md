# Flutter Performance Optimization

This document serves as a checklist and guide for optimizing Flutter applications.

## 1. Build & Rendering

- [ ] **const**: Are you using `const` constructors wherever possible?
- [ ] **build()**: Is the `build` method free of complex computations or side effects?
- [ ] **RepaintBoundary**: Are complex, static sub-trees wrapped in `RepaintBoundary`?
- [ ] **Opacity**: Avoid `Opacity` widget for simple fades; use `AnimatedOpacity` or image alpha.

## 2. List & Scroll Views

- [ ] **ListView.builder**: Are you using lazy builders for long lists?
- [ ] **itemExtent**: Have you set `itemExtent` or `prototypeItem` if list items are fixed height?
- [ ] **Images**: Are images cached and resized (`cacheWidth`/`cacheHeight`)?

## 3. Memory Management

- [ ] **Dispose**: Are Controllers (TextEditing, Scroll, Animation) disposed?
- [ ] **Riverpod**: Are you using `.autoDispose` for providers that don't need to live forever?
- [ ] **Images**: Are large images cleared from memory when not needed?

## 4. Startup Time

- [ ] **Lazy Loading**: Defer non-critical initialization until after the first frame.
- [ ] **Splash Screen**: Use a native splash screen while Flutter engine warms up.
