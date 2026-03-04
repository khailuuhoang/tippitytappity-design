# tippitytappity-design

tippitytappity is a program to practice typing


## Data model

classDiagram
direction TB

class Phrase {
  -text: string
  -difficulty: int
  +Phrase(text: string, difficulty: int)
  +get_text(): string
  +get_difficulty(): int
}

class PhraseBank {
  -phrases: vector~Phrase~
  +PhraseBank()
  +add_phrase(p: Phrase): void
  +get_random_phrase(): Phrase
  +count(): int
}

class TypingSession {
  -prompt: Phrase
  -typed: string
  -start_ms: long
  -end_ms: long
  +TypingSession(prompt: Phrase)
  +start(): void
  +finish(typed: string): void
  +elapsed_ms(): long
  +get_prompt(): Phrase
  +get_typed(): string
}

class TypingResult {
  -accuracy_pct: double
  -wpm: double
  -correct_chars: int
  -incorrect_chars: int
  +TypingResult(acc: double, wpm: double, correct: int, incorrect: int)
  +get_accuracy_pct(): double
  +get_wpm(): double
  +get_correct_chars(): int
  +get_incorrect_chars(): int
}

class AccuracyCalculator {
  +accuracy_pct(expected: string, typed: string): double
  +correct_chars(expected: string, typed: string): int
  +incorrect_chars(expected: string, typed: string): int
}

class WpmCalculator {
  +wpm(typed: string, elapsed_ms: long): double
}

PhraseBank --> Phrase : stores
TypingSession --> Phrase : uses
TypingSession --> TypingResult : produces
TypingSession --> AccuracyCalculator : uses
TypingSession --> WpmCalculator : uses
```
