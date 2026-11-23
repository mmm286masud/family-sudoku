# Family Sudoku — Project Plan

## Problem and Audience
Traditional Sudoku uses numbers. Family Sudoku replaces them with nine recognizable family characters to provide a more visual puzzle experience for players of all ages.

## Project Comparison
**Family Sudoku:** A puzzle game with user accounts, saved progress, completed-game history and character-based Sudoku gameplay.

**Memory Time Capsule:** A non-game application for saving personal memories, messages and photos in a private timeline.

**Decision:** Family Sudoku was selected because it offers a distinctive visual concept and a manageable gameplay scope.

## In Scope
- Registration, login and logout
- 9x9 family-character Sudoku puzzles
- Save and resume games
- Private game dashboard and history
- Account information updates

## Out of Scope for the First Version
- Multiplayer
- Online leaderboards
- Mobile app releases
- Complex character animations
- Large collections of procedurally generated puzzles

## Five User Stories and Acceptance Criteria
1. **Account access:** As a player, I want to create an account and log in so that I can access my progress. Acceptance: A player can register, log out and log back in.
2. **Gameplay:** As a player, I want to solve Sudoku using family characters so that the game feels more engaging. Acceptance: Nine characters are supported and valid solutions are checked correctly.
3. **Saved progress:** As a player, I want to save unfinished games so that I can continue later. Acceptance: A saved game is restored after logging back in.
4. **Dashboard:** As a player, I want to review completed puzzles and best times so that I can track my progress. Acceptance: Only the player's own results appear.
5. **Account maintenance:** As a player, I want to update my account information. Acceptance: The player can securely update a username or password.

## Prioritized Backlog
| Priority | Task | Dependency |
| --- | --- | --- |
| High | Create a working Sudoku board with one predefined puzzle | None |
| High | Implement registration and login | Database setup |
| High | Save and resume puzzles | Authentication and game board |
| High | Implement puzzle validation | Sudoku rules |
| High | Create a private dashboard | Saved and completed results |
| High | Implement account updates | Authentication |
| Medium | Add automated tests and CI checks | Features under test |
| Medium | Compare character selection methods | Working board |
| Low | Add visual polish and extra puzzles | Core gameplay |

## Development Milestones
1. Basic working Sudoku board
2. Accounts and security
3. Save and resume functionality
4. Dashboard and completed-game history
5. Tests, creative experiment and improvements

## Ownership and Review
Initial implementation owner: Individual project developer.
Peer reviewer: To be assigned during class review.
Feedback will be documented in GitHub issues with a decision, linked changes, verification and reviewer retry when available.

## Dependencies and First Working Slice
Begin with a fixed Sudoku puzzle and character-selection interface. Implement server-side accounts and a saved-game workflow before adding extra visual features.

## Open Questions
- Which character-selection method is easier: drag-and-drop or click-to-select?
- Which puzzle difficulties should be included in the first version?
- Which hosting service will support the Flask application and persistent database?

## Current Status
Planning only. Features, tests and creative experiment are not yet implemented or executed.


## Peer Review Feedback

### Issue #1: Add Family Sudoku Game Preview

**Original feedback:** A classmate suggested adding a
visual preview of the Sudoku board so readers could
understand how family characters replace numbers.

**Decision:** Accepted.

**Change implemented:** Added a pixel-art game preview
using the Family Sudoku character designs.

**Verification:** The image was displayed successfully
on the published research website.

**Reviewer retry:** Completed. After reviewing the
updated website, the classmate said the preview made
it much easier to imagine the game and understand
what the final product would look like.

**GitHub Issue:**
https://github.com/mmm286masud/family-sudoku/issues/1

**Updated Website:**
https://mmm286masud.github.io/family-sudoku/

**Status:** Resolved — issue closed.
