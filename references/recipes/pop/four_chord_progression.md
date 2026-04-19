# Pop: The Four-Chord Progression

Many pop hits use the I-V-vi-IV progression.

```python
from musicpy import *

# Progression: C - G - Am - F
progression = C('C') | C('G') | C('Am') | C('F')

# Create a simple synth melody
melody = [N('E5'), N('G5'), N('A5'), N('F5')]
melody_track = track(content=melody, instrument=81)

# Create the chords
chord_track = track(content=progression, instrument=88)

pop_song = piece(tracks=[melody_track, chord_track], bpm=120)
play(pop_song)
```
