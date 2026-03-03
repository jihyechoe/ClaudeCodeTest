# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a browser-based Tic Tac Toe game implemented as a single HTML file with embedded CSS and JavaScript. The game includes:
- Interactive 3x3 game board
- Turn tracking (X vs O)
- Win detection (8 possible winning combinations)
- Tie detection
- Score tracking across multiple games
- Visual feedback with animations and hover effects

## Architecture

**Single File Structure:**
- `tictactoe.html`: Contains all HTML markup, CSS styling, and JavaScript logic

### Code Organization

1. **Markup (lines 123-155)**: Game UI with board grid, status display, score boxes, and reset button
2. **Styles (lines 7-121)**: Dark theme styling with responsive design, hover effects, and win animations
3. **JavaScript (lines 157-227)**:
   - `WINS`: Array of 8 winning combinations (rows, columns, diagonals)
   - `board`: Array representing the 3x3 game state
   - `checkWin()`: Detects winning condition for current player
   - `handleClick()`: Main game logic for moves, win/tie detection, score updates
   - `updateScores()`: Updates the score display

## Running the Game

Simply open the HTML file in a browser:
```bash
open tictactoe.html
# or manually open the file in your browser
```

## Git Workflow

After making changes:
1. Test the changes by opening the file in a browser
2. Stage and commit with a clear message: `git add . && git commit -m "Description"`
3. Push to GitHub: `git push origin main`

Keep commits atomic and focused on single features or fixes.

## Key Development Notes

- The game board is a flat 9-element array (indices 0-8 map to 3x3 grid positions)
- CSS classes on cells: `x` and `o` for styling, `taken` to prevent re-clicking, `win` for animation
- Score state is stored in a `scores` object (X, O, T for ties)
- No external dependencies - fully self-contained
