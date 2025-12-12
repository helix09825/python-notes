---
sr-due: 2025-12-22
sr-interval: 11
sr-ease: 274
---

aliases: []  
tags: [theory, cs, programming]  
sr-due: true
graph: false

---
#review
## 🧠 Co to jest?

**Klasa** to _szablon_ (definicja) obiektu.  
Opisuje **jakie dane** (atrybuty) oraz **jakie zachowania** (metody) będą miały tworzone z niej instancje.

- Klasa → przepis
- Instancja → gotowy obiekt stworzony z przepisu

Klasa w Pythonie to pełnoprawny obiekt typu „type”, definiujący zachowanie instancji, dziedziczenie, protokoły, operator overloading oraz integrację z systemem typów.

## 🔧 Jak to działa?
### **1) Atrybuty klasowe i instancji**

- **Atrybut klasowy** — należy do _klasy_; współdzielony przez wszystkie instancje
    
- **Atrybut instancji** — unikalny dla _konkretnego obiektu_; tworzony zwykle w `__init__`

### **2) Metody specjalne (dunder methods)**

Klasy posiadają zestaw wbudowanych metod, m.in.:

- `__init__(self, ...)`  
    Wywoływana _po utworzeniu instancji_. Służy do jej konfiguracji, np. przypisania atrybutów.
    
- `__new__(cls, ...)`  
    Wywoływana _przed_ `__init__`.  
    Odpowiada za **tworzenie nowej instancji w pamięci**.  
    Bardzo rzadko używana na co dzień — głównie przy singletonach lub dziedziczeniu po typach niemutowalnych (np. `int`, `tuple`).
    
- `__str__`, `__repr__`, `__len__`, `__call__`, itp.  
    Pozwalają kontrolować zachowanie obiektu w różnych kontekstach.

## 🧪 Przykład

```python
class Person:
    species = "Homo sapiens"   # Atrybut klasowy

    def __init__(self, name, age):
        self.name = name
        self._age = age   # podkreślenie = "prywatny" atrybut

    @property
    def age(self):
        """Getter – wywoływany, gdy robisz p.age"""
        return self._age

    @age.setter
    def age(self, value):
        """Setter – wywoływany, gdy robisz p.age = ..."""
        if value < 0:
            raise ValueError("Wiek nie może być ujemny!")
        self._age = value

p = Person("Kamil", 28)

print(p.age)      # 28 (getter)
p.age = 30        # setter
print(p.age)      # 30

# p.age = -10     # ValueError: Wiek nie może być ujemny!


```

---

# 🕹 Szybkie fakty (to, co trzeba wiedzieć na start)

- Klasa to definicja → instancja to obiekt.
    
- `__new__` tworzy obiekt, `__init__` go inicjalizuje.
    
- Atrybut klasowy jest wspólny, instancji — unikalny.
    
- Klasy pozwalają grupować dane + logikę w jedną strukturę.
    
- Można pisać gettery/settery, ale w Pythonie zwykle korzysta się z `@property`.

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

#### 🧙‍♂️ **GŁÓWNA STRUKTURA ANALOGII**

#### **Character — klasa bazowa (superklasa)**

W świecie RPG każdy bohater ma pewne elementy wspólne:

- HP (punkty życia)
    
- imię
    
- poziom
    

Ale **różne profesje mają własne zasoby**, własne sposoby działania i własne logiki.

Dlatego tworzymy klasy rozszerzające:

- **Warrior**
    
- **Archer**
    
- **Mage**
    

Każda dziedziczy z Character, ale dodaje własny „twist”.

---

#### 🧩 **Struktura zasobów (core idea analogii)**

#### **Warrior**

- Zasób: **Rage** _(0–100)_
    
- Im więcej rage zużyjesz, tym większe obrażenia zadane skillem.
    
- Mechanika: _„Im bardziej wkurzony, tym mocniejszy hit.”_
    

#### **Archer**

- Zasób: **Energy** _(0–100)_
    
- Każdy skill pobiera stałą ilość energii
    
- Ale strzał **zawsze trafia krytycznie** (gwarantowany crit)
    

---

#### **Mage**

- Zasób: **Mana**
    
- Wyliczana na podstawie inteligencji postaci:  
    `mana = intelligence * 10`
    
- Każdy czar kosztuje manę, a siła zależy od inteligencji
    

---

# 🧠 **Co ta analogia uczy o klasach?**

1. `Character` to **klasa bazowa**, która daje wspólne fundamenty.
    
2. Klasy pochodne (Warrior, Archer, Mage) **dziedziczą** elementy, a własne dopisują.
    
3. Każda z klas ma **inne atrybuty instancji** i własną logikę metod.
    
4. A to idealnie odwzorowuje OOP.
    

---

# 🧪 **Przykład OOP w Pythonie odzwierciedlający tę analogię**

```python
class Character:
    def __init__(self, name, level=1, hp=100):
        self.name = name
        self.level = level
        self.hp = hp

    def __str__(self):
        return f"{self.name} (Lvl {self.level}) HP:{self.hp}"


class Warrior(Character):
    def __init__(self, name, level=1, hp=120):
        super().__init__(name, level, hp)
        self.rage = 0  # 0–100

    def use_skill(self, rage_spent):
        if rage_spent > self.rage:
            return f"{self.name} nie ma wystarczająco Rage!"

        self.rage -= rage_spent
        damage = rage_spent * 2
        return f"{self.name} uderza z siłą {damage} (rage spent: {rage_spent})"


class Archer(Character):
    def __init__(self, name, level=1, hp=90):
        super().__init__(name, level, hp)
        self.energy = 100

    def use_skill(self, energy_cost=20):
        if energy_cost > self.energy:
            return f"{self.name} nie ma energii!"

        self.energy -= energy_cost
        damage = 50  # stałe obrażenia
        return f"{self.name} trafia krytycznie! DMG:{damage}"


class Mage(Character):
    def __init__(self, name, intelligence, level=1, hp=80):
        super().__init__(name, level, hp)
        self.intelligence = intelligence
        self.mana = intelligence * 10

    def use_skill(self, mana_cost):
        if mana_cost > self.mana:
            return f"{self.name} nie ma many!"

        self.mana -= mana_cost
        damage = mana_cost * (self.intelligence / 2)
        return f"{self.name} rzuca czar za {damage:.0f} DMG!"

```

---

# 🎮 **Wywołanie**

`w = Warrior("Thorgal") a = Archer("Liriel") m = Mage("Aeron", intelligence=15)  print(w.use_skill(40)) print(a.use_skill()) print(m.use_skill(30))`

---

# 🔍 **Jak to mapuje koncepcje Pythona?**

|Element Python|Analogiczny element RPG|
|---|---|
|Klasa|Typ postaci (Mag / Wojownik / Łucznik)|
|Instancja|Twój własny bohater|
|Atrybut klasowy|Stałe dla klasy (np. max HP dla wszystkich Magów)|
|Atrybut instancji|Indywidualne statystyki bohatera|
|Dziedziczenie|Profesje mają wspólne cechy, ale różne zasoby|
|`super()`|„Przejęcie cech z klasy bazowej”|
|`self`|Ten konkretny bohater wykonujący akcję|



---

### 🗃 Keyword Connections (powiązania)

- [[method]]
- [[attribute]]
- [[__new__]]
- [[__init__]]
- [[dunder method]]
- [[self]]
- [[@property]]
- [[_private_attributes]]
- [[@staticmethod]]
- [[@classmethod]]
- [[MRO]]
- [[bound method]]
- [[shadowing atrybutu]]
- [[__dict__]]
- [[__class__]]
- [[setattr]]
- [[magic methods]]

---

### 🖼 Rysunek / schemat / diagram ASCII

![[Pasted image 20251204201315.png]]

---

## ✨ Metoda Feynmana (1–2 zdania)

Klasą nazywamy definicję czegoś co chcemy opisać, dana rzecz którą opisujemy będzie instancją

---

## ⚠ Typowe błędne wyobrażenie

**Typowe błędne wyobrażenie o klasach polega na niezrozumieniu różnicy między atrybutami klasowymi a atrybutami instancji.  
Wiele osób zakłada, że działają one „tak samo”, podczas gdy ich mechanika jest zupełnie inna.**

- Do **atrybutów instancji** odwołujemy się przez `self`, ponieważ należą do _konkretnego obiektu_.
    
- Do **atrybutów klasowych** odwołujemy się przez `type(self)` lub przez samą nazwę klasy, ponieważ należą do _samej klasy_, a nie do jej instancji.
    

Co szczególnie ważne (a często pomijane):

👉 **mutowalne atrybuty klasowe** (`list`, `dict`, `set`) są _współdzielone_ między wszystkimi instancjami.  
Zmienisz wartość w jednej instancji → zobaczą ją wszystkie pozostałe.

---

## 📌 Kontrast (X vs Y)

| Cecha                                  | OOP | Funkcje |
| -------------------------------------- | --- | ------- |
| Mutowalny stan                         | ✅   | ❌       |
| Pure functions / Efekty uboczne        | ❌   | ✅       |
| Brak efektów ubocznych (pure)          | ❌   | ✅       |
| Kompozycja jako główny sposób łączenia | ❌   | ✅       |
| Dziedziczenie                          | ✅   | ❌       |
| Proste testy (stały wynik)             | ❌   | ✅       |
| Bezpieczne współbieżnie                | ❌   | ✅       |
| Dane + metody w jednym miejscu         | ✅   | ❌       |
| Dane oddzielone od funkcji             | ❌   | ✅       |
| Polimorfizm / nadpisywanie metod       | ✅   | ❌       |
| Funkcje wyższego rzędu                 | ❌   | ✅       |
| Modelowanie świata jako obiekty        | ✅   | ❌       |
| \|Transformowanie danych\|\|\|         | ❌   | ✅       |

---

## 🗂 Fiszki (SRS) #flashcards 

Co robi metoda `__new__`?
?
Tworzy nową instancję w pamięci i zwraca obiekt; wywoływana przed `__init__`.
<!--SR:!2025-12-25,16,290-->

Co robi metoda `__init__`?
?
Inicjalizuje obiekt już utworzony przez `__new__`, ustawia atrybuty instancji.
<!--SR:!2025-12-24,15,290-->

Jaka jest różnica między atrybutem klasowym a instancji?
?
Atrybut klasowy jest wspólny dla wszystkich instancji; atrybut instancji należy tylko do konkretnego obiektu.
<!--SR:!2025-12-18,7,270-->

Gdzie tworzymy atrybuty instancji?
?
W metodzie `__init__` poprzez `self.nazwa`.
<!--SR:!2025-12-20,11,270-->

Jak odwołać się do atrybutu klasowego wewnątrz instancji?
?
Przez `type(self).nazwa` lub nazwę klasy.
<!--SR:!2025-12-25,16,290-->

Dlaczego mutowalne atrybuty klasowe są niebezpieczne?
?
Bo wszystkie instancje współdzielą tę samą listę/dict/set i modyfikacje wpływają na wszystkie obiekty.
<!--SR:!2025-12-15,7,250-->

Do czego służy dekorator `@property`?
?
Tworzy getter, który pozwala odczytywać wartość jak zwykły atrybut, ale z logiką w tle.
<!--SR:!2025-12-15,7,250-->

Do czego służy `@nazwa.setter`?
?
Definiuje setter — kontroluje zmianę wartości właściwości zarządzanej przez `@property`.
<!--SR:!2025-12-23,14,290-->

Czy `self` jest słowem kluczowym?
?
Nie, to tylko konwencja nazewnicza — można użyć dowolnej nazwy.
<!--SR:!2025-12-24,15,290-->

Co reprezentuje `self` w metodzie?
?
Referencję do konkretnej instancji, na której metoda jest wywoływana.
<!--SR:!2025-12-24,15,290-->

Czy metody statyczne wymagają `self`?
?
Nie — metoda oznaczona `@staticmethod` nie przyjmuje `self` ani `cls`.
<!--SR:!2025-12-18,10,270-->

Czym różni się `@classmethod` od `@staticmethod`?
?
`@classmethod` otrzymuje jako pierwszy argument `cls`, a `@staticmethod` nie dostaje ani `self`, ani `cls`.
<!--SR:!2025-12-24,15,290-->

Czy klasa może być wywoływalna jak funkcja?
?
Tak, jeśli posiada metodę `__call__`.
<!--SR:!2025-12-23,14,290-->

Czy obiekt z `__call__` staje się funkcją?
?
Nie — tylko zachowuje się jak funkcja, ale nadal jest instancją klasy.
<!--SR:!2025-12-18,10,270-->

Co robi `__repr__`?
?
Zwraca techniczny, jednoznaczny opis obiektu — używany do debugowania.
<!--SR:!2025-12-14,4,210-->

Co robi `__str__`?
?
Zwraca czytelną, przyjazną dla użytkownika reprezentację obiektu.
<!--SR:!2025-12-20,11,270-->

Jak Python wyszukuje atrybuty?
?
Kolejność: instancja → klasa → klasy bazowe zgodnie z MRO.
<!--SR:!2025-12-12,3,210-->

Co to jest shadowing atrybutu?
?
Nadpisanie atrybutu klasowego przez stworzenie atrybutu instancji o tej samej nazwie.
<!--SR:!2025-12-21,12,270-->

---

## 🔗 Powiązane notatki