aliases: []  
tags: [theory, cs, programming]  
sr-due: true
graph: false

---

## 🧠 Co to jest?

**Dunder method** to _specjalna metoda w Pythonie_, której nazwa zaczyna się i kończy podwójnym podkreśleniem (`__nazwa__`).  
Python wywołuje je **automatycznie**, aby obsługiwać wbudowane operacje takie jak inicjalizacja, dodawanie, porównywanie, iteracja czy konwersja na string.
## 🔧 Jak to działa?
Dunder method to **specjalny hak**, który Python wywołuje **automatycznie**, gdy wykonujesz jakąś wbudowaną operację na obiekcie.

To _nie Ty_ je wywołujesz — **Python sam je odpala**, gdy rozpoznaje, że potrzebne jest określone zachowanie.

## 🧪 Przykład

Przykłady:

### `len(x)`

➡️ Python wywołuje

`x.__len__()`

### `x + y`

➡️ Python wywołuje

`x.__add__(y)`

### `x[10]`

➡️ Python wywołuje

`x.__getitem__(10)`

### `str(x)`

➡️ Python wywołuje

`x.__str__()`

Czyli wszystko, co wygląda „magicznie”, to po prostu **wywołanie odpowiedniej dunder method**.


---

## 🧩 Mnemotechniki

### 🅰 Akronim

#### 🔠 **Akronim: D.U.N.D.E.R.**

##### **D — Double**

Podwójne podkreślenia na początku i końcu.

##### **U — Under-the-hood**

Działają „pod maską” — Python wywołuje je automatycznie.

##### **N — Native behavior**

Sterują natywnym zachowaniem obiektu (`+`, `len()`, `[]`, porównania).

##### **D — Delegate actions**

Python deleguje do nich operacje językowe.

##### **E — Enhance objects**

Pozwalają obiektom zachowywać się jak wbudowane typy (np. listy, liczby).

##### **R — Reakcja automatyczna**

Uruchamiają się w reakcji na konkretne operacje (np. `__add__` po użyciu `+`).

---

### 🔄 Tłumaczenie jako analogia

**Analogia:**
**Dunder methods to reakcje przypisane do „przycisków” Pythona.  
Python wywołuje je automatycznie, ale możesz je nadpisać — tak jak przypisujesz własne funkcje do bocznego przycisku w telefonie.**


---

### 🗃 Keyword Connections (powiązania)

- [[__init__]]
- [[__str__]]
- [[__repr__]]
- [[__len__]]
- [[__add__]]
- [[__eq__]]
- [[__lt__]]
- [[__getitem__]]
- [[__setitem__]]
- [[__iter__]]
- [[__next__]]
- [[__enter__]]
- [[__exit__]]
- [[__call__]]

---

### 🖼 Rysunek / schemat / diagram ASCII

![[Pasted image 20251207182317.png]]
---

## 🔗 Powiązane notatki %%