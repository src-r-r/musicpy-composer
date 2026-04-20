# Advanced: Negative Harmony Implementation

Negative harmony involves reflecting notes across a specific axis (usually the axis between the tonic and the minor fifth).

```python
from musicpy import *

# Define a standard melody
melody = [N('C4'), N('E4'), N('G4'), N('B4')]

# Applying negative harmony relative to C major
# In musicpy, the '@' operator can be used for this
# We define the scale to use as the axis
c_major = S('C major')
negative_melody = melody @ c_major

# Create a piece to compare
track_original = track(content=melody, instrument=1)
track_negative = track(content=negative_melody, instrument=2)

comparison_piece = piece(tracks=[track_original, track_negative], bpm=100)
play(comparison_piece)
```
