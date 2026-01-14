# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Rat Factor is a tennis score tracking Progressive Web App (PWA) for a group of 4 players: Rick, Ed, Tom, and Jethro. It tracks three match types: Singles (1v1), Doubles (2v2), and "Rat Factor" (Canadian doubles - 3 players).

## Architecture

This is a **single-file application** - all HTML, CSS, and JavaScript are contained in `index.html`. There is no build step.

### Tech Stack
- **Frontend**: Vanilla JavaScript, HTML, CSS (no frameworks)
- **Backend**: Supabase (PostgreSQL) via `@supabase/supabase-js` CDN
- **Fonts**: Google Fonts (Bebas Neue, Space Mono)

### Key Sections in index.html
- **Lines 15-924**: CSS styles including CSS variables for theming
- **Lines 926-996**: HTML structure with navigation tabs and 4 sections (Home, Log Match, History, H2H)
- **Lines 1000-1957**: JavaScript application logic

### Database Schema
The app uses a single `matches` table in Supabase with these key fields:
- `match_type`: 'singles', 'doubles', or 'canadian'
- `player1`, `player2`, `player3`, `player4`: player names
- `winner1`, `winner2`: winner(s) of the match
- `score_player1`, `score_player2`, `score_player3`: scores for Rat Factor matches
- `sets`: JSON string for doubles set scores
- `target_score`: target score for Rat Factor matches (7 or 11)
- `created_at`: timestamp

### Rat Factor Championship Rules
- **Scoring per match**: 1st place = 3 points, 2nd place = 1 point, 3rd place = 0 points
- Only **best 10 results** count toward year-end championship
- Players can play **unlimited** Rat Factor matches throughout the year
- Championship leaderboard shows each player's top 10 scores combined

### Future Implementation Needed
1. Update database to store finishing position (1st/2nd/3rd) for each player in Rat Factor matches
2. Update match entry form to capture placements for all 3 players
3. Create Rat Factor championship leaderboard that calculates best-10 scores

## Development

To develop locally, simply open `index.html` in a browser. The app connects directly to the Supabase backend.

For changes to work, you need access to the Supabase project (credentials are in the file).

## PWA Support

The `manifest.json` enables installation as a Progressive Web App on mobile devices.
