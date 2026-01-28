# Flutter API Integration Guidelines

This document establishes the standards for network communication using Dio and Freezed.

## 1. Stack
- **Client**: `Dio`
- **Serialization**: `json_serializable` / `freezed`
- **Architecture**: DataSource -> Repository -> Provider

## 2. Error Handling Strategy

All API exceptions must be caught in the Data Layer and converted into Domain Failures.

```dart
abstract class Failure {
  final String message;
  Failure(this.message);
}

class NetworkFailure extends Failure { ... }
class ServerFailure extends Failure { ... }
```

## 3. Dio Configuration Template

```dart
final dioProvider = Provider((ref) {
  final dio = Dio(
    BaseOptions(
      baseUrl: AppConfig.apiBaseUrl,
      connectTimeout: const Duration(seconds: 30),
      receiveTimeout: const Duration(seconds: 30),
      headers: {'Accept': 'application/json'},
    ),
  );

  // Interceptors
  dio.interceptors.add(InterceptorsWrapper(
    onRequest: (options, handler) {
      final token = ref.read(authProvider);
      if (token != null) options.headers['Authorization'] = 'Bearer $token';
      return handler.next(options);
    },
  ));

  return dio;
});
```

## 4. Repository Implementation Pattern

```dart
class UserRepositoryImpl implements UserRepository {
  final UserRemoteDataSource _remote;

  UserRepositoryImpl(this._remote);

  @override
  Future<Either<Failure, User>> getUser(String id) async {
    try {
      final userModel = await _remote.fetchUser(id);
      return Right(userModel.toDomain());
    } on DioException catch (e) {
      return Left(ServerFailure(e.message));
    } catch (e) {
      return Left(UnknownFailure(e.toString()));
    }
  }
}
```
