# Musicpy Interval Reference

This reference provides a quick lookup table for musical `Interval` objects used in `musicpy` for transpositions, chord construction, and melodic transformations.

## 1. Interval Lookup Table
Intervals are represented by their musical name (e.g., `P5`, `m3`).

| Interval Name | Symbol | Semitones | Description |
| :--- | :--- | :--- | :--- |
| Perfect Unison | `P1` | 0 | The same pitch |
| Minor Second | `m2` | 1 | |
| Major Second | `M2` | 2 | |
| Minor Third | `m3` | 3 | |
| Major Third | `M3` | 4 | |
| Perfect Fourth | `P4` | 5 | |
| Tritone | `A4` / `d5`| 6 | Augmented 4th / Diminished 5th |
| Perfect Fifth | `P5` | 7 | |
| Minor Sixth | `m6` | 8 | |
| Major Sixth | `M6` | 9 | |
| Minor Seventh | `m7` | 10 | |
| Major Seventh | `M7` | 11 | |
| Perfect Octave | `P8` | 12 | |

## 2. Using Intervals in Code

### Transposing Notes/Chords
Use the interval to shift pitch up or down.

```python
from musicpy import *

# Transpose a note up a Major Third
note = N('C4')
transposed_note = note + M3 
print(f"Original: {note.name}, Transposed: {transposed_note.name}")

# Transpose a chord up a Perfect Fifth
chord = C('Cmaj7')
transposed_chord = chord + P5
print(f"Original: {chord}, Transposed: {transposed_chord}")
```

### Constructing Chords from Intervals
Building a chord by defining the intervallic structure from a root.

```python
from musicpy import *

# Building a Minor triad (Root, m3, P5)
root = N('A4')
minor_triad = chord([root, root + m3, root + P5])
print(f"Minor Triad: {minor_triad}")

# Building a Dominant 7th (Root, M3, P5, m7)
dom7 = chord([root, root + M3, root + P5, root + m7])
print(f"Dominant 7th: {dom7}")
```

### Checking Intervals Between Notes
Checking the distance between two notes in a melody.

```python
from musicpy import *

mel_note = N('G4')
root_note = N('C4')
interval = mel_note - root_note

if interval == P5:
    print("A perfect fifth interval detected!")
```
