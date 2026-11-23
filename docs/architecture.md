# Family Sudoku — Technical Architecture

## Architecture Overview
Family Sudoku uses a three-tier web architecture.

```text
Browser (HTML, CSS, JavaScript)
             |
       HTTP requests
             |
     Flask Backend (Python)
             |
      Database queries
             |
       SQLite Database
```

## Technology Choices
- HTML, CSS and JavaScript: Display the Sudoku board, characters and user interface.
- Python Flask: Handle authentication, game logic and server-side validation.
- SQLite: Store accounts, saved games and completed results.
- pytest: Test backend behavior.
- GitHub Actions: Planned automated test and quality checks.
- GitHub Pages: Host the separate static research website.

## Alternatives and Tradeoffs
- Flask vs Django: Flask is lighter and suitable for a small project. Django offers more built-in features but requires more setup.
- SQLite vs PostgreSQL: SQLite is simple for development and small workloads. PostgreSQL is better suited to larger hosted applications with concurrent writes.
- HTML/CSS/JavaScript vs React: Plain JavaScript reduces dependencies for a small interactive Sudoku board. React can help manage larger interfaces but adds complexity.

## Database Model
### Users
- id (primary key)
- username (unique)
- email (unique)
- password_hash
- created_at

### Saved Games
- id (primary key)
- user_id (references Users)
- puzzle
- current_board
- difficulty
- time_elapsed
- updated_at

### Completed Games
- id (primary key)
- user_id (references Users)
- puzzle_id or trusted puzzle reference
- difficulty
- completion_time
- completed_at

Each saved or completed game belongs to one user. Puzzle solutions must remain trusted server-side.

## Example Data Flow
1. The player logs in through the browser.
2. Flask authenticates the player and creates a secure session.
3. The player starts a predefined Sudoku puzzle.
4. JavaScript sends game progress to Flask.
5. Flask verifies authentication, ownership and submitted data.
6. SQLite stores the player's saved game.
7. When the player returns, Flask retrieves their saved progress.
8. On completion, Flask verifies the puzzle and records the result.

## Code Organization
- app.py: Flask application setup and configuration.
- auth.py: Registration, login, logout and account settings.
- sudoku.py: Sudoku puzzle logic and validation.
- games.py: Game creation, saving, resuming and completion.
- models.py: Database models and relationships.
- templates/: HTML pages.
- static/: CSS, JavaScript and character images.
- tests/: Automated tests.

## SOLID and Design Patterns
The project will emphasize the Single Responsibility Principle by separating authentication, game logic and persistence. Game logic should be testable without depending directly on Flask requests or database operations.

Flask routes will act as controllers, separating requests from game rules and database access. Complex patterns will be avoided unless the implementation demonstrates a clear need.

## Security
- Hash passwords using a trusted password-hashing function.
- Use secure session configuration and CSRF protection for state-changing requests.
- Validate inputs on the server.
- Check authentication and record ownership before accessing private data.
- Keep secret keys and credentials outside source control.
- Prevent submitted puzzle boards from bypassing server-side validation.

## Hosting and Costs
The research website can be hosted on GitHub Pages at no cost for a public repository. The Flask application needs separate server-capable hosting.

Hosting provider, persistent storage, backup strategy and pricing are not decided yet. SQLite persistence must be checked against the hosting provider's filesystem behavior before deployment.

## Status
All architecture, deployment and security checks are planned. The application has not yet been implemented or tested.
