---
sr-due: 2025-12-29
sr-interval: 15
sr-ease: 290
---

aliases: []  
tags: [theory, cs, programming]  
sr-due: true
graph: false

#review 

---

## 🧠 Co to jest?
**Kontener to obiekt, który potrafi przechowywać kolekcję innych obiektów**  
i zwykle pozwala sprawdzić, czy element w nim _jest_ (`in`),  
oraz można po nim iterować (`for ... in ...`).

## Skąd wiadomo że coś jest kontenerem?

Posiada dundermethots takie jakie 

`__contains__`   # wspiera operator "in"
`__iter__`       # da się po nim iterować nie jest wymagane ale bardzo często występujee
## 🔧 Jak to działa?

|Typ|Czy mutowalny?|Co przechowuje?|Przykład|
|---|---|---|---|
|`list`|✔ tak|dowolne obiekty|`[1, "a", obj]`|
|`tuple`|✘ nie|dowolne obiekty|`(1, 2)`|
|`set`|✔ tak|unikalne obiekty|`{1, 2}`|
|`dict`|✔ tak|klucz → wartość|`{"name": "Kamil"}`|
|`str`|✘ nie|sekwencja znaków|`"hello"`|
## 🧪 Przykład

```python
__contains__   # wspiera operator "in"
__iter__       # da się po nim iterować


my_list = [1, 2, 3]

1 in my_list       # True  → działa __contains__
for x in my_list:  # działa __iter__
    print(x)


```

---

## 🧩 Mnemotechniki

### 🅰 Akronim

### **K O N T E N E R**

#### **K — Kolekcja**

Przechowuje wiele elementów naraz.
#### **O — Obiekty w środku**

Może trzymać _dowolne obiekty_ — liczby, stringi, klasy.
#### **N — Nawigacja**

Możesz po nim iterować (`for x in ...`).
#### **T — Test przynależności**

Obsługuje operator `in` → sprawdzasz, czy coś jest w środku.
#### **E — Elastyczność**

Może być mutowalny (`list`, `set`, `dict`) albo niemutowalny (`tuple`, `str`).
#### **N — Naturalna struktura**

Działa jak pudełko, torba, szuflada — intuicyjnie przechowuje dane.
#### **E — Elementy**

Zawsze chodzi o _przechowywanie elementów_ — to jego główna rola.
#### **R — Reprezentacja zbioru**

To sposób reprezentowania grupy wartości w programie.

---

### 🔄 Tłumaczenie jako analogia

**Analogia:** 
Kontener w Pythonie można porównać do pudełka z przedmiotami — takiego, które pozwala wyciągać elementy po kolei (dzięki `__iter__`) oraz sprawdzać, czy dany przedmiot w ogóle się w nim znajduje (`__contains__`).

Jakie to byłoby wspaniałe, gdyby w prawdziwym życiu działało to tak samo: szukasz baterii do pilota i zamiast wysypywać wszystko na podłogę, po prostu używasz magicznej metody `in` i od razu wiesz, czy bateria jest w środku 😄

Typy danych, które w Pythonie są kontenerami, to m.in.: `list`, `set`, `str`, `tuple` oraz `dict` — wszystkie one przechowują inne obiekty i umożliwiają sprawdzanie przynależności (`in`) oraz iterację po elementach.


---

### 🗃 Keyword Connections (powiązania)

- [[__contains__]]
- [[__iter__]]

---

### 🖼 Rysunek / schemat / diagram ASCII

![[Pasted image 20251210193958.png]]

---

## ✨ Metoda Feynmana (1–2 zdania)

Container w Pythonie to taka magiczna szuflada, która posiada w sobie obiekty. Posiada ona dwie metody, takie jak `iter` oraz `contains`. Dzięki temu jesteś w stanie iterować po elementach oraz sprawdzać, czy dany element jest w środku.

---

## ⚠ Typowe błędne wyobrażenie

Moim wcześniejszym błędnym wyobrażeniem na temat kontenerów było to, że muszą posiadać metodę `__iter__`. W rzeczywistości, aby obiekt był uznany za kontener, wystarczy implementacja metody `__contains__`. `__iter__` jest często spotykane w kontenerach, ale nie jest definicyjnym wymogiem.

---

## 📌 Kontrast (X vs Y)

| Cecha                         | Kontener | Sekwencja                       |
| ----------------------------- | -------- | ------------------------------- |
| Ma określoną kolejność        | ❌        | ✅                               |
| Posiada indeksy (`obj[0]`)    | ❌        | ✅                               |
| Implementuje `__contains__`   | ✅        | ✅                               |
| Może implementować `__iter__` | ✅        | ✅                               |
| `__iter__` jest wymagane      | ❌        | ❌ (ale praktycznie zawsze jest) |
| Przechowuje wiele elementów   | ✅        | ✅                               |
| Może być mutowalny            | ✅        | ✅ (np. list)                    |
| Może być niemutowalny         | ✅        | ✅ (np. tuple, str)              |
|Przykłady|list, set, dict, str, tuple|list, tuple, str, range|

---

## 🗂 Fiszki (SRS) #flashcards 

**Co definiuje obiekt jako kontener w Pythonie?**
?
Implementacja metody `__contains__`.
<!--SR:!2025-12-17,2,270-->

---

**Czy kontener musi posiadać `__iter__`?**
?
Nie. Kontener wymaga tylko `__contains__`.
<!--SR:!2025-12-30,15,310-->

---

**Czy każdy iterowalny obiekt jest kontenerem?**
?
Nie. Iterowalność nie oznacza posiadania `__contains__`.
<!--SR:!2026-01-01,17,310-->

---

**Czy generator jest kontenerem?**
?
Nie. Jest iterowalny, ale nie wspiera `__contains__`.
<!--SR:!2025-12-25,11,290-->

---

**Czy `str` jest kontenerem?**
?
Tak — posiada `__contains__` i `__iter__`.
<!--SR:!2025-12-27,12,290-->

---

**Jakie typy danych są kontenerami w Pythonie?**
?
list, tuple, str, set, dict.
<!--SR:!2025-12-26,12,290-->

---

**Co zrobi Python, gdy użyjesz `in`, ale obiekt nie ma `__contains__`?**
?
Spróbuje iterować obiekt (`__iter__`) i porównywać elementy.
<!--SR:!2025-12-16,2,250-->

---

**Czy kontener musi mieć kolejność?**
?
Nie. Kolejność jest cechą sekwencji, nie kontenera.
<!--SR:!2025-12-17,4,270-->

---

**Czym kontener różni się od sekwencji?**
?
Sekwencja ma kolejność i indeksy; kontener nie musi ich mieć.
<!--SR:!2025-12-16,2,230-->

---

**Czy własna klasa może być kontenerem?**
?
Tak — wystarczy zaimplementować `__contains__` (opcjonalnie także `__iter__`).
<!--SR:!2025-12-31,16,310-->

---

## 🔗 Powiązane notatki
