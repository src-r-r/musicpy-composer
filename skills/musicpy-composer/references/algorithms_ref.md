# Musicpy Algorithmic Generation Reference

This module provides implementation patterns for generative music using randomization and mathematical logic.

## 1. Stochastic (Randomized) Composition
Use Python's `random` or `numpy` to influence `musicpy` parameters like duration, pitch, and volume.

### Gaussian (Normal) Distribution for Velocity/Volume
Instead of fixed volume, use a bell curve to create more natural dynamics.
```python
import random
from musicpy import *

# Generate a sequence of volumes using Gaussian distribution
# mean=100, standard_deviation=10
volumes = [int(random.gauss(100, 10)) for _ in range(8)]

notes = [N('C5'), N('E5'), N('G5'), N('B5')]
# Apply volumes to notes
track_with_dynamics = track(content=C('Cmaj7'), volume=volumes)
play(track_with_dynamics)
```

### Uniform Randomness for Rhythmic Density
Use `random.choice` to pick between different note durations to create "jittery" rhythms.
```python
import random
from musicpy import *

durations = [1/4, 1/8, 1/16]
melody_notes = [N('C5'), N('D5'), N('E5'), N('F5')]
rhythmic_melody = []

for note in melody_notes:
    dur = random.choice(durations)
    rhythmic_melody.append(note % (dur, 1, 100))

play(rhythmic_melody)
```

## 2. Markov Chain Melody Generation
Implement a simple transition matrix where the next note depends on the current note.

```python
import random
from musicpy import *

# Define states (notes) and transition probabilities
states = ['C5', 'E5', 'G5', 'B5']
transitions = {
    'C5': ['C5', 'E5', 'G5'],
    'E5': ['C5', 'E5', 'G5', 'B5'],
    'G5': ['C5', 'array_of_notes_logic'], # simplified
    'B5': ['C5', 'E5']
}
# Note: In practice, use a probability weight list with random.choices()

def markov_melody(start_note, length):
    current = start_note
    melody = [N(current)]
    for _ in range(length - 1):
        # Simplified logic: pick randomly from a fixed set
        next_note = random.choice(states) 
        melody.append(N(next_note))
        current = next_note
    return melody

melody = markov_melody('C5', 16)
play(melody, bpm=120)
```

## 3. Mathematical Sequences (Fibonacci/L-Systems)
Use mathematical series to determine note intervals or time intervals.

### Fibonacci-based Rhythms
```python
from musicpy import *

fib = [1, 1, 2, 3, 5, 8, 13]
# Map Fibonacci numbers to durations (1/n)
fib_durations = [1/f for f in fib]
notes = [N('C5'), N('D5'), N('E5'), N('F5'), N('G5'), N('A5'), N('B5')]

fib_track = track(content=notes, duration=fib_durations)
play(fib_track)
```
