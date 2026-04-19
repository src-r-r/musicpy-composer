# Musicpy DAW & Export Reference

This module provides instructions for interfacing `musicpy` with Digital Audio Workstations (DAWs) and controlling MIDI via the `daw` module.

## 1. MIDI Export Pipeline
The primary way to move music from `musicpy` to a DAW is via MIDI files.

### Standard Export
```python
from musicpy import *

# Define your piece
track1 = track(content=C('Cmaj7'), instrument=1)
track2 = track(content=C('G7'), instrument=2)
result = piece(tracks=[track1, track2], bpm=120)

# Write to MIDI
write(result, 'my_composition.mid')
```

### Advanced Orchestration for Multi-Track DAWs
When exporting for a DAW, organize your `piece` so that each `track` contains a single instrument.

```python
from musicpy import *

# Define separate tracks for different instruments
piano = track(content=C('Cmaj7', 1/4), instrument=1) # Piano
strings = track(content=C('Cmaj7', 1/2), instrument=49) # Strings
bass = track(content=C('C1'), instrument=32) # Bass

# Use 'piece' to group them with a single BPM and start times
orchestration = piece(
    tracks=[piano, strings, bass],
    instruments=[1, 49, 32],
    bpm=100,
    start_times=[0, 0, 0]
)

write(orchestration, 'orchestra_export.mid')
```

## 2. Automation & MIDI CC (Continuous Controller)
While `musicpy` is structural, you can simulate automation by modulating volume or pan over time within a track.

### Volume Swells (Expressive Dynamics)
Create a track where the volume changes per note to simulate a "swelling" effect.
```python
from musicpy import *

# Define a sequence of volumes for a swell effect
swell_volumes = [40, 60, 80, 100, 80, 60, 40]
notes = [N('C5'), N('E5'), N('G5'), N('B5'), N('C6'), N('B5'), N('G5')]

# Apply volume changes using the '%' operator
swell_track = track(content=notes, volume=swell_volumes)
play(swell_track)
```

### Panning Automation
Simulate a stereo field movement by changing the `pan` attribute.
```python
from musicpy import *

# Move from left (0%) to right (100%)
panning_notes = [N('C5'), N('E5'), N('G5'), N('B5')]
panning_values = [0, 33, 66, 100]

pan_track = track(content=panning_notes, pan=panning_values)
play(pan_track)
```

## 3. Integration Tips
- **Note Duration**: Ensure durations in `musicpy` are aligned with your DAW's grid (e.g., 1/4, 1/8).
- **Track Naming**: While `musicpy` doesn't support track names in MIDI, use distinct `instrument` MIDI numbers to help identify tracks in your DAW.
- **Time Signature**: While `musicpy` handles rhythm mathematically, Ensure your `piece` rhythm is compatible with your DAW's project time signature.
