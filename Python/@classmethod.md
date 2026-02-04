aliases: []  
tags: [theory, cs, programming]  
sr-due: true
graph: false

---

## 🧠 Co to jest?
@classmethod jest to metoda która jest powiązana ze swoją klasą a nie instancją 

## 🔧 Jak to działa?
@classmethod jako 1 argument przekazuje cls zamiast self, więc jesteśmy wstanie pracować na atrybutach klasowych 

## 🧪 Przykład

```python
class Player:
    # Atrybut klasowy – wspólny dla wszystkich zawodników
    current_play = "Pick and Roll"

    def __init__(self, name):
        self.name = name

    @classmethod
    def change_play(cls, new_play):
        """Zmienia zagrywkę dla całego zespołu."""
        cls.current_play = new_play

    def show_status(self):
        return f"{self.name} gra według zagrywki: {self.current_play}"


# --- Użycie ---
p1 = Player("Kobe")
p2 = Player("Shaq")

print(p1.show_status())
print(p2.show_status())

# Zmiana zagrywki przez jednego gracza
Player.change_play("Triangle Offense")

print("\nPo zmianie zagrywki:")
print(p1.show_status())
print(p2.show_status())
```

---

## 🧩 Mnemotechniki

### 🅰 Akronim

**C.L.A.S.S.**

### **C — Common state**

Metoda operuje na **wspólnych danych klasy**, nie na pojedynczych instancjach.

### **L — Linked to class**

Związana jest z **klasą**, a nie z obiektem — pierwszy argument to `cls`.

### **A — Affects all instances**

Zmiany dokonane w metodzie dotyczą **wszystkich obiektów** tej klasy.

### **S — Shared behavior**

Służy do definiowania **zachowań współdzielonych** przez instancje.

### **S — Setup factories**

Często używana do **tworzenia obiektów w alternatywny sposób** (factory methods).

---

### 🔄 Tłumaczenie jako analogia

**Analogia:**

**„Kiedy jeden zawodnik zmieni zagrywkę, zmienia się ona dla całej drużyny.”**

W klasie:

- **Drużyna** → klasa
    
- **Zagrywka drużyny** → atrybut **klasowy**
    
- **Zawodnik** → instancja klasy
    
- **Zmiana zagrywki** → wywołanie `@classmethod`
    

Czyli:

> **@classmethod działa jak tablica trenera – zmiana na tablicy obowiązuje wszystkich zawodników.**

Nie ustawiasz zagrywki tylko dla jednego gracza — wpływa ona na **całą drużynę**, bo dotyczy **klasy**, nie instancji.

---

### 🗃 Keyword Connections (powiązania)

- [[Class]]  
- [[shadowing atrybutu]]


---

### 🖼 Rysunek / schemat / diagram ASCII

![[Pasted image 20251206234026.png]]

---

## ✨ Metoda Feynmana (1–2 zdania)

Odnoszenie się do metody klasowej jest jak ogłoszenie dla całego gatunku.
To nie jest informacja wysłana do jednego człowieka — tylko do wszystkich ludzi naraz.

Przykład:
Jesteśmy jednym „gatunkiem” → class Human.
I gdy tylko nadchodzi poniedziałek, wszyscy automatycznie wiedzą, że wolne się skończyło.
Nie musisz każdemu mówić z osobna.
Wystarczy jedno ogłoszenie na poziomie klasy, a każda instancja — każdy człowiek — to przejmuje.

To właśnie metoda klasowa:
🔹 zmienia stan całej grupy,
🔹 działa globalnie na wszystkich jej przedstawicieli,
🔹 nie dotyczy tylko jednej instancji.

---

## ⚠ Typowe błędne wyobrażenie
Wielu programistów błędnie zakłada, że **zmiana atrybutu klasowego automatycznie aktualizuje go dla wszystkich instancji**, niezależnie od tego, czy instancje wcześniej w jakikolwiek sposób manipulowały tym atrybutem.  
W rzeczywistości, jeśli instancja **choć raz nadpisze** atrybut klasowy (np. przez `instance.attr = value`), tworzy własną kopię atrybutu i **przestaje patrzeć na wartość z klasy**.  
To nazywa się **shadowing**: instancja „maskuje” atrybut klasowy i od tej chwili **nie reaguje na żadne zmiany dokonane w klasie**, nawet jeśli zmieniasz je metodą klasową.

---

## 📌 Kontrast (X vs Y)

|Cecha|@classmethod|Metoda instancji|
|---|---|---|
|Pierwszy parametr|`cls`|`self`|
|Poziom działania|na klasie|na instancji|
|Wpływ na stan|wpływa na **wszystkie** instancje (o ile nie shadowing)|wpływa tylko na konkretny obiekt|
|Źródło danych|stan klasy|stan instancji|
|Wywołanie|przez klasę lub instancję|zwykle przez instancję|
|Dostęp do klasy|tak|pośrednio (przez `type(self)`)|
|Dostęp do instancji|nie|tak|
|Typowe zastosowania|konstrukcja obiektów, konfiguracja globalna|logika indywidualnego obiektu|
|Shadowing a działanie|nie widzi shadowingu instancji|shadowing nie ma znaczenia|
|Zakres efektu zmian|globalny w obrębie klasy|lokalny dla jednego obiektu|


---

## 🗂 Fiszki (SRS) #flashcards 

Co dostaje jako pierwszy argument metoda klasowa?  
**?**  
`cls`, czyli referencję do klasy, a nie instancji.

---

Kiedy metoda klasowa działa globalnie na wszystkie instancje?  
**?**  
Gdy modyfikuje lub odczytuje atrybut klasowy, który nie został przesłonięty przez instancję.

---

Co się dzieje, gdy wykonasz `instance.attr = value` dla atrybutu klasowego?  
**?**  
Tworzysz atrybut instancji i tworzysz shadowing, czyli maskowanie klasy przez instancję.

---

Czy shadowing wpływa na możliwość globalnej aktualizacji atrybutów przez classmethod?  
**?**  
Tak — instancja po shadowingu ignoruje zmiany w klasie.

---

Dlaczego mutowalne atrybuty klasowe są „niebezpieczne”?  
**?**  
Bo wszystkie instancje współdzielą jeden obiekt, więc mutacja wpływa globalnie.

---

Czym różni się przypisanie od mutacji w kontekście atrybutów klasowych?  
**?**  
Przypisanie tworzy shadowing (nowy obiekt w instancji), mutacja edytuje wspólny obiekt.

---

Czy metoda klasowa ma dostęp do `self`?  
**?**  
Nie — chyba że instancję przekażesz jako argument ręcznie.

---

Czy metoda instancji automatycznie ma dostęp do atrybutów klasowych?  
**?**  
Tak — o ile nie ma w instancji lokalnego shadowingu.

---

Jak sprawić, by instancja po shadowingu znów widziała wartość z klasy?  
**?**  
Usunąć atrybut instancji: `del instance.attr`.

---

Czy metoda klasowa może pełnić rolę alternatywnego konstruktora?  
**?**  
Tak — to jedno z jej głównych zastosowań.

---

## 🔗 Powiązane notatki