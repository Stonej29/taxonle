# Animals Complete Dataset

## Overview

This repository contains a comprehensive taxonomic dataset of animal species with detailed information about their taxonomy, distribution, conservation status, and characteristics.

## 🎮 Animal Taxonomy Wordle Game

An interactive browser-based game where you guess animals based on their taxonomic classification!

**Play the game:** Open `index.html` in your browser

### How to Play

1. The game randomly selects a target animal from the dataset
2. Enter your guess using either the common name or scientific name
3. After each guess, see how your animal's taxonomy compares to the target:
   - 🟢 **Green** = Taxonomy level matches
   - 🔴 **Red** = Taxonomy level doesn't match
4. You have 6 attempts to guess the correct animal
5. Use the autocomplete feature to help find animals in the database

### Features

- **760 animals** from the dataset
- **Autocomplete search** for easy animal selection
- **Visual feedback** with color-coded taxonomy comparison
- **Responsive design** works on desktop and mobile
- **Guess history** shows all your previous attempts
- **Fully client-side** - no server required!

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
