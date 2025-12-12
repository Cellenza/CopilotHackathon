# GitHub Copilot Instructions

## Priority Guidelines

When generating code for this repository:

1. **Version Compatibility**: Always detect and respect the exact versions of languages, frameworks, and libraries used in this project
2. **Context Files**: Prioritize patterns and standards defined in the .github/copilot directory
3. **Codebase Patterns**: When context files don't provide specific guidance, scan the codebase for established patterns
4. **Architectural Consistency**: Maintain our layered architectural style and established boundaries
5. **Code Quality**: Prioritize maintainability, testability, and consistency in all generated code

## Technology Version Detection

Before generating code, scan the codebase to identify:

1. **Language Versions**: Detect the exact versions of programming languages in use
   - Examine project files, configuration files, and package managers
   - Look for language-specific version indicators (e.g., <LangVersion> in .NET projects, <TargetFramework> tags)
   - Never use language features beyond the detected version

2. **Framework Versions**: Identify the exact versions of all frameworks
   - Check package.json, .csproj, pom.xml, requirements.txt, etc.
   - Respect version constraints when generating code
   - Never suggest features not available in the detected framework versions

3. **Library Versions**: Note the exact versions of key libraries and dependencies
   - Generate code compatible with these specific versions
   - Never use APIs or features not available in the detected versions

## Repository Structure

This is a multi-language GitHub Copilot Hackathon repository with the following structure:

- **cpp/**: C++ exercises and challenges
- **dotnet/**: .NET/C# exercises and challenges using .NET 8.0
- **java/**: Java exercises and challenges
- **javascript/**: JavaScript exercises and challenges
- **nodejs/**: Node.js exercises and challenges
- **python/**: Python exercises and challenges

Each language directory contains:
- **01-commands/**: Basic exercises focused on slash commands (doc, explain, fix, tests)
- **02-challenges/** or **02-exercises/**: More advanced implementation challenges

## Technology-Specific Guidelines

### .NET Guidelines

**Detected Version**: .NET 8.0

- Use only C# language features compatible with .NET 8.0
- Follow namespace conventions: use file-scoped namespaces where appropriate
- **Naming Conventions**:
  - Classes: PascalCase (e.g., `Account`, `BankingTransactionDTO`)
  - Methods: PascalCase (e.g., `Deposit`, `Withdraw`, `GetBalance`)
  - Properties: PascalCase with public/private access modifiers
  - Local variables: camelCase
  - Test methods: Descriptive names with underscores (e.g., `WhenAPrintStatementIsAskedAfterTheFirstDeposit_DateAmountAndBalanceArePrinted`)
- **Testing Framework**: xUnit (version 2.4.2)
  - Use `[Fact]` attribute for simple tests
  - Follow Arrange-Act-Assert pattern with comments
  - Use descriptive test names that explain the scenario and expected outcome
- **Documentation**: Use XML documentation comments (///) for public classes and methods
- **Access Modifiers**: Use `internal` for classes not exposed outside assembly
- **Collections**: Use generic collections (`List<T>`, `Dictionary<K,V>`)
- **Dependency Injection**: Follow established DI patterns in challenge projects

### Java Guidelines

**Detected Version**: Java with JUnit 5 (Jupiter)

- Follow standard Java naming conventions
- **Package Structure**: `com.training.app` or similar patterns
- **Naming Conventions**:
  - Classes: PascalCase (e.g., `Account`, `BankingTransactionDTO`)
  - Methods: camelCase (e.g., `deposit`, `withdraw`, `getBalance`)
  - Fields: camelCase with private access
  - Constants: UPPER_SNAKE_CASE
- **Testing Framework**: JUnit Jupiter (version 5.10.0)
  - Use `@Test` annotation
  - Follow clear test naming conventions
  - Use `assertEquals`, `assertTrue`, etc.
- **Date/Time**: Use `java.time` package (e.g., `LocalDate.now()`)
- **Collections**: Use generic collections (`List<T>`, `ArrayList<T>`)
- **Access Modifiers**: Use appropriate visibility (private fields, public methods)

### JavaScript/Node.js Guidelines

**Detected Version**: Node.js with Jest testing framework

- Use ES6+ features consistently
- **Module System**: Use CommonJS (`require`/`module.exports`) as evident in codebase
- **Naming Conventions**:
  - Classes: PascalCase (e.g., `Account`, `BankingTransactionDTO`)
  - Functions/Methods: camelCase (e.g., `deposit`, `getBalance`)
  - Files: camelCase or PascalCase matching class names
- **Testing Framework**: Jest (version 29.7.0)
  - Use `test()` function for test cases
  - Use `expect()` for assertions
  - Mock console.log and other side effects using `jest.spyOn()`
  - Clean up mocks with `.mockRestore()`
- **Class Structure**: Use ES6 classes with constructors
- **Dependencies**: 
  - Express (4.21.2) for web applications
  - Use `require()` for importing modules
- **Error Handling**: Follow established patterns in existing code
- **Date/Time**: Use standard `Date` object

### Python Guidelines

**Detected Version**: Python 3.x with Flask and pytest

- Follow PEP 8 style guide
- **Naming Conventions**:
  - Classes: PascalCase (e.g., `Account`, `BankingTransactionDTO`)
  - Functions/Methods: snake_case (e.g., `deposit`, `withdraw`)
  - Files: snake_case (e.g., `account.py`, `banking_transaction_dto.py`)
  - Test files: suffix with `_test.py`
- **Import Style**: 
  - Use absolute imports
  - Import specific items from modules (e.g., `from datetime import date`)
- **Testing Framework**: pytest with Flask-Testing
  - Follow clear test function naming
  - Use descriptive test names
- **Web Framework**: Flask (version 3.0.3)
- **Date/Time**: Use `datetime` module (e.g., `date.today()`)
- **Class Structure**: Use `__init__` constructors
- **Collections**: Use built-in list and dict types

### C++ Guidelines

- Follow modern C++ practices
- **Naming Conventions**: Follow established patterns in existing code
- **File Organization**: Separate headers (.h) and implementations (.cpp)
- **Testing**: Follow established testing patterns in codebase

## Code Quality Standards

### Maintainability
- Write self-documenting code with clear naming
- Follow the naming and organization conventions evident in the codebase
- Follow established patterns for consistency
- Keep functions focused on single responsibilities
- Limit function complexity and length to match existing patterns

### Testability
- Follow established patterns for testable code
- Match dependency injection approaches used in the codebase
- Apply the same patterns for managing dependencies
- Follow established mocking and test double patterns
- Match the testing style used in existing tests

## Documentation Requirements

- Match the level and style of comments found in existing code
- Document according to patterns observed in the codebase
- Follow existing patterns for documenting non-obvious behavior
- Use the same format for parameter descriptions as existing code
- For .NET: Use XML documentation comments for public APIs
- For JavaScript: Use JSDoc style if present
- For Java: Use JavaDoc for public APIs
- For Python: Use docstrings for classes and functions where appropriate

## Testing Approach

### Unit Testing

Each language has its own testing framework and patterns:

- **.NET**: xUnit with Arrange-Act-Assert pattern
  - Clear test method names describing scenario and outcome
  - Use `[Fact]` for tests
  - Include comments for Arrange, Act, Assert sections
  
- **JavaScript/Node.js**: Jest
  - Use `test()` function with descriptive names
  - Use `expect()` assertions
  - Mock external dependencies appropriately
  
- **Java**: JUnit 5
  - Use `@Test` annotation
  - Follow standard assertion patterns
  
- **Python**: pytest
  - Function-based tests with descriptive names
  - Use pytest assertions

### Test Naming Conventions

- **.NET**: `WhenCondition_ExpectedBehavior` with underscores
- **JavaScript**: Descriptive strings in `test()` function
- **Java**: `testScenarioDescription` in camelCase
- **Python**: `test_scenario_description` in snake_case

## Codebase Scanning Instructions

When context files don't provide specific guidance:

1. Identify similar files to the one being modified or created
2. Analyze patterns for:
   - Naming conventions
   - Code organization
   - Error handling
   - Logging approaches
   - Documentation style
   - Testing patterns
   
3. Follow the most consistent patterns found in the codebase
4. When conflicting patterns exist, prioritize patterns in newer files or files with higher test coverage
5. Never introduce patterns not found in the existing codebase

## Project-Specific Patterns

### Banking Kata Pattern

The repository contains a recurring "Banking Kata" exercise across multiple languages with consistent business logic:

- **Account**: Core class managing balance and transaction history
  - Properties: balance, statement (list of transactions)
  - Methods: deposit, withdraw, getBalance/getStatement
  
- **BankingTransactionDTO**: Data transfer object for transactions
  - Properties: date, amount, balance
  
- **AccountStatementPrint**: Utility for printing account statements
  - Method: print/PrintStatement
  - Format: "Date Amount Balance" with transaction rows

When implementing similar patterns, follow the established structure in the target language.

### API Structure (for challenges)

For web API challenges:
- **Node.js**: Use Express.js with middleware pattern
  - Route handlers in controllers
  - Business logic in services
  - Error handlers as middleware
  
- **.NET**: Use Minimal API or ASP.NET Core patterns
  - RESTful endpoints
  - Dependency injection
  - Entity Framework Core for data access (where applicable)

## General Best Practices

- Follow naming conventions exactly as they appear in existing code for the target language
- Match code organization patterns from similar files
- Apply error handling consistent with existing patterns
- Follow the same approach to testing as seen in the codebase
- Match logging patterns from existing code (if present)
- Use the same approach to configuration as seen in the codebase
- When working with dates: use Date() in JS, DateTime in .NET, LocalDate in Java, date in Python

## Language-Specific File Naming

- **.NET**: PascalCase.cs (e.g., Account.cs, BankingTransactionDTO.cs)
- **Java**: PascalCase.java with package path structure
- **JavaScript/Node.js**: camelCase.js or PascalCase.js matching class name
- **Python**: snake_case.py (e.g., account.py, banking_transaction_dto.py)
- **C++**: Various patterns for .h and .cpp files

## Context Files Priority

Prioritize the following files in .github directory (if they exist):

1. **copilot-instructions.md** (this file): Primary instructions
2. **instructions/angular.instructions.md**: Angular-specific guidance
3. **prompts/*.prompt.md**: Specialized prompt templates for specific tasks

## Project-Specific Guidance

- Scan the codebase thoroughly before generating any code
- Respect existing architectural boundaries without exception
- Match the style and patterns of surrounding code in the target language
- When in doubt, prioritize consistency with existing code over external best practices
- This is an educational repository - code should be clear and demonstrate best practices for learning purposes
- Tests are a critical part of the learning experience - always follow established testing patterns
