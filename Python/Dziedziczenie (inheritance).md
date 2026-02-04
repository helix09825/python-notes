---
sr-due: 2026-01-07
sr-interval: 2
sr-ease: 249
---

aliases: []  
tags: [theory, cs, programming]  
sr-due: true
graph: false

#review 

---

## 🧠 Co to jest?
**Dziedziczenie w Pythonie** to mechanizm OOP, w którym klasa potomna **przejmuje i może rozszerzać lub nadpisywać** atrybuty oraz metody klasy nadrzędnej, a dostęp do nich odbywa się **zgodnie z kolejnością MRO (Method Resolution Order)**.

## 🔧 Jak to działa?
 1️⃣ Tworzysz klasę potomną
	➡️ `B` **nie kopiuje** kodu z `A`  
	➡️ `B` tylko **wie, że A jest jej rodzicem**
2️⃣ Wywołujesz metodę na obiekcie
3️⃣ Python sprawdza MRO (Method Resolution Order)

Gdy wywołasz b.foo():

🔍 Szukaj foo w klasie B
🔍 Nie ma → idź do A
🔍 Jest → wywołaj
🛑 Stop (nie idzie dalej)
➡️ Pierwsze znalezione = użyte

## 🧪 Przykład

```python
class A:
    def foo(self):
        print("A")

class B(A):
    pass
    
b = B()
b.foo() # "A"

```

---

## 🧩 Mnemotechniki

### 🅰 Akronim

**Akronim:**

**Rozwinięcie:** PRM

P – Przejmuję
R – Rozszerzam / Replace (nadpisuję)
M – MRO

---

### 🔄 Tłumaczenie jako analogia

**Analogia:** 

Jest rodzina która składa się z kilku pokoleń, dziadkowie, rodzice, dzieci 

jeśli dziecko chce pożyczyć sprzęt musi zapytać o zgodę starszego pokolenia aż do uzyskania zgody według kolejności MRO  

---

### 🗃 Keyword Connections (powiązania)

- [[MRO]]

---

### 🖼 Rysunek / schemat / diagram ASCII

![[Pasted image 20251217075255.png]]
---

## ✨ Metoda Feynmana (1–2 zdania)

**ziedziczenie w Pythonie** polega na tym, że klasa najpierw używa **własnych** metod i atrybutów, a jeśli ich nie ma, **korzysta z metod klas nadrzędnych zgodnie z kolejnością MRO**.

To jak z Netflixem: jeśli masz **własne konto**, używasz swojego; jeśli nie, **korzystasz z konta rodziców**, a jeśli oni też go nie mają — szukasz dalej wyżej.

---

## ⚠ Typowe błędne wyobrażenie


🧠 PODSUMOWANIE – TWOJE 4 GŁÓWNE BŁĘDNE ZAŁOŻENIA

❌ Obiekt „posiada referencje” do metod ✅ Metody są **dynamicznie wyszukiwane w klasach** (lookup po MRO)
❌ Kolejność klas = kolejność MRO ✅ Kolejność wywołań ustala **MRO (C3 linearization)**
❌ super() = rodzic  ✅`super()` wywołuje **następną klasę w MRO**
❌ Dziedziczenie = dane + zachowanie ✅ Dziedziczenie służy głównie do **współdzielenia zachowania**

✅ JEDNO ZDANIE – MODEL POPRAWNY
Dziedziczenie w Pythonie polega na dynamicznym wyszukiwaniu metod w hierarchii klas zgodnie z MRO, które jest ustalane przy tworzeniu klasy, a super() przechodzi do kolejnej klasy w tej kolejności.

---

## 📌 Kontrast (X vs Y)

| Cecha | Dziedziczenie (inheritance) | Koncepcja przeciwna |
| ----- | --------- | ------------------- |
|       |           |                     |
|       |           |                     |

---

## 🗂 Fiszki (SRS) #flashcards 

Czym jest dziedziczenie w Pythonie?
?
Dziedziczenie to mechanizm, w którym klasa używa własnych metod, a jeśli ich nie ma, Python wyszukuje je w klasach nadrzędnych zgodnie z MRO.
<!--SR:!2026-01-29,2,230-->

Po czym rozpoznajemy dziedziczenie w Pythonie?
?
Po tym, że klasa jest zdefiniowana na podstawie innej klasy i posiada ustaloną kolejność MRO.
<!--SR:!2026-01-29,2,230-->

Kiedy używamy dziedziczenia w Pythonie?  
?  
Gdy klasy reprezentują relację „jest typem” i chcemy współdzielić zachowanie między nimi.

Gdzie Python przechowuje metody przy dziedziczeniu?  
?  
Metody są przechowywane w klasach i wyszukiwane dynamicznie w hierarchii klas zgodnie z MRO.

Jak Python decyduje, którą metodę wywołać przy dziedziczeniu?  
?  
Python wybiera pierwszą metodę znalezioną w kolejności MRO.

Na czym polega nadpisywanie metody w dziedziczeniu?  
?  
Na zdefiniowaniu metody w klasie potomnej, która ma pierwszeństwo przed metodami klas nadrzędnych.

Czym jest MRO w Pythonie?  
?  
MRO (Method Resolution Order) to kolejność, w jakiej Python przeszukuje klasy w poszukiwaniu metod i atrybutów (algorytm C3).

Kiedy Python ustala MRO?
?
MRO jest ustalane w momencie tworzenia klasy, a nie instancji.
<!--SR:!2026-01-28,1,230-->

Co robi super() w kontekście dziedziczenia?  
?  
super() wywołuje metodę z kolejnej klasy w MRO, a nie bezpośrednio z rodzica.

Jaki jest główny cel dziedziczenia w Pythonie?  
?  
Współdzielenie zachowania między klasami poprzez hierarchię.

---

## 🔗 Powiązane notatki