---
name: Flutter Testing & QA
description: Comprehensive guide for testing Flutter applications including unit, widget, and integration tests, as well as goldens and mocking.
---

# Flutter Testing & Quality Assurance

Best practices for ensuring your Flutter application is reliable, bug-free, and maintainable through a robust testing strategy.

## Testing Pyramid

1. **Unit Tests**: Test a single function, method, or class. (Fast, no UI)
2. **Widget Tests**: Test a single widget in isolation. (Fast, mock dependencies)
3. **Integration Tests**: Test a complete app or a large part of an app. (Slow, runs on device/emulator)

## Key Practices

### 1. Unit Testing
- **Business Logic**: All BLoCs, Notifiers, and Use Cases must have 100% unit test coverage.
- **Mocking**: Use `mocktail` or `mockito` to mock external dependencies (APIs, Databases).
- **Test-Driven Development (TDD)**: Write tests before implementation for complex business rules.

### 2. Widget Testing
- **Finders & Matchers**: Use `find.byType`, `find.byKey`, and `expect(..., findsOneWidget)`.
- **Pump**: Use `tester.pumpWidget()` to build the widget and `tester.pump()` for animations.
- **Golden Tests**: Use `matchesGoldenFile` to ensure UI doesn't regress visually.

### 3. Integration Testing
- **User Flows**: Test critical paths like "Login -> Purchase -> Checkout".
- **Performance Profiling**: Run integration tests with `--profile` to capture performance metrics.

### 4. Code Quality
- **Lints**: Use `flutter_lints` or `very_good_analysis`.
- **Coverage**: Run `flutter test --coverage` and use `lcov` to generate reports.

## Example: Mocking with Mocktail

```dart
class MockUserRepository extends Mock implements UserRepository {}

void main() {
  late MockUserRepository mockRepo;
  late LoginBloc loginBloc;

  setUp(() {
    mockRepo = MockUserRepository();
    loginBloc = LoginBloc(repository: mockRepo);
  });

  test('emits [Loading, Success] when login succeeds', () async {
    when(() => mockRepo.login(any(), any())).thenAnswer((_) async => User());
    
    loginBloc.add(LoginSubmitted(email: 'test@test.com', password: 'password'));
    
    await expectLater(
      loginBloc.stream,
      emitsInOrder([
        LoginState.loading(),
        LoginState.success(),
      ]),
    );
  });
}
```
