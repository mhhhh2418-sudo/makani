# Developer Guide

## 1) Development Environment Setup Instructions
- **Visual Studio**: Install Visual Studio 2019 or later. Ensure to select the .NET desktop development workload.
- **SQL Server**: Download and install SQL Server Express. Use SQL Server Management Studio (SSMS) for database management.
- **Node.js**: Install Node.js v12 or later. Check the installation by running `node -v` and `npm -v` in the terminal.

## 2) Project Structure Explanation and Conventions
- **/src**: Contains all source code.
  - **/Controllers**: API controllers.
  - **/Models**: Data models.
  - **/Services**: Business logic.
- **/Tests**: Unit and integration tests.
- **/Migrations**: Database migrations for EF Core.

## 3) Clean Architecture Principles and Layer Responsibilities
- **Presentation Layer**: Handles incoming HTTP requests.
- **Domain Layer**: Contains business logic and domain entities.
- **Data Layer**: Interacts with the database (EF Core).
- **Services Layer**: Contains application-specific rules and logic.

## 4) Coding Standards and Naming Conventions for C#  
- Class names should be in PascalCase.
- Methods should be in PascalCase.
- Use camelCase for local variables.
- Constants should be in ALL_CAPS.

## 5) Entity Framework Core Usage Patterns and Migrations  
- Use `DbContext` for database operations.
- Execute migrations using the command `dotnet ef migrations add {MigrationName}` followed by `dotnet ef database update`.

## 6) Service Layer Implementation Guidelines  
- Services should be scoped (created per request).
- Separate interfaces from implementations for better testing.

## 7) Dependency Injection Configuration  
- Register services in the `Startup.cs` file under `ConfigureServices` method.
  - Example: `services.AddScoped<IMyService, MyService>();`

## 8) Async/Await Patterns and Best Practices  
- Use async methods for IO-bound operations.
- Always await async calls to prevent deadlocks.

## 9) Error Handling and Logging Strategies  
- Use `try-catch` blocks for error handling.
- Implement logging using `ILogger<T>` interface.

## 10) Testing Guidelines  
- Write unit tests for individual components.
- Use integration tests to verify interactions between components.

## 11) Git Workflow and Branching Strategy  
- Use feature branches for new features.
- Follow GitFlow workflow for releases.

## 12) Code Review Checklist  
- Ensure tests exist for new features.
- Check code for readability and maintainability.
- Verify correct error handling and logging.

---

*Document created on 2026-03-04 03:42:19 UTC*