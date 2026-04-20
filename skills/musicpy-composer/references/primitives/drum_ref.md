# Musicpy Drum Reference

The `drum` type is a specialized structure in `musicpy` for defining percussion patterns. It uses a string-based syntax where each element represents a MIDI note or a rhythmic subdivision.

## 1. Syntax and Structure
A `drum` definition is a string containing note identifiers separated by spaces, with an optional duration parameter.

**Syntax**: `drum('Note1 Note2 Note3 ...', scale_or_duration)`

- **Notes**: Use MIDI note names (e. 
  e.g., `K` for Kick, `S` for Snare, `H` for Hi-hat).
- **Subdivisions**: Numbers like `1/4`, `1/8`, `1/16` denote the length of the beat.

## 2. Mapping MIDI Notes to Drum Sounds
When working with `drum`, it is standard practice to map common MIDI drum numbers to characters:

| Character | MIDI Note | Instrument |
| :--- | :--- | :--- |
| `K` | 36 | Kick Drum |
| `S` | 38 | Snare Drum |
| `H` | 42 | Closed Hi-Hat |
| `O` | 46 | Open Hi-Hat |
| `C` | 49 | Clap |
| `T` | 45 | Low Tom |

## 3. Usage Examples

### Basic 4/4 Beat
A standard kick and snare pattern.
```python
from musicpy import *
beat = drum('K H S H K H S H', 1/4)
play(beat, bpm=120)
```

### Complex Syncopated Pattern
Using 1/8 and 1/16 subdivisions for hi-hats and snares.
```python
from musicpy import *
# A syncopated pattern with hi-hats and a rimshot
perc = drum('H H H H S H H H', 1/8)
play(perc, bpm=140)

# 1/16 note hi-hats with emphasis on the snare
complex_pattern = drum('H H H H S H H H', 1/16)
play(complex_pattern, bpm=90)
```

### Integrating Drum Patterns with Melodies
You can stack `drum` tracks with melodic tracks using the `piece` object.
```python
from musicpy import *

melody = track(content=C('C5', 1/4), instrument=1)
drums = track(content=drum('K H S H K H S H', 1/4), instrument=115)

composition = piece(tracks=[melody, drums], bpm=100)
play(composition)
```
