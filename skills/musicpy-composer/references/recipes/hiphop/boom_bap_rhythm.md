# Hip-Hop: Boom Bap Drum Pattern

A classic Boom Bap pattern relies on a strong kick on the 1, a snare on the 2 and 4, and swinging hi-hats.

```python
from musicpy import *

# Hi-hat pattern: continuous 8th notes with slight velocity variation
hihats = rhythm('h h h h h h h h', 1/8)
hihat_track = track(content=hihats, instrument=42, volume=[100, 80, 90, 70, 100, 80, 90, 70])

# Kick and Snare pattern
# Kick on 1 and the 'and' of 2
# Snare on 2 and 4
kick_snare_rhythm = rhythm('k . s . k . s .', 1/4)
kick_snare_track = track(content=kick_snare_rhythm, instrument=11)

# Combine into a loop
boom_bap = piece(tracks=[hihat_track, kick_snare_track], bpm=90)
play(boom_bap)
```
