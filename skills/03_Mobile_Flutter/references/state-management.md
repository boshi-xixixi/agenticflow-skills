# Flutter State Management (Riverpod)

This document defines the patterns for using Riverpod in enterprise applications.

## 1. Core Principles

- **Immutability**: All state must be immutable (use `freezed`).
- **Auto Dispose**: Use `.autoDispose` by default to prevent memory leaks.
- **Dependency Injection**: Use `Provider` to inject dependencies (Repositories, Services).
- **Separation**: Logic lives in `Notifiers`, UI only calls methods on Notifiers.

## 2. Provider Types

| Provider Type | Use Case |
|Data Type| Description |
|---|---|
| `Provider` | Dependencies, Read-only values, Utility classes. |
| `StateProvider` | Simple UI state (filters, toggles). |
| `FutureProvider` | Async data fetching (GET requests). |
| `StreamProvider` | Real-time data (WebSockets, Firebase). |
| `StateNotifierProvider` | Complex business logic & state mutation. |
| `AsyncNotifierProvider` | (Riverpod 2.0) Complex async business logic. |

## 3. Implementation Patterns

### A. Data Model (Freezed)

```dart
@freezed
class User with _$User {
  const factory User({
    required String id,
    required String name,
  }) = _User;

  factory User.fromJson(Map<String, dynamic> json) => _$UserFromJson(json);
}
```

### B. Repository Provider

```dart
final userRepositoryProvider = Provider<UserRepository>((ref) {
  return UserRepositoryImpl(ref.watch(apiClientProvider));
});
```

### C. Async Business Logic (AsyncNotifier)

Preferred over `StateNotifier` for async operations in Riverpod 2.0+.

```dart
final userListProvider = AsyncNotifierProvider.autoDispose<UserListNotifier, List<User>>(() {
  return UserListNotifier();
});

class UserListNotifier extends AutoDisposeAsyncNotifier<List<User>> {
  @override
  FutureOr<List<User>> build() {
    // Initial Load
    return ref.read(userRepositoryProvider).fetchUsers();
  }

  Future<void> addUser(User user) async {
    state = const AsyncValue.loading();
    state = await AsyncValue.guard(() async {
      await ref.read(userRepositoryProvider).createUser(user);
      // Refresh list
      return ref.read(userRepositoryProvider).fetchUsers();
    });
  }
}
```

### D. UI Consumption

```dart
class UserListPage extends ConsumerWidget {
  @override
  Widget build(BuildContext context, WidgetRef ref) {
    final userListAsync = ref.watch(userListProvider);

    return userListAsync.when(
      loading: () => const CircularProgressIndicator(),
      error: (err, stack) => Text('Error: $err'),
      data: (users) => ListView.builder(
        itemCount: users.length,
        itemBuilder: (_, index) => Text(users[index].name),
      ),
    );
  }
}
```
