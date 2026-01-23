---
name: Flutter State Management
description: Compare and implement popular Flutter state management solutions including Riverpod, BLoC, Provider, and GetX. Use when choosing an architecture or implementing complex state flows.
---

# Flutter State Management

A guide to choosing and implementing the right state management solution for your Flutter application.

## When to Use This Skill

- Starting a new project and deciding on architecture
- Switching from `setState` to a more scalable solution
- Managing global state (User session, Theme, Settings)
- Sharing state between distant widgets

## Popular Solutions

### 1. Riverpod (Recommended 2026)
- **Pros**: Compile-safe, no `BuildContext` dependency, great testability, auto-dispose support.
- **Cons**: Learning curve for functional concepts.
- **Best for**: New projects, scalable apps.
- **Key Pattern**: `ConsumerWidget`, `ref.watch()`.

### 2. BLoC (Business Logic Component)
- **Pros**: Strict separation of concerns, event-driven, standard in enterprise.
- **Cons**: Boilerplate (though reduced with Cubit).
- **Best for**: Large teams, enterprise apps, complex event streams.
- **Key Pattern**: `BlocProvider`, `BlocBuilder`, `Events` & `States`.

### 3. Provider
- **Pros**: Simple, official Google recommendation for years, easy to learn.
- **Cons**: Depends on `BuildContext`, runtime errors if provider not found.
- **Best for**: Small to medium apps, simple dependency injection.
- **Key Pattern**: `ChangeNotifier`, `Consumer`.

### 4. GetX
- **Pros**: "All-in-one" (State, Nav, DI), very little boilerplate.
- **Cons**: Non-standard patterns, can lead to messy code, hard to test.
- **Best for**: Rapid prototyping, solo developers who want speed.
- **Key Pattern**: `Get.put()`, `Obx()`.

## Decision Guide

| Feature | Riverpod | BLoC | Provider | GetX |
| :--- | :--- | :--- | :--- | :--- |
| **Scalability** | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ | ⭐⭐⭐ | ⭐⭐ |
| **Testability** | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ | ⭐⭐⭐ | ⭐⭐ |
| **Ease of Learning**| ⭐⭐⭐ | ⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ |
| **Boilerplate** | Low | High/Med | Low | Very Low |

## Best Practices

- **Lift State Up**: Keep state as low in the tree as possible, but high enough to be shared.
- **Immutability**: Always use immutable state classes (use `freezed` package) to avoid side effects.
- **Avoid Global Variables**: Don't use global singletons; use the DI system provided by your state manager.
