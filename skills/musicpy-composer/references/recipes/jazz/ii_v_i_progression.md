# Jazz: ii-V-I Progression & Extensions

The ii-V-I progression is the cornerstone of jazz harmony. This guide demonstrates how to implement it with common jazz extensions.

```python
from musicpy import *

# Define a ii-V-I progression in C Major
# ii: Dm7, V: G7, I: Cmaj7
ii = C('Dm7')
v = C('G7')
i = C('Cmaj7')

progression = ii | v | i

# Add some jazz tension with extensions (e.g., G7alt or G13)
v_alt = C('G7alt')
progression_complex = ii | v_alt | i

# Create a simple walking bass line
bass_line = [N('D2'), N('F2'), N('G2'), N('B2'), N('C2')]
bass_track = track(content=bass_line, instrument=32)

# Create a piano voicing (using 9th, 11th, 13th)
piano_track = track(content=progression_complex, instrument=1)

piece = piece(tracks=[bass_track, piano_track], bpm=120)
play(piece)
```
