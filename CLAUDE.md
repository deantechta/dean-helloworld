# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a simple Korean-language random lottery/drawing application built as a single-file HTML page. The application allows users to enter up to 10 participant names, randomly select a winner, and export drawing results to CSV format.

## Running the Application

Open `index.html` directly in a web browser. No build process, server, or dependencies required.

## Code Structure

The entire application is contained in `index.html`:
- **HTML**: Two-stage interface
  - Stage 1 (`setupScreen`): Participant count input (1-10)
  - Stage 2 (`mainScreen`): Dynamically generated input fields, action buttons, and result display
- **CSS**: Embedded styles using flexbox and grid layout, with animations for visual effects
- **JavaScript**: Main functions
  - `createInputs()`: Dynamically creates participant input fields based on user's count selection
  - `resetSetup()`: Returns to setup screen and optionally clears results
  - `drawWinner()`: Validates inputs, randomly selects from non-empty entries, displays result with visual effects (drumroll, confetti, animations), and logs to results array
  - `startDrumRoll()`: Creates suspense by rapidly cycling through participant names before revealing winner
  - `showWinner()`: Displays final winner with animations, confetti, and background effects
  - `createConfetti()`: Generates 60 falling confetti particles with random colors and positions
  - `exportToExcel()`: Exports timestamped results to a CSV file with filename format `draw_results_YYYYMMDD_HHMMSS.csv`

## Key Implementation Details

- **Dynamic UI**: Input fields are created at runtime based on user-selected participant count (1-10 max)
- **Two-stage interface**: Setup screen for count selection, then main screen with generated inputs
- **Visual effects**: Drumroll (2 seconds of rapid name cycling), confetti animation (60 particles), winner text animations (scale, rotate, glow), and rainbow background gradient
- **State management**:
  - `results` array tracks all drawing history with timestamps for the session
  - `isDrawing` flag prevents multiple simultaneous draws
  - `startTime` variable captures when the page loads, used for CSV filename generation
- **User interactions**:
  - Enter key support for quick participant count confirmation
  - Auto-focus on first input field after creation
  - Confirmation dialog when resetting with existing results
- **CSV export**: Uses data URI scheme with dynamic link creation/removal
- **Random selection**: Uses `Math.random()` with array index calculation, filters out empty entries automatically
