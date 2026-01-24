# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a simple Korean-language random lottery/drawing application built as a single-file HTML page. The application allows users to enter up to 10 participant names, randomly select a winner, and export drawing results to CSV format.

## Running the Application

Open `index.html` directly in a web browser. No build process, server, or dependencies required.

## Code Structure

The entire application is contained in `index.html`:
- **HTML**: 10 input fields for participant names, two action buttons, and a result display area
- **CSS**: Embedded styles using flexbox and grid layout
- **JavaScript**: Two main functions:
  - `drawWinner()`: Validates inputs, randomly selects from non-empty entries, displays result, and logs to results array
  - `exportToExcel()`: Exports timestamped results to a CSV file with filename format `draw_results_YYYYMMDD_HHMMSS.csv`

## Key Implementation Details

- The `results` array tracks all drawing history with timestamps for the session
- The `startTime` variable captures when the page loads, used for CSV filename generation
- CSV export uses data URI scheme with dynamic link creation/removal
- Random selection uses `Math.random()` with array index calculation
