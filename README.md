# Animals Complete Dataset

## Overview

This repository contains a comprehensive taxonomic dataset of animal species with detailed information about their taxonomy, distribution, conservation status, and characteristics.

## 🎮 Taxonle - Taxonomy Tree Discovery Game

An interactive Metazooa-style browser game where you discover a mystery animal through taxonomy!

**Play the game:** Open `index.html` in your browser

### How to Play

1. A mystery animal is randomly selected from the dataset
2. Guess any animal by common or scientific name
3. The tree reveals what taxonomic levels your guess shares with the target
4. Each guess shows you how close you are (Kingdom → Phylum → Class → Order → Family → Genus → Species)
5. The **???** marker appears at the next unrevealed level, showing where the mystery animal branches off
6. Use clues from shared taxonomy to deduce the target animal
7. You have 20 guesses to find it!

### Features

- **760 animals** from the dataset
- **Metazooa-style gameplay** - discover through shared taxonomy
- **Visual tree** showing all guessed animals and the mystery placeholder
- **Color-coded levels** from red (Kingdom) to green (Species)
- **Autocomplete search** for easy animal selection
- **Give Up button** to reveal the answer if stuck
- **Guess history** tracking all attempts
- **Responsive design** works on desktop and mobile
- **Fully client-side** - no server required!

### Example

If the target is a **Lion**:
- Guess "Dog" → Reveals: Animalia → Chordata → Mammalia → Carnivora (then diverges)
- Tree shows ??? at Family level (you haven't reached Felidae yet)
- Guess "House Cat" → Reveals deeper: All the way to Felidae
- Now ??? moves to Genus level
- Keep guessing to narrow it down!

## Dataset File

**File:** `animals_complete.tsv`
**Format:** Tab-separated values (TSV)
**Records:** 760 animal species
**Size:** ~285 KB

## Structure

The dataset contains 18 columns with the following fields:

| Column | Description |
|--------|-------------|
| `taxonID` | Unique identifier for the taxon |
| `commonName` | Common name of the species |
| `scientificName` | Full scientific name with authorship |
| `canonicalName` | Canonical form of the scientific name |
| `scientificNameAuthorship` | Author and year of scientific description |
| `family` | Taxonomic family |
| `genus` | Taxonomic genus |
| `class` | Taxonomic class |
| `order` | Taxonomic order |
| `phylum` | Taxonomic phylum |
| `distribution` | Geographic distribution (countries/regions) |
| `threatStatus` | Conservation status (e.g., least concern, endangered) |
| `description` | Detailed description including ecology, feeding, and behavior |
| `taxonRank` | Taxonomic rank (primarily species) |
| `taxonomicStatus` | Status (e.g., accepted) |
| `genericName` | Genus name component |
| `specificEpithet` | Species name component |
| `infraspecificEpithet` | Subspecies name component (if applicable) |

## Dataset Statistics

### Distribution by Class

- **Birds (Aves):** 352 species (46%)
- **Mammals (Mammalia):** 253 species (33%)
- **Amphibians (Amphibia):** 89 species (12%)
- **Insects (Insecta):** 37 species (5%)
- **Crustaceans (Malacostraca):** 13 species (2%)
- **Mollusks (Gastropoda):** 9 species (1%)
- **Arachnids (Arachnida):** 7 species (1%)

### Data Completeness

- All 760 records include taxonomic classification
- All 760 records include geographic distribution data
- Most records include detailed ecological descriptions

## Example Record

```
taxonID: 2433573
commonName: Kinkaju
scientificName: Potos flavus (Schreber, 1774)
family: Procyonidae
genus: Potos
class: Mammalia
order: Carnivora
phylum: Chordata
distribution: Colombia, Ecuador, Germany, Venezuela
threatStatus: least concern, vulnerable
```

## Usage

The dataset can be loaded using standard TSV/CSV parsing tools:

**Python:**
```python
import pandas as pd
df = pd.read_csv('animals_complete.tsv', sep='\t')
```

**R:**
```r
df <- read.delim('animals_complete.tsv', sep='\t')
```

## Notes

- Multiple threat statuses may be listed for a single species, indicating different assessments or regional variations
- Description fields contain rich text with detailed information about diet, behavior, habitat, and subspecies
- Some fields may be empty for certain records (particularly `infraspecificEpithet` for species without subspecies designation)
