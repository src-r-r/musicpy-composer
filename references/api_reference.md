# Musicpy API Reference

This document provides a structured reference for the `musicpy` library, extracted from the official documentation.

## Core Data Structures

- **Note**: `N('C5')` or `note('C', 5)`. 
  - Parameters: `name` (e.g., 'C'), `num` (octave, e.g., 5), `duration` (length in bars), `volume` (0-127), `channel` (MIDI channel).
  - Shortcuts: `to_note('E5')` or `N('E5')`.
- **Chord**: `C('Cmaj7')` or `get_chord('C', 'maj7')`.
  - Multi-note: `chord('C5, E5, G6')`.
  - From note: `N('A3')('sus')` (Generates a chord using a note and a chord name).
- **Scale**: `S('C major')` or `scale('C', 'major')`.
- **Piece**: `P(tracks=[...], instruments=[...], start_times=[...], bpm=150)`.
- **Track**: `track(content=..., instrument=..., start_time=...)`.
- **Rhythm**: `rhythm('b b 0 0 b 0 b 0', 1)`.

## Syntactic Sugar & Operations

### Transformation & Manipulation
- **Transpose**: `A + n` (up), `A - n` (down), `A.up(n)`, `A.down(n)`.
  - Advanced: `++A` (raise 3 semitones), `--A` (lower 3 semitones).
- **Inversion**: `A / n` (nth inversion), `A ^ n` (invert $n$-th note to highest).
- **Modulation**: `A.modulation(i, j)` (from scale $i$ to $j$).
- **Reversal**: `~A` or `A.reverse()`.
- **Accidental Conversion**: `~a` (Converts C# to Db or vice versa).
- **Note Expansion**: `A + (n, i)` (raise $i$-th note by $n$ semitones).

### Composition & Sequence
- **Concatenation**: `A | B` (connect $A$ then $B$), `A | (B, n)` (with $n$ bars interval).
- **Repetition/Expansion**: `A * n` (repeat $n$ times), `A | (n, i)` (n times with $i$ bars interval).
- **Stacking**: `A & B` (stack $A$ and $B$ vertically), `A & n` (stack $n$ times).
- **Rest**: `A | n` (add $n$ bars of rest after $A$).

### Chord & Scale Properties
- **Indexing**: `A[i]` (get $i$-th note), `A[i:j]` (get notes $i$ to $j$).
- **Degree Extraction**: `A.get_degree(i)` (get $i$-th degree of scale).
- **Pattern Generation**: `A % 6451` (generate progression pattern 6451 from scale $A$).
- **Intervals**: `A.intervalof()` (get musical intervals of chord $A$).
- **Dotted Notes**: `A.dotted(n)` (adds $n$ dots to a note/chord).

### Input/Output
- **MIDI Read**: `read(path)`.
- **MIDI Write**: `write(A)`.
- **Playback**: `play(A, bpm=100)`.
- **Stop**: `stopall()`.

## Advanced Functions
- **Negative Harmony**: `A @ B` (negative harmony of chord $A$ at scale $B$).
- **Arpeggiation**: `arp(chord, octaves, start_pitch)`.
- **Rhythm to Chords**: `get_chords_from_rhythm(chord, rhythm_obj)`.
- **Pitch Conversion**: `degree_to_note(60)` $\rightarrow$ `C4`.
