# Musicpy Note Type Reference

Detailed documentation for manipulating the `note` data type in `musicpy`.

## Construction
- **By Name & Octave**: `note('D', 6)` or `N('D6')`
- **Direct String**: `N('E5')` or `to_note('E5')`
- **With Attributes**: `note(name='C', num=5, duration=0.5, volume=100)`
  - `duration`: length in bars (float)
  - `volume`: MIDI strength (0-127)
  - `channel`: MIDI channel

## Transformations
- **Transpose**:
  - `a.up(n)` / `a.down(n)`
  - `a + n` (up) / `a - n` (down)
  - `+++a` (up 3 semitones) / `---a` (down 3 semitones)
- **Accidentals**:
  - `~a` toggles between sharp and flat (e.g., `C#` $\leftrightarrow$ `Db`)
- **Pitch Manipulation**:
  - `a.reset_pitch('E')`: Changes pitch to E, keeps octave.
  - `a.reset_octave(3)`: Changes octave to 3, keeps pitch.
  - `a.reset_name('A5')`: Resets both pitch and octave.
- **Comparison**:
  - `a == b`: True if pitches are identical (e.g., `C#5 == Db5`).
  *Note: Comparison is pitch-based, independent of note name string.*

## Advanced Features
- **Dotted Notes**:
  - `a.dotted()`: Single dotted note.
  - `a.dotted(2)`: Double dotted note.
  - Use in strings: `chord('C5[.8;.]')` (dotted eighth).
- **Chord Generation**:
  - `N('A3')('sus')`: Generates a chord based on the note and a quality (e.g., A3 sus4).
  - `a.with_interval(database.major_seventh)`: Creates a chord using a specific interval relative to note `a`.
- **Properties**:
  - `a.degree`: Returns MIDI pitch number.
  - `a.name`: Returns note name string.
  - `a.num`: Returns octave number.
  - `a.duration`: Returns duration in bars.
