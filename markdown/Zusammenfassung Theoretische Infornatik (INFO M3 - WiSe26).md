# Zusammenfassung: Theoretische Infornatik (INFO M3 - WiSe26)

## Formale Sprachen

### Alphabet

Eine endliche Menge Σ heißt **Alphabet**. Die Elemente eines Alphabets werden **Buchstaben** (Zeichen oder Symbole) genannt.

### Wort

Sei Σ ein Alphabet. Ein **Wort** über Σ ist eine endliche (auch leere) Folge von **Buchstaben** aus Σ. Das leere Wort λ ist die leere Buchstabenfolge (manchmal auch ε).

Die **Länge** $|w|$ eines Wortes $w$ ist die Länge des Wortes als Folge, d.h. die Anzahl der Vorkommen von Buchstaben in $w$.

### Kleensche Hülle

Σ\* ist die Menge aller Wörter über Σ, Σ+ = Σ\* - {λ}.

### Sprache

Eine **Sprache** L über ein Alphabet Σ ist eine Teilmenge von Σ\*. Das Komplement C(L) der Sprache L bezüglich Σ ist die Sprache Σ\* - L. ($L_∅ = ∅$ - leere Sprache, $L_\lambda = \{\lambda\}$ - nur leeres Wort)