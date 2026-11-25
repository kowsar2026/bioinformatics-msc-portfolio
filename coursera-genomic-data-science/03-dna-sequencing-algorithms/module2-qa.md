# Module 2: Preprocessing, indexing and approximate matching (my Q&A)

Date: Nov 25, 2026
Course: Algorithms for DNA Sequencing (Johns Hopkins, Coursera)

## Lectures I finished today
- Practical: Implementing Boyer-Moore
- Preprocessing
- Indexing and the k-mer index
- Ordered structures for indexing
- Hash tables for indexing

## Q1: All 4-mers of ACGTAC
- 0 = ACGT
- 1 = CGTA
- 2 = GTAC

## Q2: Finding TTAC using a 3-mer index of GATTACA
Index: 0 = GAT, 1 = ATT, 2 = TTA, 3 = TAC, 4 = ACA

1. Take the first 3 letters of the pattern: TTA.
2. Look it up in the index: it is at position 2.
3. Check the next letter in the text (position 5). It is C, which matches the last letter of TTAC.
4. So TTAC is found at position 2.

## Q3: Hash table vs sorted list
A sorted list uses binary search to find the match. A hash table uses math (a hash function) to jump straight to the slot in one step.


**Why is max(shift, skip_bc, skip_gs) safe?**
Each rule only skips positions where the pattern cannot match. Both rules are safe, so the larger shift skips the most positions and still misses no match.

**What does "occurrences" hold, and when is something added?**
It holds the starting positions in the text where the whole pattern was found. A position is added only when the loop finishes with no mismatch.

**Why build the tables once, before the search?**
The tables depend only on the pattern, not on the text. After they are built, each mismatch needs only a quick lookup instead of working the answer out again.

**Why index the text when we have many patterns?**
The text doesn't change, so we index it once. Each new pattern then needs only quick lookups of its k-mers and a check of the hits, instead of scanning the whole text again.

