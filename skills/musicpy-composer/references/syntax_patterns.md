# Musicpy Syntax Patterns

This document details the idiomatic "syntactic sugar" patterns in `musicpy` for expressive composition.

## 1. The Pipe `|` (Concatenation/Sequence)
Used to chain musical events over time.
- **Standard**: `chord_A | chord_B` (A followed by B)
- **With Interval**: `chord_A | (chord_B, 2)` (A, then a 2-bar gap, then B)
- **With Rests**: `chord_A | 4` (A, followed by 4 bars of silence)

## 2. The Asterisk `*` (Repetition/Expansion)
Used to repeat structures or scale quantities.
- **Sequence Repetition**: `chord_A * 4` (Repeats the chord 4 times)
- **Expansion**: `track_A * 2` (Repeats the track)

## 3. The Ampersand `&` (Stacking/Verticality)
Used to layer musical elements simultaneously.
- **Simultaneous Chords**: `chord_A & chord_B` (A and B playing at the same time)
- **Vertical Repetition**: `chord_A & 3` (Stacks the same chord 3 times vertically)

## 4. The At Symbol `@` (Structure/Transformation)
Used for complex transformations and inversions.
- **Inversion**: `chord_A @ 1` (First inversion)
- **Negative Harmony**: `chord_A @ scale_B` (Apply negative harmony of A relative to scale B)
- **Array-based transformation**: `chord_A @ [1, 2, 3]` (Reconstruct chord using specific indices)

## 5. The Tilde `~` (Reversal)
- **Reversal**: `~chord_A` (Reverses the order of notes or events)

## 6. The Percent `%` (Attributes & Patterns)
Used to set properties or generate progressions.
- **Attribute Setting**: `note_A % (duration, volume, channel)`
- **Progression Pattern**: `scale_A % 6451` (Generates a progression based on the 6-4-5-1 pattern)

## 7. The Caret `^` (Inversion/Complexity)
- **Note Inversion**: `chord_A ^ 2` (Inverts the 2nd note to the top of the chord)
