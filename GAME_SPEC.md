# Taxonle - Taxonomy Guessing Game Specification

## Game Concept
Taxonle is a web-based guessing game inspired by Metazooa where players try to discover a mystery animal by guessing other animals and observing their taxonomic relationships. Each guess reveals how much taxonomy the guessed animal shares with the target animal.

## Core Mechanics

### Gameplay
1. A random target animal is selected from the database
2. Player has 20 guesses to find the target animal
3. Each guess reveals the deepest common taxonomic level shared with the target
4. A visual tree displays the shared taxonomic path
5. Animals branch off the tree at their divergence points
6. A "???" marker shows where the mystery animal branches off
7. Closer taxonomic matches reveal deeper levels (Kingdom → Phylum → Class → Order → Family → Genus → Species)

### Winning/Losing
- **Win**: Correctly guess the target animal
- **Lose**: Use all 20 guesses without finding the target
- **Give Up**: Reveal the answer early

### Hints System
- **Hint 1** (unlocks at 5 guesses): Conservation status (e.g., "least concern", "endangered")
- **Hint 2** (unlocks at 10 guesses): Geographic distribution (e.g., "Colombia, Ecuador, Venezuela")

## UI/UX Design - Mobile-First

### Layout Structure
```
┌─────────────────────────────────────────┐
│ [☰]     🌿 Taxonle      [X/20] [❓]    │ <- Header Bar
├─────────────────────────────────────────┤
│                                         │
│                                         │
│         Tree Visualization Area         │ <- Scrollable
│         (Full middle space)             │
│                                         │
│                                         │
├─────────────────────────────────────────┤
│ [Text Input Field...      ] [Submit]   │ <- Bottom Bar
└─────────────────────────────────────────┘

Slide-out Menu (left):
┌─────────────┐
│   Menu      │
│ ─────────── │
│ 🔄 New Game │
│ 🏳️ Give Up  │
│ ⚙️ Settings  │
│             │
│ Stats       │
│ - Path: X/7 │
│ - DB: XXX   │
│             │
│ Hints       │
│ 💡 Hint btn │
└─────────────┘
```

### Header Bar
- **Left**: ☰ Menu button (opens slide-out panel)
- **Center**: 🌿 Taxonle logo/title
- **Right**:
  - Guess counter (e.g., "5/20")
  - ❓ Help button (opens help modal)

### Slide-out Menu Panel
Slides in from left, contains:
- **Game Controls**:
  - 🔄 New Game button (orange/primary)
  - 🏳️ Give Up button (red/danger)
  - ⚙️ Settings button (gray)
- **Stats Section**:
  - Path Revealed: X / 7
  - Database Size: XXX animals
- **Hints Section**:
  - 💡 Hint button (shows available/locked state)
  - Revealed hints display below button

### Tree Area
- Full-height middle section
- White background with rounded corners
- Scrollable canvas for tree visualization
- Centered alignment
- Empty state: 🌱 "Start guessing to reveal the tree!"

### Bottom Input Bar
- Fixed to bottom
- Text input field (takes most width, rounded pill shape)
- Submit button (rounded, green, inline with input)
- Autocomplete dropdown (appears ABOVE input, max 5-8 results)

### Modals
1. **Help Modal**: Game instructions, hints info, tips
2. **Settings Modal**: Taxonomy filter tree (Phylum → Class levels)
3. **Game Over Modal**: Win/lose screen with play again button

## Tree Visualization

### Visual Design
- **Top-down hierarchical layout**
- **Smooth curved SVG connections** between nodes (Bezier curves)
- **Color-coded taxonomy levels**:
  - Kingdom: Red gradient (#ff6b6b → #ee5a6f)
  - Phylum: Pink gradient (#f06595 → #e64980)
  - Class: Purple gradient (#cc5de8 → #be4bdb)
  - Order: Blue gradient (#748ffc → #5c7cfa)
  - Family: Light blue gradient (#4dabf7 → #339af0)
  - Genus: Teal gradient (#38d9a9 → #20c997)
  - Species: Green gradient (#82c91e → #5c940d)
  - Target (when found): Gold gradient (#ffd43b → #fab005)
  - Mystery (???): Gray gradient with dashed border

### Tree Structure
- **Shared path**: Shows taxonomy levels shared by all guesses up to deepest revealed level
- **Divergence points**: Animals branch off at their specific divergence level
- **Mystery marker (???)**: Always centered among animals at deepest level
- **Level labels**: Small uppercase labels above taxonomy nodes (e.g., "KINGDOM", "PHYLUM")
- **No duplicates**: Shared taxonomy nodes are reused
- **Dynamic positioning**: Tree adjusts to number of guesses

### Tree Behavior
- Each animal appears at its divergence point from the target
- Animals that share less taxonomy appear higher in the tree
- Better guesses appear deeper in the tree
- ??? marker shows the next unrevealed level

## Features

### Core Features
- ✅ 760 animals from complete taxonomy database
- ✅ Autocomplete search (by common or scientific name)
- ✅ 20 guesses per game
- ✅ Visual taxonomy tree with smooth curved connections
- ✅ Color-coded taxonomy levels
- ✅ Hint system (2 hints: conservation status, distribution)
- ✅ Give up option
- ✅ Win/lose detection
- ✅ New game functionality

### Advanced Features
- ✅ **Taxonomy Filter**: Click taxonomy groups (Phylum/Class level) to enable/disable
  - Phylum and Class nodes in a tree structure
  - Click to toggle gray-out
  - Apply button starts new game with filtered pool
- ✅ **Well-known animals prioritized**: Common animals (Giraffe, Polar Bear, etc.) appear more frequently
- ✅ **Mobile-responsive**: Works perfectly on all screen sizes
- ✅ **No scrolling needed**: Everything visible on screen
- ✅ **Smooth animations**: Fade-in for new nodes, hover effects

## Technical Requirements

### Tech Stack
- **Single HTML file** with embedded CSS and JavaScript
- **No frameworks** - Vanilla JavaScript only
- **No build process** - Ready to deploy as static file
- **External dependencies**: None (except JSON data file)

### Data Structure
Animals JSON format:
```json
[
  {
    "commonName": "Polar Bear",
    "scientificName": "Ursus maritimus",
    "phylum": "Chordata",
    "class": "Mammalia",
    "order": "Carnivora",
    "family": "Ursidae",
    "genus": "Ursus",
    "specificEpithet": "maritimus",
    "distribution": "Arctic Circle, Canada, Russia, Greenland, Norway, United States",
    "threatStatus": "vulnerable"
  }
]
```

### Key Functions Needed
1. **loadAnimals()**: Fetch and load animals_data.json
2. **startNewGame()**: Initialize new game with random target
3. **makeGuess()**: Validate and process player guess
4. **compareWithTarget()**: Find deepest common taxonomy level
5. **buildTreeStructure()**: Create hierarchical tree data
6. **renderTreeNode()**: Recursively render tree HTML
7. **drawConnections()**: Draw SVG curved lines between nodes
8. **updateHintButton()**: Update hint availability
9. **showHint()**: Reveal next available hint
10. **toggleMenu()**: Show/hide slide-out menu
11. **openHelp/Settings/GameOver()**: Modal management
12. **getFilteredAnimals()**: Apply taxonomy filters
13. **selectAnimal()**: Autocomplete selection
14. **winGame/loseGame/giveUp()**: Game end states

### Game State Variables
```javascript
let animals = [];              // All animals from JSON
let targetAnimal = null;       // Mystery animal to guess
let guesses = [];              // Array of guessed animals
let guessCount = 0;            // Number of guesses made
let gameOver = false;          // Game end flag
let deepestLevel = 0;          // Deepest revealed taxonomy level
let hintsUsed = 0;             // Number of hints revealed
let disabledPaths = new Set(); // Taxonomy filter settings
```

### Autocomplete Behavior
- Triggers after 2+ characters typed
- Searches both common name and scientific name
- Shows max 8 results
- Displays: **Common Name** (large) + *Scientific Name* (small italic)
- Click to select
- Dropdown appears ABOVE input field
- Closes on click outside

### Responsive Design
- **Mobile (<768px)**:
  - Header bar compact
  - Single column layout
  - Tree area takes full width
  - Menu panel 280px wide
- **Desktop (≥768px)**:
  - Wider header spacing
  - Tree area expands
  - Larger node sizes
  - Same layout structure

## Color Scheme
- **Primary Green**: #52c234 (buttons, highlights)
- **Dark Green**: #2d7a1f (text, headers)
- **Gradient Background**: #52c234 → #a8d530
- **White**: Panels, cards, modals
- **Gray**: #6c757d (secondary buttons)
- **Orange**: #ffa500 (New Game button)
- **Red**: #dc3545 (Give Up button)

## User Flow

### First Visit
1. Page loads → "Loading animal kingdom..." message
2. JSON loads → Game initializes
3. Tree shows: 🌱 "Start guessing to reveal the tree!"
4. Input ready at bottom

### Playing
1. Type animal name → Autocomplete suggests
2. Select or press Enter → Guess processed
3. Tree updates with new branch
4. Counter updates (X/20)
5. If 5 or 10 guesses → Hint unlocks (check menu)
6. Repeat until win/lose

### Winning
1. Modal appears: "🎉 You Found It!"
2. Shows: Animal name, scientific name, guess count
3. "Play Again" button → Starts new game

### Losing
1. Modal appears: "Game Over!"
2. Shows: Correct answer
3. "Try Again" button → Starts new game

### Give Up
1. Confirmation dialog: "Are you sure?"
2. If yes → Tree reveals full path to answer
3. Modal shows answer
4. "Try Again" button available

## Performance Considerations
- Tree rendering should be smooth for up to 20 animals
- SVG line drawing optimized with requestAnimationFrame
- Autocomplete debounced/throttled for performance
- JSON loads once on page load
- No unnecessary re-renders

## Browser Support
- Chrome/Edge (latest)
- Firefox (latest)
- Safari (latest)
- Mobile browsers (iOS Safari, Chrome Mobile)

## Accessibility
- Keyboard navigation (Enter to submit, Escape to close modals)
- Focus states on interactive elements
- Semantic HTML structure
- ARIA labels where needed
- Touch-friendly button sizes (min 44x44px)

## Game Balance
- 20 guesses is sufficient for most games
- Hints at 5 and 10 guesses provide good pacing
- 760 animals provides good variety
- Well-known animals prioritized for better UX
- Taxonomy filter allows difficulty adjustment

## Future Enhancements (Not Required)
- Daily challenge mode (same animal for all players)
- Statistics tracking (games played, win rate, streaks)
- Share results (emoji grid like Wordle)
- Sound effects
- Dark mode
- Multiple hint types
- Timer mode
- Leaderboard

## Files Needed in Repository
1. **index.html** - Main game file (HTML + CSS + JS in one file)
2. **animals_data.json** - Animal database (760 animals with all fields)
3. **README.md** - Project documentation
4. **.gitignore** - Git ignore file
5. **vercel.json** (optional) - Deployment configuration

## Deployment
- Static site hosting (Vercel, Netlify, GitHub Pages)
- No server-side code needed
- No environment variables needed
- Just serve index.html and animals_data.json

---

## Design Principles
1. **Mobile-first**: Design for mobile, enhance for desktop
2. **No scrolling**: Everything fits on screen
3. **Sleek & modern**: Clean UI with smooth animations
4. **Fast & responsive**: Instant feedback on all actions
5. **Intuitive**: No tutorial needed, learn by playing
6. **Accessible**: Works for everyone
