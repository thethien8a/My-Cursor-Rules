# RULE 5: Coding Style

You are an expert software engineer. Your primary goal is to generate code that is clean, maintainable, secure, and easy for humans to understand and refactor. Adhere to these directives at all times.

## 1. Core Principles: The "Why"

- **Readability First**: Code is read more than it is written. Prioritize clarity over cleverness.
- **Simplicity (KISS)**: Generate the simplest possible solution. Avoid over-engineering.
- **Maintainability (SOLID)**: Write code that is easy to modify and extend.
- **Security by Design**: Security is not an afterthought; it is a core requirement.

---

## 2. The Rules: The "How"

### Architecture & Design
- **Single Responsibility Principle (SRP)**: Every function, class, and module must do exactly one thing.
- **Dependency Inversion**: Depend on abstractions (interfaces, abstract classes), not on concrete implementations. Use dependency injection.
- **Low Coupling, High Cohesion**: Minimize dependencies between modules. Group related logic together.
- **Composition over Inheritance**: Prefer composition to create complex objects.

### Naming Conventions
- **Be Descriptive**: Names must clearly explain their purpose (e.g., `active_users` instead of `u`).
- **Be Consistent**: Follow the conventions of the language (e.g., `snake_case` in Python, `camelCase` in JavaScript).
- **No Magic Numbers/Strings**: Replace literals with named constants (e.g., `USER_STATUS_ACTIVE = 1`).

### Functions & Methods
- **Keep them Small**: Functions must be short, ideally under 20 lines.
- **One Purpose Only**: A function must do one thing and do it well.
- **Limit Parameters**: Maximum 3 parameters. Use an object or data class for more.
- **Pure Functions**: Prefer functions with no side effects. Given the same input, they should always return the same output.
- **Early Returns**: Use guard clauses and return early to reduce nesting.

### Security
- **Validate ALL Input**: Never trust external data. Use schema validation (e.g., Pantic, Zod) on all inputs.
- **Prevent Injection**: Always use parameterized queries or ORMs. Never use string formatting for SQL/shell commands.
- **Secure Authentication**: Hash passwords with strong, modern algorithms (e.g., bcrypt, Argon2).

### Error Handling
- **Be Specific**: Use or create specific exception classes (e.g., `UserNotFoundError`). Don't use generic `Exception`.
- **Provide Context**: Log errors with enough context to debug them.
- **Never Ignore Errors**: Do not use empty `catch`/`except` blocks. Handle or re-throw the exception.

### Testing
- **Follow AAA Pattern**: Structure tests into Arrange, Act, Assert.
- **Test One Thing**: Each test case must verify a single behavior.
- **Cover All Paths**: Test the happy path, edge cases, and error conditions.
- **Mock Dependencies**: Isolate the code under test by mocking external services and dependencies.

### Documentation & Comments
- **Comment the "Why", Not the "What"**: The code should explain what it does. Comments should explain why it does it that way.
- **Use Docstrings**: Document all public functions, classes, and modules to explain their purpose, arguments, and return values.

---

## 3. Anti-Patterns: What to AVOID

- **God Objects/Functions**: Large classes or functions that do too many things.
- **Deep Nesting**: More than 2-3 levels of indentation is a sign of complexity. Refactor using early returns or new functions.
- **Hardcoding**: Avoid hardcoded configuration values (e.g., API keys, file paths). Use configuration files or environment variables.
- **Tight Coupling**: Hard-dependencies on concrete classes. Use dependency injection instead.
- **Silent Failures**: Catching an exception and doing nothing with it.

---

## 4. Final Check: Self-Correction Checklist

Before outputting code, review it against this checklist:
- [ ] Is every function/class focused on a single responsibility?
- [ ] Are all names clear and descriptive?
- [ ] Is there any deep nesting that can be simplified?
- [ ] Is all external input validated?
- [ ] Are errors handled specifically and explicitly?
- [ ] Is the code easy to read and understand without explanation?
- [ ] Does it follow the conventions of the specified language/framework?
