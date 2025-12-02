
aliases: []  
tags: [theory, cs, programming]  
sr-due: true
graph: false

---

## 🧠 Co to jest?
Składanie to wygodny sposób na tworzenie zwięzłych list `list`

Zawsze tworzy nową listę 

## 🔧 Jak to działa?
- **Iteruje** po każdym elemencie źródła
    
- **Opcjonalnie filtruje** elementy (część `if`)
    
- **Transformuje** każdy element (wyrażenie na początku)
    
- **Zwraca nową listę**

## 🧪 Przykład

```python
[expression for item in iterable if condition]

numbers = [1, 2, 3, 4]
squares = [n*n for n in numbers]


result_1 = [expression for element in iterable if condition]
result_2 = [expression if condition else default_expression for element in iterable]

```

---

## 🧩 Mnemotechniki

### 🅰 Akronim

**Akronim:**

**Rozwinięcie:**

- A —
    
- B —
    
- C —
    

---

### 🔄 Tłumaczenie jako analogia

**Analogia:**
Wyobraź sobie taśmę z zabawkami.  
Oglądasz każdą zabawkę (**for**),  
wyrzucasz te popsute (**if**),  
a dobre malujesz na nowy kolor (**expression**).  
Na końcu masz nowe pudełko pełne tylko tych fajnych, odnowionych zabawek —  
**to właśnie list comprehension**.

---

### 🗃 Keyword Connections (powiązania)

- [[list]]
    

---

### 🖼 Rysunek / schemat / diagram ASCII

```
 ┌───────────┐       ┌─────────────┐       ┌─────────────────┐       
 |  iterable | --->  |   for item  | --->  |   if condition   | ->  | expression 
 └───────────┘       └─────────────┘       └─────────────────┘      | 
																	↓
															 ┌───────────────┐
															 |  new list []  |
															 └───────────────┘

```

---

## ✨ Metoda Feynmana (1–2 zdania)
**List comprehension** to taka **pythonowa sztuczka**, która pozwala zamienić **kilka linijek pętli `for`** w **jedną czytelną linijkę**.  
Działa to tak, że Python **przechodzi po elementach**, **wybiera tylko te, które spełniają warunek**, a potem **zamienia je na nowe wartości** i odkłada do nowej listy.  
Efekt? To samo co długa pętla – tylko **prościej, szybciej i czytelniej**.

---

## ⚠ Typowe błędne wyobrażenie

Wiele osób myśli, że **list comprehension modyfikuje istniejącą listę**.  
To nieprawda — **za każdym razem tworzy całkowicie nową listę**, niezależnie od tego, co robisz w wyrażeniu.  
Oryginalna lista **zostaje nietknięta**, a wynik list comprehension to **nowy obiekt w pamięci**.

---

## 📌 Kontrast (X vs Y)

| Cecha        | List Comperhension               | Zwykła pętla                 |
| ------------ | -------------------------------- | ---------------------------- |
| Długość      | Krótka                           | Dłuższa                      |
| Czytelność   | Bardzo dobra przy prostej logice | Dobra dla złożonych operacji |
| Wydajność    | Minimalnie szybsza               | Minimalnie wolniejsza        |
| Zastosowanie | Transformacje, filtrowanie       | Gdy logika jest złożona      |

---

## 🗂 Fiszki (SRS) #flashcards 

**P:** Co to jest list comprehension?
?
**O:** Zwięzły sposób tworzenia nowej listy poprzez iterację, opcjonalne filtrowanie i transformację elementów.
<!--SR:!2025-12-04,4,270-->

---

**P:** Jaka jest składnia list comprehension?
?
**O:** `[expression for item in iterable if condition]`
<!--SR:!2025-12-03,3,250-->

---

**P:** Co robi część `if` w list comprehension?
?
**O:** Filtruje elementy tak, aby do nowej listy trafiły tylko te spełniające warunek.
<!--SR:!2025-12-04,4,272-->

---

**P:** Czym list comprehension różni się od pętli?
?
**O:** Robi to samo, ale krócej, czytelniej i często szybciej.
<!--SR:!2025-12-04,4,272-->

---

## 🔗 Powiązane notatki