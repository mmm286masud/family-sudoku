# Family Sudoku — Testing and Code Quality Plan

## Testing Goal
Make sure accounts, Sudoku gameplay, saved progress, private dashboards and account settings work correctly and securely.

All checks below are planned, not yet executed.

## Unit Tests — pytest
Test individual Python functions without starting the full application.

- Valid Sudoku solution is accepted.
- Duplicate family characters in a row are rejected.
- Duplicate characters in a column or 3x3 box are rejected.
- Incomplete Sudoku boards are not considered solved.
- Invalid board sizes or unsupported character values are rejected.
- Completion-time calculations handle boundary values.

## Integration Tests — pytest and Flask Test Client
Test how Flask, authentication and SQLite work together.

- A user can register with valid information.
- Duplicate usernames or emails are rejected.
- Correct login credentials are accepted.
- Incorrect passwords are rejected.
- An authenticated player can save a puzzle.
- Saved progress remains available after logout and login.
- A player cannot read or modify another player's saved games.
- Account updates require authentication.
- Completed games are recorded only after server-side validation.

## End-to-End Tests — Browser
Test complete user workflows.

1. Register, log in, start a puzzle and save progress.
2. Log out, log back in and resume the saved puzzle.
3. Complete a valid puzzle and view the result in the dashboard.
4. Update account information and confirm the change.
5. Verify that protected pages are unavailable after logout.

Automated browser testing may be added later if practical.

## Test Data and Edge Cases
Use synthetic test accounts and fixed Sudoku puzzles with known solutions.

Test:
- Empty input
- Invalid login credentials
- Duplicate account information
- Incorrect and incomplete puzzles
- Unexpected character values
- Board dimensions other than 9x9
- Empty game history
- Unauthorized access to another user's records

## Local Testing
Planned command:

```bash
python -m pytest
```

Run fast unit tests frequently while developing. Run integration tests when backend or database functionality changes.

## Code Quality
Planned Python tools:
- Ruff for formatting and linting
- pytest for automated tests
- pip-audit for dependency vulnerability checks, subject to setup

Planned commands after installing and configuring the tools:

```bash
ruff format --check .
ruff check .
python -m pytest
pip-audit
```

Python code should use consistent naming, readable functions and clearly separated responsibilities. Formatting, lint and test failures must be investigated and fixed before merging.

JavaScript should also follow consistent formatting and basic browser-console error checks. A dedicated JavaScript linter may be chosen when the frontend is implemented.

## Continuous Integration
Plan to configure GitHub Actions to run Python formatting, linting and automated tests on pushes and pull requests.

Local checks should provide quick feedback. CI should repeat important automated checks rather than running expensive browser tests unnecessarily.

## Checking Acceptance Criteria
The five user stories in docs/plan.md will be connected to appropriate unit, integration or end-to-end checks as development progresses.

## Reporting Results
Every check will be marked as:
- Planned: Not yet run.
- Attempted: Run but not confirmed successful.
- Observed: Actual outcome recorded with evidence.

## Current Status
All tests and quality checks are planned. No application tests or CI workflows have been run yet.
