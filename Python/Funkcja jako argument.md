aliases: []  
tags: [theory, cs, programming]  
sr-due: true  
graph: false

---

## 🧠 Co to jest?

**Funkcja opakowująca** to taka, która umożliwia opakowywanie innej funkcji w celu rozszerzenia zachowania opakowywanej funkcji bez jej trwałej modyfikacji. Funkcje w Pythonie są „obywatelami pierwszej klasy”. Oznacza to, że mogą być np. podawane jako argument, zwracane z funkcji, modyfikowane i przypisywane do zmiennej.

## 🔧 Jak to działa?

Funkcja opakowująca przyjmuje inną funkcję jako argument i zwraca nową funkcję, która wykonuje dodatkowe działania **przed**, **po**, albo **zamiast** oryginału — bez zmiany jej kodu. Najczęściej korzysta z domknięć (closures), by „pamiętać” przekazaną funkcję.

## 🧪 Przykład

```python
def logger(func):
    def wrapper(*args, **kwargs):
        print(f"Wywołano funkcję: {func.__name__}")
        result = func(*args, **kwargs)
        print("Zakończono działanie.")
        return result
    return wrapper

@logger
def say_hello(name):
    return f"Cześć {name}!"

say_hello("Kamil")
```

---

## 🧩 Mnemotechniki

### 🅰 Akronim

**Akronim:** W.R.A.P.

**Rozwinięcie:**

- **W** — Wywołuje dodatkowy kod
    
- **R** — Rozszerza funkcję
    
- **A** — Argumentem jest funkcja
    
- **P** — Przekazuje dalej wynik
    

---

### 🔄 Tłumaczenie jako analogia

**Analogia:** To jak owinięcie prezentu papierem — środek (oryginalna funkcja) pozostaje ten sam, ale dodajesz warstwę, która wpływa na to, jak zostaje „dostarczony”.

---

### 🗃 Keyword Connections (powiązania)

- [[lambda]]
- [[wywołanie zwrotne]]   
- [[Callable]]
 - [[First-Class Object]]

---

### 🖼 Rysunek / schemat / diagram ASCII

```
[funkcja wejściowa]
        ↓
 [funkcja opakowująca]
        ↓
[nowe zachowanie + oryginalna funkcja]
```
![[Pasted image 20251130205245.png]]
---

## ✨ Metoda Feynmana (1–2 zdania)

Funkcja opakowująca dodaje nowe zachowanie do funkcji, której kodu nie dotykasz. To jak filtr na zdjęcie — obraz jest ten sam, ale przechodzi przez dodatkową warstwę.

---

## ⚠ Typowe błędne wyobrażenie

Wiele osób myśli, że funkcja opakowująca **modyfikuje** oryginał — w rzeczywistości tworzy jedynie nową wersję, a oryginał pozostaje nietknięty.

---

## 📌 Kontrast (X vs Y)

|Cecha|Funkcja jako argument|Koncepcja przeciwna|
|---|---|---|
|Zmiana oryginału|❌ Nie|✔ Tak, modyfikacja kodu|
|Elastyczność|✔ Wysoka|❌ Niska|
|Styl|Dekorowanie|Nadpisywanie|
|Tworzenie wersji|Nowa funkcja|Zmiana istniejącej|

---

## 🗂 Fiszki (SRS) #flashcards

Czym jest funkcja opakowująca?
?
Funkcja, która przyjmuje inną funkcję i zwraca jej rozszerzoną wersję, nie zmieniając oryginalnego kodu.
<!--SR:!2025-12-03,1,230-->

---

## 🔗 Powiązane notatki

- [[dekorator]]
    
- [[closure]]