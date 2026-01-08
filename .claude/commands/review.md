# Code Review Guidelines

Review the PR for:
- Logic correctness and potential bugs
- Security vulnerabilities
- Code style and maintainability
- Proper error handling

## Database Index Considerations

**Important**: Database indexes can be created using multiple approaches:
1. **Manual Index Creation**: Using SQL statements (e.g., `CREATE INDEX`) in deployment scripts or direct database operations
2. **ORM Migrations**: Using framework migration tools (SQLAlchemy migrations, Django migrations, etc.)
3. **Schema Definitions**: Using declarative schema definitions or annotations

All three approaches are valid and acceptable. Do NOT flag index creation as requiring a database migration if the code demonstrates:
- Direct SQL index creation statements
- Manual index management in deployment/setup scripts
- Explicit index definitions in schema or configuration files
- Framework-agnostic index handling

A change is only problematic if:
- An index is being added but no corresponding creation mechanism is shown
- Production deployment would fail without the index
- Documentation is missing on how/when the index is created

If indexes are created manually, that is not a deficiency and should not be flagged as a blocker.
