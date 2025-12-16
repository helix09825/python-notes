
aliases: []  
tags: [theory, cs, programming]  
sr-due: true
graph: false

#review 

---

## 🧠 Co to jest?

**OOP (Object-Oriented Programming)**, czyli **programowanie obiektowe**, to paradygmat programowania, w którym **program buduje się z obiektów** – a nie tylko z funkcji i danych.

Obiekt = **dane + zachowanie** zamknięte w jednej całości.
## 🔧 Jak to działa?

Zamiast pisać:

- „mam funkcje i osobne dane”
    

piszemy:

- „mam **obiekty**, które _coś mają_ i _coś robią_”
    

Przykład myślowy:

> **Samochód**  
> – dane: prędkość, paliwo  
> – zachowanie: jedź(), hamuj(), tankuj()
## 🧪 Przykład

```python
class Car:
    pass
```

## 🎯 Po co OOP?

OOP pomaga:

- porządkować duże projekty
    
- modelować rzeczywistość (biznes, domenę)
    
- pisać kod **łatwiejszy do utrzymania**
    
- zmniejszać powtórzenia (DRY)

---

## 🧩 Mnemotechniki

### 🅰 Akronim

**Akronim:** OOP

**Rozwinięcie:**

- O — Object
    
- O — Oriented
    
- P — Programing
    

---

### 🔄 Tłumaczenie jako analogia

**Analogia:**
OOP to podejście w programowaniu, które polega na budowaniu kodu z obiektów — czyli połączeń danych i zachowań zamkniętych w jednej całości.

To tak, jakbyśmy budowali zamek z LEGO:  
zamiast myśleć o pojedynczych klockach, pracujemy na gotowych budowlach, takich jak Komnata, Rycerz, Lochy czy Brama — a każda z nich ma swój stan i swoje zachowania.

---

### 🗃 Keyword Connections (powiązania)

- [[Enkapsulacja (encapsulation)]]
    
- [[Dziedziczenie (inheritance)]]
    
- [[Polimorfizm (polymorphism)]]
    

---

### 🖼 Rysunek / schemat / diagram ASCII

```
[Input] → [Processing] → [Output]
```

---

## ✨ Metoda Feynmana (1–2 zdania)

Programowanie OOP polega na tym, że budujemy miasto z gotowych budowli (obiektów), a nie z pojedynczych klocków — bo detale są zamknięte wewnątrz tych budowli.
![[Pasted image 20251215063617.png]]

![[Pasted image 20251215071825.png]]
Ten obraz przedstawia **cztery filary programowania obiektowego (OOP)** zapamiętane poprzez **symbolikę ciała i zwierząt**.

- **Dziedziczenie** (lwia łapa z koroną) oznacza, że obiekt **przejmuje strukturę i możliwości klasy bazowej**, ale nie jej konkretny stan (instancję).
    
- **Polimorfizm** (dwugłowy smok) pokazuje, że **ta sama metoda** może wywoływać **różne zachowania** – jedno polecenie, różne efekty.
    
- **Enkapsulacja** (nakolanniki z tarczy żółwia) symbolizuje **ukrycie wnętrza obiektu** – korzystasz z niego bez potrzeby zaglądania do środka.
    
- **Abstrakcja** (skrzydła orła) oznacza skupienie się na **tym, co obiekt robi**, a nie **jak jest to zrealizowane**.
    

Całość tworzy system pamięciowy, w którym **każdy filar OOP ma swoje miejsce na ciele i jednoznaczny symbol**, dzięki czemu łatwo go przywołać z pamięci bez definicji słownych.

---

## ⚠ Typowe błędne wyobrażenie

W OOP **polimorfizm NIE wymaga dziedziczenia**.
Pomieszałem dcit z objektem z oop w rzeczywistości Objekt w OOP to instancja klasy -> więc nie może istnieć bez Klasy
Mślałem że Objekt może mieć tylko dane jako strukturwa w rzeczywistości Objekt powinien mieć też zachowania inaczej nie spełnia OOP i jest to DTO 


---

## 📌 Kontrast (X vs Y)

| Cecha                                      | OOP | Koncepcja przeciwna (FP) |
| ------------------------------------------ | --- | ------------------------ |
| Dane i zachowanie są połączone             | ✅   | ❌                        |
| Dane są modyfikowane „w miejscu”           | ✅   | ❌                        |
| Zachowanie jest wywoływane na danych       | ✅   | ❌ (funkcja → dane)       |
| Funkcje są obywatelami pierwszej klasy     | ❌   | ✅                        |
| Istnieje pojęcie tożsamości obiektu        | ✅   | ❌                        |
| Stan obiektu zmienia się w czasie          | ✅   | ❌                        |
| Przepływ programu opiera się na obiektach  | ✅   | ❌                        |
| Operacje są niezależne od struktury danych | ❌   | ✅                        |
| Preferowana jest niemutowalność            | ❌   | ✅                        |
| Logika jest skupiona w jednym „bycie”      | ✅   | ❌                        |
| Łatwo modelować domenę (biznes, świat gry) | ✅   | ⚠️ / zależy              |
| Łatwo śledzić przepływ danych              | ❌   | ✅                        |

---

## 🗂 Fiszki (SRS) #flashcards 

Czym w OOP jest **obiekt**?
?
Obiekt to instancja klasy, która posiada **tożsamość, stan i zachowanie**.
<!--SR:!2025-12-18,3,250-->

---

Czym różni się **klasa** od obiektu?
?
Klasa jest definicją (szablonem), a obiekt konkretną instancją tej definicji.
<!--SR:!2025-12-19,4,270-->

---

Na czym polega **enkapsulacja** w OOP?
?
Na ukrywaniu szczegółów implementacji i udostępnianiu tylko kontrolowanego interfejsu.
<!--SR:!2025-12-16,1,230-->

---

Czy **polimorfizm** wymaga dziedziczenia?
?
Nie, polimorfizm polega na wspólnym interfejsie zachowania, a nie na relacji dziedziczenia.
<!--SR:!2025-12-16,1,230-->

---

Czym jest **polimorfizm** w OOP?
?
To możliwość wywoływania tego samego zachowania na różnych obiektach, które reagują na nie na swój sposób.
<!--SR:!2025-12-18,3,250-->

---

Czym jest **tożsamość obiektu**?
?
To fakt, że obiekt jest rozpoznawalny jako ten sam byt niezależnie od zmian swojego stanu.
<!--SR:!2025-12-16,1,230-->

---

Dlaczego **śledzenie przepływu danych** bywa trudniejsze w OOP?
?
Ponieważ obiekty zmieniają swój stan w czasie, a dane nie płyną liniowo przez funkcje.
<!--SR:!2025-12-19,4,270-->

---

Czym jest **mutowalność** w OOP?
?
To możliwość zmiany stanu obiektu „w miejscu” bez tworzenia nowego obiektu.
<!--SR:!2025-12-16,1,230-->

---

Czy OOP wymaga **mutowalności**?
?
Nie, OOP może być niemutowalne, ale klasyczne podejście często na niej polega.
<!--SR:!2025-12-16,1,230-->

---

Czym różni się **obiekt OOP** od zwykłej struktury danych?
?
Obiekt OOP łączy dane z zachowaniem, a struktura danych przechowuje tylko dane.
<!--SR:!2025-12-19,4,270-->

---

Czy obiekt bez metod jest pełnoprawnym obiektem OOP?
?
Nie do końca — jest raczej pojemnikiem na dane (anemic model) niż obiektem z zachowaniem.
<!--SR:!2025-12-16,1,230-->

---

Na czym polega główna różnica mentalna między **OOP a FP**?
?
OOP skupia się na obiektach zmieniających stan, a FP na przepływie danych przez funkcje.
<!--SR:!2025-12-16,1,230-->

---

## 🔗 Powiązane notatki
https://www.programiz.com/python-programming/object-oriented-programming
https://beapython.dev/2020/01/21/functional-vs-object-oriented-programming-in-python/