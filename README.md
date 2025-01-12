# Go Application Structure

This repository provides a well-organized and scalable folder structure for Go applications. It is designed to separate concerns and promote a clean architecture that is easy to maintain, extend, and test. The structure is suited for large Go applications with HTTP APIs, gRPC, databases, and caching layers.

## Folder Structure
```bash
go-app-structure/
│
├── cmd/                    # Main application entry points
│   └── app/
│      └── main.go         # Main entry point for starting the application
│
├── config/              # Application configuration setup
│
├── internal/               # Private application code (cannot be imported by external projects)
│   ├── entities/           # Domain entities (business models)
│   ├── http/
│   │   ├── controllers/    # HTTP controllers (business logic for request handling)
│   │   └── middlewares/    # HTTP middleware (e.g., authentication, logging)
│   ├── repositories/
│   │   ├── impl/           # Implementations of repository interfaces
│   │   └── interfaces/     # Repository interfaces (contracts)
│   ├── services/           # Business services (core business logic)
│   └── useCases/           # Use cases (application-specific business logic)
│
├── routes/                 # Route definitions for HTTP and gRPC
│   └── api.go              # API routing for the application
│
├── database/               # Database migrations, schema definitions, etc.
│
├── pkg/                    # Shared packages and utility functions
│
├── .env                    # Environment variables
├── .envexample             # Example .env file
├── go.mod                  # Go module file
└── README.md               # Documentation for the project
```


## Components Explained

### `cmd/`
Contains the application's entry points. Typically, you'll have subdirectories for each application you want to run (for example, an HTTP server or a gRPC server). The `main.go` file here is responsible for setting up and launching the application, handling environment configuration, and initializing services, routes, etc.

### `internal/`
This is where the core logic of the application resides. It's structured according to the principles of Clean Architecture and Domain-Driven Design (DDD).

- **entities/**: The domain entities (or models) that represent business objects, such as `User`, `Product`, etc.
- **http/controllers/**: This folder contains the HTTP controllers responsible for handling HTTP requests. Each controller corresponds to a resource (e.g., `UserController`).
- **http/middlewares/**: Middleware functions for HTTP, like logging, authentication, or CORS handling.
- **repositories/interfaces/**: Repository interfaces defining the methods to interact with the database or any persistent storage.
- **repositories/impl/**: Concrete implementations of the repository interfaces. For example, implementations for PostgreSQL, MySQL, etc.
- **services/**: Business logic or domain services, which encapsulate and manage the application's core logic.
- **useCases/**: Application services, containing use-case specific business logic. These are orchestrators that typically call services and repositories to fulfill a specific task.

### `routes/`
This folder contains the API routing logic, where HTTP and gRPC routes are defined. The routes are registered here, and controllers (handlers) are linked to specific routes.

- `api.go`: Defines routes and groups them logically (e.g., user routes, product routes, etc.).

### `database/`
Stores database-related artifacts such as migration files and SQL scripts. This allows for a clean separation of schema definitions and application logic.

### `pkg/`
Contains shared packages, such as logging, error handling, or helper functions, that can be used across the entire project. These should be reusable and independent from the business logic.

### `.env` and `.envexample`
- `.env`: The file that contains environment-specific variables like database connection strings, API keys, etc.
- `.envexample`: A template `.env` file that can be shared publicly, without sensitive data.

### `go.mod`
This file is where you define your module dependencies and versions. It allows Go to manage your project's dependencies.

## Getting Started

1. **Clone the repository:**

```bash
git clone https://github.com/Sunat2001/go-app-structure.git
cd go-app-structure
```

This structure keeps everything clean, modular, and easy to follow.

## License

This project is licensed under the [MIT license](https://opensource.org/licenses/MIT).

