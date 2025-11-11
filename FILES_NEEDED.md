# Files Needed for New Repository

## Required Files

### 1. index.html
**Purpose**: Main game file
**Contents**: Complete HTML + CSS + JavaScript in a single file
**Size**: ~1500-2000 lines
**Location**: Root of repository
**Source**: Build from GAME_SPEC.md or copy from current working version

### 2. animals_data.json
**Purpose**: Animal database
**Contents**: Array of 760 animals with taxonomy and hint data
**Size**: ~280 KB
**Location**: Root of repository
**Source**: Copy from current repo

Format:
```json
[
  {
    "commonName": "Animal Name",
    "scientificName": "Scientific Name",
    "phylum": "...",
    "class": "...",
    "order": "...",
    "family": "...",
    "genus": "...",
    "specificEpithet": "...",
    "distribution": "Geographic location",
    "threatStatus": "Conservation status"
  }
]
```

### 3. README.md
**Purpose**: Project documentation
**Contents**: Game description, features, how to play, deployment instructions
**Size**: ~100-200 lines
**Location**: Root of repository
**Source**: Create new (template below)

### 4. .gitignore
**Purpose**: Git ignore file
**Contents**: Standard ignores for web projects
**Size**: ~20 lines
**Location**: Root of repository

```
# OS
.DS_Store
Thumbs.db

# Editors
.vscode/
.idea/
*.swp
*.swo
*~

# Logs
*.log
npm-debug.log*

# Misc
.env
.env.local
```

### 5. vercel.json (optional)
**Purpose**: Vercel deployment configuration
**Contents**: Deployment settings
**Size**: ~10-20 lines
**Location**: Root of repository

```json
{
  "version": 2,
  "builds": [
    {
      "src": "index.html",
      "use": "@vercel/static"
    }
  ],
  "routes": [
    {
      "src": "/(.*)",
      "dest": "/$1"
    }
  ]
}
```

---

## Optional Files

### LICENSE
**Purpose**: Open source license
**Suggestion**: MIT License

### .prettierrc (optional)
**Purpose**: Code formatting configuration

### package.json (optional)
**Purpose**: Only if you want npm scripts for local development
**Note**: Not required - this is a static site

---

## Repository Structure

```
taxonle/
├── index.html              # Main game file (REQUIRED)
├── animals_data.json       # Animal database (REQUIRED)
├── README.md              # Documentation (REQUIRED)
├── .gitignore             # Git ignore (REQUIRED)
├── vercel.json            # Deployment config (OPTIONAL)
├── LICENSE                # License file (OPTIONAL)
└── docs/                  # Optional documentation folder
    ├── GAME_SPEC.md       # Game specification
    └── screenshots/       # Game screenshots
```

---

## README.md Template

```markdown
# 🌿 Taxonle

A web-based taxonomy guessing game where you discover mystery animals through taxonomic relationships.

## 🎮 How to Play

1. A random mystery animal is selected
2. Guess animals to reveal shared taxonomy
3. The tree shows taxonomic relationships
4. Use hints and strategy to find the target
5. Win by guessing correctly within 20 tries!

## ✨ Features

- 🌳 Visual taxonomy tree with smooth animations
- 🔍 Autocomplete search (760 animals)
- 💡 Hint system (unlocks at 5 and 10 guesses)
- ⚙️ Taxonomy filter (customize difficulty)
- 📱 Mobile-first responsive design
- 🎨 Beautiful color-coded taxonomy levels
- ⚡ Fast and lightweight (no dependencies)

## 🚀 Live Demo

[Play Taxonle →](https://your-deployment-url.vercel.app)

## 🛠️ Tech Stack

- Pure HTML/CSS/JavaScript (no frameworks)
- Single-file deployment
- Static site (no backend needed)

## 📦 Deployment

### Vercel (Recommended)
1. Fork this repository
2. Import to Vercel
3. Deploy!

### Other Static Hosts
Works on Netlify, GitHub Pages, Cloudflare Pages, etc.
Just serve `index.html` and `animals_data.json`.

## 🧬 Taxonomy Levels

- Kingdom (Red)
- Phylum (Pink)
- Class (Purple)
- Order (Blue)
- Family (Light Blue)
- Genus (Teal)
- Species (Green)

## 🎯 Game Rules

- 20 guesses per game
- Hint 1: Conservation status (unlocks at 5 guesses)
- Hint 2: Geographic distribution (unlocks at 10 guesses)
- Give up option reveals the answer
- Taxonomy filter lets you customize difficulty

## 📄 License

MIT License - feel free to fork and modify!

## 🙏 Credits

Inspired by [Metazooa](https://metazooa.com) and Wordle.
Animal data from biodiversity databases.
```

---

## How to Set Up New Repository

1. **Create repository on GitHub**
   ```bash
   gh repo create taxonle --public
   ```

2. **Add files**
   ```bash
   # Copy these files to new repo:
   cp index.html /path/to/new/repo/
   cp animals_data.json /path/to/new/repo/
   # Create README, .gitignore, vercel.json
   ```

3. **Initial commit**
   ```bash
   cd /path/to/new/repo
   git init
   git add .
   git commit -m "Initial commit: Taxonle game"
   git branch -M main
   git remote add origin https://github.com/yourusername/taxonle.git
   git push -u origin main
   ```

4. **Deploy to Vercel**
   ```bash
   vercel --prod
   # Or link repository in Vercel dashboard
   ```

---

## File Checklist

Before creating the repository, ensure you have:

- [x] index.html (complete working game)
- [x] animals_data.json (760 animals with all fields)
- [x] README.md (project documentation)
- [x] .gitignore (standard web ignores)
- [x] GAME_SPEC.md (in docs/ or root - optional but helpful)
- [x] LLM_PROMPT.md (in docs/ - for future development)
- [x] vercel.json (if deploying to Vercel)
- [x] LICENSE (if open source)

**Minimum required for deployment: index.html + animals_data.json**
