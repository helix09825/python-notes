

aliases: []  
tags: [theory, cs, programming]  
sr-due: true
graph: false

---

## 🧠 Co to jest?
#### Zmienna globalna
Zmienna globalna to zmienna istniejąca w globalnym zakresie programu.  
Jest dostępna w całym module, a funkcje mogą odwoływać się do niej lub ją modyfikować przy użyciu słowa kluczowego `global`.  
Nie zaleca się nadpisywania zmiennych globalnych wewnątrz funkcji, ani nazywania ich tak samo jak zmiennych lokalnych, ponieważ może to prowadzić do niejednoznaczności i błędów logicznych.

#### Zmienna lokalna
**Zmienna lokalna** to zmienna utworzona **wewnątrz funkcji**, która istnieje tylko w jej **lokalnym zakresie** i przestaje istnieć po zakończeniu działania funkcji.

#### Zmienna nielokalne
**Zmienna nielokalna** to zmienna, która pochodzi z **wyższego (zawierającego) zakresu funkcji**, ale nie jest globalna.  
Można się do niej odnieść i modyfikować ją wewnątrz funkcji zagnieżdżonej, używając słowa kluczowego **`nonlocal`**

## 🔧 Jak to działa?
#### 🔵 **Zmienna globalna (`counter`)**

- Żyje w całym module.
    
- `global counter` pozwala funkcji `inner()` ją zmieniać.
    

#### 🟢 **Zmienna nielokalna (`x`)**

- Jest w funkcji `outer()`.
    
- `inner()` modyfikuje ją dzięki `nonlocal x`.
    

#### 🟡 **Zmienna lokalna (`y`)**

- Istnieje tylko w `inner()` i znika po jej zakończeniu.

## 🧪 Przykład

```python
counter = 0  # 🔵 zmienna globalna

def outer():
    x = 10  # 🟢 zmienna nielokalna (dla inner)

    def inner():
        nonlocal x      # pozwala modyfikować x z outer()
        x += 5

        global counter  # pozwala modyfikować zmienną globalną
        counter += 1

        y = 3  # 🟡 zmienna lokalna (dla inner)
        return y

    local_value = inner()
    return x, counter, local_value

print(outer())
```

---

## 🧩 Mnemotechniki

### 🅰 Akronim

**Akronim:** G-N-L

**Rozwinięcie:**

- G — Global
	- ➡ zmienna widoczna w całym module, modyfikowana przez global.
- N — Nonlocal
	- ➡ zmienna należąca do funkcji zewnętrznej, modyfikowana przez nonlocal.
- L — Local
	- ➡ zmienna utworzona wewnątrz funkcji, istnieje tylko tam.
---

### 🔄 Tłumaczenie jako analogia

**Analogia:**

**Global = dom, Nonlocal = pokój, Local = biurko — im bliżej środka, tym bardziej prywatne.**

---

### 🗃 Keyword Connections (powiązania)

- [[scope]]
- [[global]]
- [[closure]]
- [[nonlocal]]
- [[Lexical scope]]
- [[enclosing]]

---

### 🖼 Rysunek / schemat / diagram ASCII

![[Pasted image 20251201113941.png]]
---

## ✨ Metoda Feynmana (1–2 zdania)

Scope zmiennych działa jak dom: poziom globalny to cały dom, poziom nonlocal to pokój, a poziom lokalny to biurko.  

Możemy sięgać z biurka do rzeczy w pokoju i w domu, ale nie da się z poziomu domu dostać do rzeczy schowanych na biurku.

---

## ⚠ Typowe błędne wyobrażenie
**Wielu początkujących uważa, że aby odczytać zmienną z wyższego scope’u (funkcji zewnętrznej lub globalnego), trzeba używać słów kluczowych `global` lub `nonlocal`. To nieprawda.**

Python **zawsze automatycznie szuka zmiennej w wyższych scope’ach** — najpierw w lokalnym, potem w zewnętrznym (enclosing), następnie w globalnym, a na końcu w builtins.  
Dopiero **modyfikacja** zmiennej z wyższego scope’u wymaga jawnego użycia słów kluczowych `global` lub `nonlocal`.

---

## 📌 Kontrast (X vs Y)

| Cecha                                                                      | global    | nonlocal                                                                    | local                       |
| -------------------------------------------------------------------------- | --------- | --------------------------------------------------------------------------- | --------------------------- |
| Gdzie powstaje zmienna?                                                    | w module  | w zewnętrznej funkcji                                                       | w obecnej funkcji           |
| Jak długo istnieje?                                                        | cały czas | jest przyczepiona do funkcji wewnętrznej i to od niej zależy jej cykl życia | tylko podczas życia funkcji |
| Czy funkcja może ją odczytać bez słówek kluczowych?                        | ✅         | ✅                                                                           | ✅                           |
| Czy funkcja może ją modyfikować bez słówek kluczowych?                     | ❌         | ❌                                                                           | ✅                           |
| Jakiego słowa kluczowego wymaga modyfikacja?                               | global    | nonlocal                                                                    | ❌                           |
| Zmienna jest widoczna poza funkcją.                                        | ✅         | ✅                                                                           | ❌                           |
| Czy może być nadpisana przypadkowo?                                        | ✅         | ❌                                                                           | ❌                           |
| Czy jest tworzona na nowo przy każdym wywołaniu funkcji?                   | ❌         | ❌                                                                           | ✅                           |
| Czy można ją zachować w clousure?                                          | ❌         | ✅                                                                           | ✅                           |
| Czy dostęp do niej zależy od miejsca wywołania funkcji, czy jej definicji? | definicji | definicji                                                                   | definicji                   |

---

## 🗂 Fiszki (SRS) #flashcards 

Co to jest zmienna globalna?
?
Zmienna utworzona w module, widoczna w całym programie; do modyfikacji wymaga słowa kluczowego global.

Co to jest zmienna lokalna?
?
Zmienna utworzona wewnątrz funkcji, dostępna tylko w tej funkcji i tworzona na nowo przy każdym wywołaniu.

Co to jest zmienna nielokalna (nonlocal)?
?
Zmienna należąca do funkcji zewnętrznej, którą funkcja wewnętrzna może modyfikować dzięki słowu kluczowemu nonlocal.

Czy można odczytać zmienną globalną bez użycia global?
?
Tak, do odczytu zmienna globalna jest zawsze dostępna.

Czy można modyfikować zmienną globalną bez global?
?
Nie, Python wtedy potraktuje ją jako zmienną lokalną i wyrzuci UnboundLocalError.

Czy można odczytać zmienną nonlocal bez użycia nonlocal?
?
Tak, odczyt jest dozwolony — nonlocal jest potrzebne tylko do modyfikacji.

Czy można modyfikować zmienną nonlocal bez nonlocal?
?
Nie, Python uzna wtedy zmienną za lokalną i wygeneruje błąd UnboundLocalError.

Czy zmienna lokalna jest widoczna poza funkcją, w której powstała?
?
Nie, zmienna lokalna jest ograniczona wyłącznie do danej funkcji.

Czy zmienna lokalna może zostać zachowana w closure?
?
Tak, jeśli jest lokalną zmienną funkcji zewnętrznej, zostanie zapamiętana przez funkcję wewnętrzną.

Czy zmienna globalna może zostać zachowana w closure?
?
Nie, closure przechowuje tylko zmienne z lokalnych scope’ów funkcji zewnętrznych.

Czy funkcja widzi zmienne lokalne innej funkcji?
?
Nie, scope nigdy nie działa „w dół” ani „w bok” — tylko w górę.

Od czego zależy dostępność zmiennych (lexical scope)?
?
Dostępność zależy od miejsca definicji funkcji, a nie od miejsca jej wywołania.

Jaka jest kolejność szukania zmiennych w Pythonie (LEGB)?
?
Local → Enclosing (nonlocal) → Global → Builtins.

Co się stanie przy próbie użycia zmiennej z wyższego scope bez deklaracji global lub nonlocal, jeśli próbujemy ją modyfikować?
?
Python potraktuje ją jako zmienną lokalną i zgłosi UnboundLocalError.

---

## 🔗 Powiązane notatki