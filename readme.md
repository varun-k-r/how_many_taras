# Jataka Rebirths Dataset

Analysis of the various forms that the Bodhisattva takes across all 547 Jataka Tales — the canonical collection of the Buddha's past lives in the Theravada Pali Canon.

## Source

[Table of the Jātaka Stories](https://ancient-buddhist-texts.net/English-Texts/Jataka/000-Jataka-Table.htm#gsc.tab=0) at Ancient Buddhist Texts, compiled by Ānandajoti Bhikkhu. Character mappings, synopses, and keywords are drawn from the Jātaka-aṭṭhakathā commentary tradition, with the English translation based on the PTS edition by Fausböll.

## Summary

| Metric | Value |
|---|---|
| Stories | 547 |
| Character-incarnation rows | 1,448 |
| Male characters | 1,258 (86.9%) |
| Female characters | 190 (13.1%) |
| Sex ratio | 151 females per 1,000 males |
| Bodhisattva incarnations | 547 |
| Bodhisattva as female | 0 |

## The Bodhisattva's Forms

The Bodhisattva appears in every story — as human, animal, or divine being. Across all 547 tales, the Bodhisattva is **male in every single incarnation**.
Surprising, given that Tara — the most famous female Buddha in many Buddhist schools of thought — embodies the feminine dimension/version of Buddha.

### By broad category

| Category | Count | Share |
|---|---|---|
| Human | 352 | 64.4% |
| Animal | 127 | 23.2% |
| Divine/Supernatural | 68 | 12.4% |

### Top incarnation forms

| Species | Count |
|---|---|
| Human (king, minister, ascetic, merchant, etc.) | 352 |
| Deva (Sakka, Tree Devatā, Brahma, etc.) | 65 |
| Monkey | 13 |
| Deer | 12 |
| Parrot | 12 |
| Horse | 9 |
| Goose | 9 |
| Lion | 9 |
| Bird (generic) | 7 |
| Pigeon | 6 |
| Elephant | 6 |
| Bull/Ox | 5 |
| Quail | 5 |
| Vulture | 4 |
| Fish | 3 |
| Rat | 3 |
| Iguana | 3 |
| Crow | 3 |
| Nāga | 3 |

## Sex Ratio by Category

Even the animals are overwhelmingly male. Zero female monkeys, jackals, parrots, snakes, quails, turtles, tigers, or dogs across all 547 stories.

| Category | Male | Female | Females per 1,000 males |
|---|---|---|---|
| Human | 821 | 155 | 189 |
| Animal | 328 | 30 | 91 |
| Divine/Supernatural | 109 | 5 | 46 |

The few female animals are mostly does (deer), female crocodiles (wives trying to eat the Bodhisattva's heart), and elephant cows.

## Devadatta as Antagonist

Devadatta — the Buddha's rival cousin — appears in 81 stories (14.8%), almost always as antagonist. His incarnation forms mirror the Bodhisattva's but skew toward trickster animals:

| Species | Count |
|---|---|
| Human | 45 |
| Jackal | 7 |
| Crocodile | 5 |
| Monkey | 5 |
| Deer | 2 |
| Falcon | 2 |
| Crow | 2 |
| Elephant | 2 |

## Recurring Characters

The Jataka tales map present-day figures to their past-life identities. The most frequently recurring:

| Present identity | Appearances | Typical past-life role |
|---|---|---|
| Bodhisattva (the Buddha) | 538 | Protagonist in every story |
| Ānanda | 157 | King, supporter, companion |
| Sāriputta | 99 | Wise minister, teacher, ally |
| Devadatta | 81 | Antagonist, fool, trickster |
| Uppalavaṇṇā | 29 | Mother, sister, queen |
| Moggallāna | 28 | Supporting character |
| Anuruddha | 26 | Sakka (King of Devas), king |
| Rāhula | 18 | Son, young prince, nephew |

## Schema

| Column | Type | Description |
|---|---|---|
| `story_id` | string | Jataka number (e.g., "Ja 11") |
| `story_title` | string | Pali title |
| `story_title_eng` | string | English title translation |
| `nipata` | string | Section (1s = one verse, 2s = two verses, etc.) |
| `character_present` | string | Present-day identity (e.g., "Ānanda", "Devadatta") |
| `character_past` | string | Past-life incarnation role and name |
| `species` | categorical | human, deva, monkey, deer, lion, jackal, etc. |
| `sex` | categorical | male, female |
| `role_type` | categorical | protagonist, antagonist, supporting |
| `is_bodhisatta` | categorical | yes/no |
| `keywords` | string | Moral themes and content tags from the source |

## Files

| File | Description |
|---|---|
| `jataka_rebirths.csv` | One row per character per story (1,448 rows) |
| `jataka_sex_ratio_by_category.csv` | Sex ratio by human/animal/divine |
| `jataka_sex_ratio_by_species.csv` | Sex ratio by species (45 species) |
| `readme.md` | This file |

## Notes on Data Quality

1. **Sex inference**: Determined from Pali gendered terms (miga/migī, maccha/macchī), role descriptions ("mother," "queen," "doe"), and known gender of present-day characters (Uppalavaṇṇā = female, Ānanda = male). Approximately 95% confidence; edge cases involve genderless Devas and animals without explicit markers.

2. **Species inference**: Parsed from role descriptions. Defaults to "human" when no animal or divine keyword is present. "Deva" covers Sakka, Tree Devatās, Brahma, Sea Devatās, and other divine beings. "Naga" is distinct from "elephant" (hatthināga).

3. **Group characters excluded**: Entries like "the Buddha's disciples = the rest of the cast" are omitted as they don't represent individual incarnations.

4. **Bodhisattva count**: The parser finds the Bodhisattva in 538 stories under the name "Bodhisatta" and in the remaining 9 under variant spellings or reversed line order. All 547 stories have a Bodhisattva entry.

## Citation

Ānandajoti Bhikkhu, comp. "Table of the Jātaka Stories." Ancient Buddhist Texts. https://ancient-buddhist-texts.net/English-Texts/Jataka/000-Jataka-Table.htm

Fausböll, V., ed. *The Jātaka, Together with Its Commentary.* 7 vols. London: Pali Text Society, 1877–1897.
