# Prompt for Building Taxonle

Use this prompt when working with an LLM to build the game from scratch:

---

## Main Prompt

```
I need you to build a web-based taxonomy guessing game called "Taxonle" based on the detailed specification in GAME_SPEC.md.

The game is inspired by Metazooa and Wordle - players guess animals to discover a mystery target animal by observing taxonomic relationships.

Key requirements:
- Single HTML file with embedded CSS and JavaScript (no frameworks)
- Mobile-first design with no scrolling needed
- Sleek header bar: Menu button (left), Title (center), Counter + Help (right)
- Slide-out menu panel from left side with game controls, stats, and hints
- Full-height tree visualization area in the middle (scrollable canvas)
- Bottom input bar with text field and submit button side-by-side
- Visual taxonomy tree with colored nodes and smooth curved SVG connections
- 760 animals loaded from animals_data.json
- Autocomplete search, hint system, taxonomy filters
- Win/lose/give up states with modal overlays

Please read GAME_SPEC.md thoroughly for complete details on:
- Game mechanics and rules
- UI/UX layout and design
- Tree visualization structure
- Color scheme and styling
- All required features and functions
- Technical implementation details

Build the complete index.html file with all functionality integrated.
The design should be modern, sleek, and work perfectly on mobile devices.

Focus on:
1. Clean, readable code
2. Smooth animations and transitions
3. Responsive design (mobile-first)
4. No external dependencies
5. Single-file deployment ready

Additional context files provided:
- GAME_SPEC.md (detailed specification)
- animals_data.json (animal database)
```

---

## Follow-up Prompts (if needed)

### If tree rendering needs refinement:
```
The taxonomy tree needs to:
1. Show only the shared taxonomic path (no full branches for each animal)
2. Place animals at their specific divergence points
3. Keep the ??? mystery marker centered among animals at the deepest level
4. Use smooth Bezier curves for connections
5. Color-code each taxonomy level
Please review the tree visualization section in GAME_SPEC.md and update the buildTreeStructure() and renderTreeNode() functions.
```

### If mobile layout needs adjustment:
```
Ensure the layout is truly mobile-first with:
1. No scrolling needed for the main view
2. Header, tree area, and input bar fill 100vh exactly
3. Tree area is flex:1 and scrollable
4. Slide-out menu is 280px wide
5. All touch targets are at least 44x44px
Please verify the CSS uses flexbox with fixed header/input and flexible tree area.
```

### If hint system needs fixing:
```
The hint system should:
1. Unlock hint 1 at 5 guesses (conservation status)
2. Unlock hint 2 at 10 guesses (geographic distribution)
3. Show available/locked state in menu button
4. Display hints in the slide-out menu below the hint button
5. Update button text based on state
Please check the updateHintButton() and showHint() functions.
```

---

## Validation Checklist

Ask the LLM to confirm:
- [ ] Single HTML file with embedded CSS/JS
- [ ] Mobile-responsive (works on phones)
- [ ] No scrolling on main view (100vh layout)
- [ ] Header bar with menu, title, counter, help
- [ ] Slide-out menu from left with all controls
- [ ] Bottom input bar with autocomplete
- [ ] Tree visualization with colored nodes
- [ ] Smooth SVG curved connections
- [ ] All 10+ functions implemented
- [ ] Hint system working (5 and 10 guesses)
- [ ] Win/lose/give up modals
- [ ] Settings with taxonomy filter
- [ ] Help modal with instructions
- [ ] Ready to deploy (just add JSON file)
