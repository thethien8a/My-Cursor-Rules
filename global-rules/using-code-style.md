# RULE 4: CODING STYLE
> Generate maintainable, secure, and professional code following industry best practices

## CORE PRINCIPLES

**Clean Code Fundamentals:**
- Code must read like prose - clear and understandable at first glance
- Keep it simple - avoid over-engineering and unnecessary complexity
- Be consistent - same patterns and style throughout the entire codebase
- Self-documenting - code should explain its purpose without excessive comments

**SOLID Principles (Apply Always):**
- Single Responsibility: Each function/class has one clear purpose
- Open/Closed: Open for extension, closed for modification
- Liskov Substitution: Subtypes must be substitutable for their base types
- Interface Segregation: Many small interfaces better than one large interface
- Dependency Inversion: Depend on abstractions, not concrete implementations

---

## NAMING CONVENTIONS

**Universal Rules:**
- Use descriptive, searchable names - no single letters except loop counters
- Avoid abbreviations and mental mapping - be explicit
- Replace magic numbers with named constants
- Follow language-specific conventions consistently

**Python Examples:**
```python
# ❌ BAD
d = datetime.now()
u = [x for x in users if x.a]
if status == 1:

# ✅ GOOD
current_date = datetime.now()
active_users = [user for user in users if user.is_active]
USER_STATUS_ACTIVE = 1
if status == USER_STATUS_ACTIVE:
```

**Naming Patterns:**
- Variables/Functions: snake_case (Python), camelCase (JS/Java), PascalCase (C#)
- Constants: UPPER_SNAKE_CASE (all languages)
- Classes: PascalCase (all languages)
- Private members: _leading_underscore (Python), camelCase (others)

---

## CODE STRUCTURE

**Function Rules:**
- Maximum 20-30 lines per function
- Maximum 3 parameters - use objects/dictionaries for more
- Single responsibility - one function does one thing well
- Avoid side effects - pure functions when possible
- Use descriptive names that explain what the function does

**Python Example:**
```python
# ❌ BAD - Does everything
def process_user(user_data):
    if not user_data.get('email'):
        raise ValueError('Email required')
    user_data['email'] = user_data['email'].lower()
    database.save(user_data)
    send_welcome_email(user_data['email'])

# ✅ GOOD - Separated concerns
def validate_user_email(user_data):
    if not user_data.get('email'):
        raise ValueError('Email required')

def normalize_user_data(user_data):
    normalized = user_data.copy()
    normalized['email'] = normalized['email'].lower()
    return normalized

def create_user(user_data):
    validate_user_email(user_data)
    normalized_data = normalize_user_data(user_data)
    user = database.save(normalized_data)
    send_welcome_email(user.email)
    return user
```

**Class Structure:**
- Small classes with single responsibility
- High cohesion - related functionality together
- Low coupling - minimal dependencies between classes
- Use composition over inheritance when possible

**File Organization:**
- Group related functionality together
- Separate concerns into different modules/packages
- Keep configuration separate from business logic
- Use clear directory structure that reflects architecture

---

## SECURITY FIRST

**Input Validation (Always Required):**
- Validate all input data before processing
- Use schema validation libraries
- Sanitize data to prevent injection attacks
- Never trust user input

**Python Example:**
```python
# ✅ Always validate input
from pydantic import BaseModel, EmailStr, validator

class UserInput(BaseModel):
    email: EmailStr
    password: str
    age: int
    
    @validator('password')
    def validate_password(cls, value):
        if len(value) < 8:
            raise ValueError('Password must be at least 8 characters')
        return value
    
    @validator('age')
    def validate_age(cls, value):
        if not 13 <= value <= 120:
            raise ValueError('Age must be between 13 and 120')
        return value
```

**Security Measures:**
- SQL Injection: Always use parameterized queries, never string concatenation
- XSS Prevention: Sanitize all outputs, escape HTML content
- Authentication: Use secure password hashing (bcrypt, Argon2)
- Authorization: Check permissions on every request
- HTTPS: Use TLS for all communications
- Rate Limiting: Prevent abuse and DoS attacks

---

## ERROR HANDLING

**Custom Exception Classes:**
```python
class UserNotFoundError(Exception):
    def __init__(self, user_id):
        super().__init__(f"User with ID {user_id} not found")
        self.status_code = 404

class ValidationError(Exception):
    def __init__(self, message, field=None):
        super().__init__(message)
        self.field = field
        self.status_code = 400
```

**Error Handling Rules:**
- Use built-in exception types when appropriate
- Create custom exceptions for domain-specific errors
- Log errors with sufficient context for debugging
- Never expose internal system details to users
- Provide graceful fallbacks when possible
- Use try-catch blocks appropriately - don't catch and ignore

---

## TESTING

**Test Structure (AAA Pattern):**
```python
def test_create_user_with_valid_data():
    # Arrange
    user_data = {
        'email': 'test@example.com',
        'password': 'securepassword123',
        'name': 'Test User'
    }
    
    # Act
    user = user_service.create_user(user_data)
    
    # Assert
    assert user.email == user_data['email']
    assert user.id is not None
    assert user.created_at is not None
```

**Testing Principles:**
- Write tests before or immediately after implementation
- Test one thing at a time - focused test cases
- Use descriptive test names that explain the scenario
- Follow the testing pyramid: many unit tests, some integration tests, few E2E tests
- Mock external dependencies in unit tests
- Test both happy path and error scenarios

---

## PERFORMANCE

**Efficient Code Practices:**
```python
# ✅ Use appropriate data structures
user_lookup = {}  # O(1) lookup instead of list iteration
unique_emails = set()  # O(1) membership test

# ✅ List comprehensions for filtering/mapping
active_users = [user for user in users if user.is_active]
user_emails = [user.email for user in active_users]

# ✅ Generators for large datasets
def process_large_dataset(data):
    for item in data:
        processed_item = expensive_operation(item)
        yield processed_item

# ✅ Early returns to avoid unnecessary processing
def validate_user(user):
    if not user:
        return False
    if not user.email:
        return False
    if not user.is_verified:
        return False
    return True
```

**Performance Rules:**
- Choose the right data structure for the task
- Avoid premature optimization - measure first
- Use caching strategically for expensive operations
- Implement pagination for large datasets
- Use database indexes appropriately
- Minimize network calls and database queries

---

## DOCUMENTATION

**Comment Guidelines:**
```python
# ❌ BAD - Obvious comment
users = []  # List to store users

# ✅ GOOD - Explains why
# Cache user data for 5 minutes to reduce database load
user_cache = {}

# ✅ GOOD - Complex business logic explanation
def calculate_discount(user, order_total):
    """
    Calculate discount based on user tier and order history.
    
    Premium users: 15% discount on orders > $100
    Regular users: 5% discount on orders > $200
    New users: 10% welcome discount on first order
    """
    if user.is_premium and order_total > 100:
        return order_total * 0.15
    elif user.order_count == 0:
        return order_total * 0.10
    elif order_total > 200:
        return order_total * 0.05
    return 0
```

**Documentation Rules:**
- Comment WHY, not WHAT - code should be self-explanatory
- Document complex business logic and algorithms
- Use docstrings for functions and classes
- Keep comments up-to-date with code changes
- Write meaningful commit messages
- Document API endpoints and data models

---

## AVOID THESE ANTI-PATTERNS

**Common Mistakes:**
```python
# ❌ God functions - too many responsibilities
def handle_user_request(request):
    # 200+ lines doing validation, processing, database operations, etc.
    pass

# ❌ Magic numbers and strings
if user.status == 1:
    pass
if role == "admin":
    pass

# ❌ Tight coupling
class UserService:
    def __init__(self):
        self.database = PostgreSQLDatabase()  # Hard dependency
        self.email_service = SMTPEmailService()  # Hard dependency

# ❌ Ignoring exceptions
try:
    risky_operation()
except:
    pass  # Silent failure

# ❌ Deep nesting
def process_data(data):
    if data:
        if data.is_valid:
            if data.user:
                if data.user.is_active:
                    # deeply nested logic
                    pass
```

**Better Alternatives:**
```python
# ✅ Single responsibility functions
def validate_user_data(data):
    pass

def save_user(data):
    pass

# ✅ Named constants
USER_STATUS_ACTIVE = 1
ROLE_ADMIN = "admin"

if user.status == USER_STATUS_ACTIVE:
    pass

# ✅ Dependency injection
class UserService:
    def __init__(self, database, email_service):
        self.database = database
        self.email_service = email_service

# ✅ Proper exception handling
try:
    result = risky_operation()
    return result
except SpecificException as e:
    logger.error(f"Operation failed: {e}")
    raise UserFriendlyError("Unable to complete request")

# ✅ Early returns to reduce nesting
def process_data(data):
    if not data:
        return None
    if not data.is_valid:
        raise ValidationError("Invalid data")
    if not data.user or not data.user.is_active:
        raise AuthorizationError("User not authorized")
    
    # main logic here
    return processed_result
```

---

## PRE-COMMIT CHECKLIST

**Code Quality:**
- [ ] Functions are under 30 lines and have single responsibility
- [ ] Variable and function names are descriptive and follow conventions
- [ ] No magic numbers or hardcoded strings
- [ ] No duplicate code - common functionality extracted
- [ ] Complex logic is documented with comments

**Security:**
- [ ] All input is validated and sanitized
- [ ] No SQL injection vulnerabilities (parameterized queries used)
- [ ] Sensitive data is properly encrypted/hashed
- [ ] Authentication and authorization checks in place

**Testing:**
- [ ] Unit tests written for new functionality
- [ ] Tests follow AAA pattern and are well-named
- [ ] Both happy path and error scenarios tested
- [ ] All tests pass

**Performance:**
- [ ] Appropriate data structures chosen
- [ ] No obvious performance bottlenecks
- [ ] Database queries optimized
- [ ] Large datasets handled with pagination/streaming

**Documentation:**
- [ ] Complex business logic documented
- [ ] API changes documented
- [ ] README updated if necessary
- [ ] Commit message is clear and descriptive

---

## FINAL PRINCIPLES

**Remember:** 
- Code is read more often than it's written - optimize for readability
- Consistency is more important than personal preference
- Security should be built in, not bolted on
- Test early, test often, test everything that can break
- Simple solutions are usually better than clever ones
- When in doubt, choose clarity over brevity

Apply these rules consistently to generate maintainable, secure, and professional code that experienced developers would be proud to write and maintain.
