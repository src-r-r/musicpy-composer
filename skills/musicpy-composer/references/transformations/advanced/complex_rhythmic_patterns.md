# Advanced: Complex Rhythmic Patterns (Polyrhythms)

Polyrhythms involve playing two different rhythms simultaneously (e.g., 3 over 2).

```python
from musicpy import *

# 3-over-2 polyrhythm
# Pattern A: 2 beats of 1/4 notes
pattern_a = [N('C4', 1/4), N('C4', 1/4)]

# Pattern B: 3 beats of 1/6 notes (triplets) in the same 2/4 time
pattern_b = [N('G4', 1/6), N('G4', 1/6), N('G4', 1/6)]

track_a = track(content=pattern_a, instrument=1)
track_b = track(content=pattern_b, instrument=2)

polyrhythm_piece = piece(tracks=[track_a, track_b], bpm=120)
play(polyrhythm_piece)
```
