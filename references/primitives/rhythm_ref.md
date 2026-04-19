# Musicpy Rhythm Reference

The `rhythm` structure allows for precise control over the temporal aspect of musical notes, enabling the creation of syncopation, swing, and complex polyrhythms.

## 1. Core Components
- **Notes/Chords**: The musical content (e.g., `N('C5')`, `C('Cmaj7')`).
- **Duration**: The length of the event (e. 
g., `1/4`, `1/8`, `1/16`).
- **Rest**: Silence included in the sequence.

## 2. Creating Rhythmic Patterns

### Simple Rhythmic Sequence
Using the `rhythm` object to define a sequence of note durations.
```python
from musicpy import *

# A sequence of 8th and 16th notes
r = rhythm('1/8 1/8 1/16 1/16 1/8 1/8 1/16 1/16', 1)
notes = [N('C5'), N('E5'), N('G5'), N('B5'), N('C6'), N('B5'), N('G5'), N('E5')]

# Map notes to the rhythm
melody = track(content=notes, duration=r)
play(melody)
```

### Using Rests for Syncopation
Incorporate rests directly into the rhythmic string to create "gaps."
```python
from musicpy import *

# A rhythm with rests (represented by 0 or 'r')
syncopated_rhythm = '1/8 0 1/16 1/16 1/8 0 1/8 1/8'
notes = [N('C5'), N('E5'), N('G5'), N('B5'), N('C6'), N('G5'), N('E5'), N('C5')]

melody = track(content=notes, duration=syncopated_rhythm)
play(melody)
```

## 3. Polyrhythms and Polyrhythmic Logic
Polyrhythms involve playing two or more different rhythms simultaneously (e.g., 3 against 4).

### 3:4 Polyrhythm Example
```python
from musicpy import *

# 3-note pattern in 4/4 time
pattern_3 = track(content=C('C5', 1/4), instrument=1, start_time=0)
pattern_3 += track(content=C('E5', 1/4), instrument=1, start_time=0.5)
pattern_3 += track(content=C('G5', 1/4), instrument=1, start_time=1.0)

# 4-note pattern
pattern_4 = track(content=C('C5', 1/4), instrument=2, start_time=0)
pattern_4 += track(content=C('G5', 1/4), instrument=2, start_time=0.75)
pattern_4 += track(content=C('E5', 1/4), instrument=2, start_time=1.5)

piece = piece(tracks=[pattern_3, pattern_4], bpm=120)
play(piece)
```
