# Flutter Testing Guidelines

This document defines the testing strategy for enterprise applications.

## 1. The Testing Pyramid

- **Unit Tests (70%)**: Test business logic, repositories, and utils. Fast and isolated.
- **Widget Tests (25%)**: Test UI components, interactions, and simple flows.
- **Integration Tests (5%)**: Test full end-to-end user journeys.

## 2. Unit Testing (Business Logic)

**Tools**: `test`, `mockito`, `bloc_test` (if using Bloc), `riverpod_test` (conceptually).

```dart
void main() {
  group('UserNotifier', () {
    late MockUserRepository mockRepo;
    late UserNotifier notifier;

    setUp(() {
      mockRepo = MockUserRepository();
      notifier = UserNotifier(mockRepo);
    });

    test('loadUser updates state to data on success', () async {
      // Arrange
      when(mockRepo.getUser('1')).thenAnswer((_) async => User(id: '1', name: 'Bob'));

      // Act
      await notifier.loadUser('1');

      // Assert
      expect(notifier.state, isA<AsyncData<User>>());
    });
  });
}
```

## 3. Widget Testing (UI)

**Tools**: `flutter_test`.

```dart
testWidgets('Login button shows loading indicator when pressed', (tester) async {
  // Arrange
  await tester.pumpWidget(const MaterialApp(home: LoginPage()));

  // Act
  await tester.tap(find.text('Login'));
  await tester.pump(); // Start animation

  // Assert
  expect(find.byType(CircularProgressIndicator), findsOneWidget);
});
```

## 4. Best Practices

- **Mock External Dependencies**: Never make real network calls in Unit/Widget tests.
- **Test Names**: Should be sentences (e.g., "should return error when network fails").
- **AAA Pattern**: Arrange, Act, Assert.
