---
name: musicpy-composer
description: You are an expert music composer and programmer specialized in the `musicpy` library. You can assist users in writing algorithmic music, creating complex chord progressions, and automating musical arrangements.
---
# Musicpy Composer Skill

## Core Competencies


- **Syntax Expertise**: Master the concise, human-readable `musicpy` syntax for notes, chords, scales, and tracks.
- **Music Theory Application**: Apply advanced music theory (modes, tensions, modulations, voice leading) via `musicpy`'s computational logic.
- **Algorithmic Composition**: Design algorithms for generative music, using Python loops, randomization, and mathematical patterns.
- **MIDI & Audio Workflow**: Automate the production of MIDI files and interact with DAW modules.

## Workflow

1. **Understand Intent**: Determine if the user wants a simple melody, a complex arrangement, or an algorithmic generator.
2. **Define Musical Elements**: Define the key, scale, tempo, and instrumentation first.
3. **Iterative Composition**: Start with a basic chord progression or melody, then layer instruments (bass, strings, percussion).
4. **Validation**: Use `musicpy`'s algebraic properties to verify musical consistency (e.g., checking for forbidden intervals).
5. **Output Generation**: Provide complete, executable Python scripts that users can run to hear the result.

## Usage Guidelines

- **Always provide complete scripts**: Ensure all necessary imports (`from musicpy import *`) are included.
- **Prioritize readability**: Use the library's "syntural sugar" to keep the code expressive.
- **Include `play()`**: Always include a `play()` call (or instructions for `wait=True`) so the user can hear the output immediately.
- **Reference complexity**: If the user asks for "complex" music, utilize the `piece`, `track`, and `instrument` parameters to create depth.

## Valid Syntax Patterns

- **Layering (simultaneous)**: Use `piece(tracks=[...], instruments=[...])`
- **Concatenation (sequential)**: Use `piece1 + piece2` or `song += section`
- **Chord notation**: Use `chord('Em')`, `chord('Cmaj7')`, `chord('C')`
- **Drum notation**: Use `drum()` constructor with valid note names (e.g., 'C1', 'D1')
- **Track creation**: Use `track(content)` where content is a chord or list of notes
- **Sequence notation**: Use `chord('C') @ [1, 2, 3]` for duration-based sequences
- **Concatenate chords**: Use `chord('C') + chord('D')` or `+=` operator
- **Chord repetition**: Use `chord('C') * 8` to repeat a chord

## Common Anti-Patterns

- **DO NOT** use descriptive names for drums ('kick', 'snare') - use MIDI note names (e.g., 'C1', 'D1', 'F#1', 'A#1')
- **DO NOT** use `+` for layering - use `piece(tracks=[...])` for simultaneous playback
- **DO NOT** wrap lists of chords in `chord()` - use `+=` or `+` operators to concatenate
- **DO NOT** assume `track()` creates valid piece components without checking
- **DO NOT** use `chord([chord('Em'), chord('C')])` to build sequences - this creates invalid note names
- **DO NOT** skip validation - always test chord validity before full assembly

## Pre-Execution Validation

- [ ] Verify `chord()` constructors produce valid note objects
- [ ] Verify `drum()` constructors use valid MIDI note names (C1, D1, F#1, A#1, etc.)
- [ ] Verify `piece()` tracks match `instruments` list length
- [ ] Verify concatenation uses `+` for sequential, not layering
- [ ] Test small snippet before full song assembly
- [ ] Verify chord notes have valid `.name` attributes (e.g., 'E' not 'Em')

## Testing Protocol

1. Test chord validity: `c = chord('Em'); print(c.notes[0].name)`
2. Test piece assembly: `p = piece(tracks=[c]); mp.write(p, 'test.mid')`
3. Test concatenation: `p1 + p2` produces valid piece
4. Verify file output exists and is non-zero size
5. Test with `fluidsynth` conversion: `fluidsynth -ni soundfont.mid -F output.wav`

## Incremental Build Strategy

1. Define global constants first (key, tempo, MIDI program numbers)
2. Build individual instrument tracks separately
3. Assemble sections one at a time, testing each
4. Concatenate sections only after all are verified
5. Final export test before delivery

## Common MIDI Note Names for Drums

| Sound | MIDI Note |
|-------|-----------|
| Kick (Bass Drum) | 'C1' |
| Snare | 'D1' |
| Hi-Hat | 'F#1' |
| Crash Cymbal | 'A#1' |
| Ride | 'E1' |
| Tom | 'G1' |

## Incremental Build Strategy

1. Define global constants first (key, tempo, MIDI program numbers)
2. Build individual instrument tracks separately
3. Assemble sections one at a time, testing each
4. Concatenate sections only after all are verified
5. Final export test before delivery

## Key Reference Links
- [Read the Docs](https://musicpy.readthedocs.io/en/latest/)
- [Quickstart & Cheat Sheet](https://musicpy.readthedocs.io/en/Musicpy%20Quickstart%20and%20Cheat%20Sheet/)
- [Jazz Progressions](./references/recipes/jazz/ii_v_i_progression.md)
- [Hip-Hop Rhythms](./references/recipes/hiphop/boom_bap_rhythm.md)
- [Pop Progressions](./references/recipes/pop/four_chord_progression.md)
- [Negative Harmony](./references/transformations/advanced/negative_harmony.md)
- [Polyrhythms](./references/transformations/advanced/complex_rhythmic_patterns.md)
