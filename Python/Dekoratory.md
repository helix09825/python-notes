aliases: []  
tags: [theory, cs, programming]  
sr-due: true
graph: false

---

## 🧠 Co to jest?
Dekorator to funkcja, która przyjmuje inną funkcję jako argument, „opakowuje” ją i zwraca nową wersję z rozszerzonym zachowaniem — bez zmieniania oryginalnego kodu. Mechanizm ten jest inspirowany wzorcem projektowym _Dekorator_, który polega na dynamicznym dodawaniu funkcjonalności.

To _dodawanie zachowania przed lub po_ działaniu funkcji.

## 🔧 Jak to działa?
1. **Piszesz funkcję, która przyjmuje funkcję**
    
2. **Wewnątrz tworzysz funkcję „opakowującą”**
    
3. **Zwracasz ją**
    
4. **Używasz `@nazwa_dekoratora` nad funkcją, którą chcesz udekorować**

## 🧪 Przykład

```python
def dekorator(func):
    def wrapper():
        print("Zanim funkcja się wykona")
        result = func()
        print("Po wykonaniu funkcji")
        return result
    return wrapper

@dekorator
def hello():
    print("Hello!")

hello()

```

---

## 🧩 Mnemotechniki

### 🅰 Akronim

**Akronim:** O-O-Z-W

**Rozwinięcie:**

- **O** – **Otrzymuje funkcję**  
- **O** – **Opakowuje ją**  
- **Z** – **Zwraca nową wersję**  
- **W** – **Wzorzec projektowy (inspiracja)**

---

### 🔄 Tłumaczenie jako analogia

**Analogia:**
**Hot-dog z Żabki jako system dekoratorów**

#### **Parówka → funkcja (oryginalna logika)**

To jest “goła” funkcja.  
Może działać sama — parówka to parówka.

#### **Bułka → dekorator opakowujący**

Bułka:

- **nie zmienia parówki**,
    
- **opakowuje ją**,
    
- dodaje „zachowanie”: trzyma wszystko razem, nadaje formę, umożliwia zjedzenie.
    

W Pythonie bułka = funkcja wrapper.

#### **Sos → kolejny dekorator, który rozszerza zachowanie**

Do hot-doga możesz dodać:

- ketchup,
    
- musztardę,
    
- jalapeno,
    
- majonez truflowy, jak ktoś ma fantazję 😂
    

Każdy sos:

- **nie zmienia parówki**,
    
- tylko **dodaje nową warstwę działania** (smak → nowe zachowanie).
    

To jest dokładnie to, co robi dekorator w Pythonie.

---

### 🗃 Keyword Connections (powiązania)

- [[meta function]]
    
- [[syntactic sugar]]
    
- [[design patterns]]
    

---

### 🖼 Rysunek / schemat / diagram ASCII


![[Pasted image 20251202193057.png]]

---

## ✨ Metoda Feynmana (1–2 zdania)
Dekorator to taki „wrapper” dla Twojej funkcji — dodaje nowe zachowanie bez ingerowania w jej oryginalny kod.  
To jak w Żabce: masz parówkę (funkcję), do której dokładane są kolejne warstwy — bułka i sosy — pełniące rolę dekoratorów.

---

## ⚠ Typowe błędne wyobrażenie

- **„Dekorator musi zawsze zwracać funkcję.”**  
    W rzeczywistości dekorator powinien zwrócić _jakiś obiekt_, który zastąpi oryginał — może to być funkcja, klasa, obiekt wywoływalny, a nawet coś innego. Brak zwracanej wartości jest technicznie możliwy, ale praktycznie psuje działanie programu.
    
- **„Dekorator przyjmuje wyłącznie funkcję jako argument.”**  
    Dekorator przyjmuje _callable_ lub obiekt, który dekoruje — może to być funkcja, metoda, klasa lub dowolny inny element oznaczony `@`.
    
- **„Dekorator wykonuje się dopiero przy wywołaniu funkcji.”**  
    To półprawda — wykonuje się _od razu_, w momencie definicji funkcji. Dopiero wrapper (czyli udekorowana wersja) działa przy późniejszym wywołaniu.
    
- **„Dekorator nie może mieć własnych argumentów.”**  
    Może — i jest to częsty wzorzec. Dekorator z argumentami to po prostu funkcja, która _zwraca_ właściwy dekorator (tzw. „fabryka dekoratorów”).

---

## 📌 Kontrast (X vs Y)

| Cecha                                       | Dekoratory | Hard-coding |
| ------------------------------------------- | ---------- | ----------- |
| Dynamiczne rozszerzanie funkcji             | ✅          | ❌           |
| Dodawanie zachowania bez modyfikacji źródła | ✅          | ❌           |
| Warstwowe opakowywanie funkcji              | ✅          | ❌           |
| Oddzielanie logiki bazowej od dodatkowej    | ✅          | ❌           |
| Wielokrotne użycie tego samego rozszerzenia | ✅          | ❌           |
| Wykonywany przy definicji funkcji           | ✅          | ❌           |
| Funkcje jako obiekty pierwszej klasy        | ✅          | ❌           |

---

## 🗂 Fiszki (SRS) #flashcards 

**Co to jest dekorator?  
?  
Funkcja opakowująca, która rozszerza działanie innej funkcji bez zmiany jej kodu.**

**Co zwraca dekorator?  
?  
Obiekt zastępujący oryginalną funkcję (najczęściej wrapper).**

**Kiedy wykonuje się dekorator?  
?  
Przy definicji funkcji (czas dekorowania).**

**Kiedy wykonuje się wrapper?  
?  
Dopiero przy wywołaniu udekorowanej funkcji.**

**Jak działa stosowanie wielu dekoratorów?  
?  
Tworzą warstwy — wykonywane są od góry do dołu, wywoływane od dołu do góry.**

**Czy dekorator może mieć własne argumenty?  
?  
Tak, wtedy tworzy „fabrykę dekoratorów” (funkcja zwracająca dekorator).**

**Jaka jest przeciwna koncepcja do dekoratorów?  
?  
Hard-coding — modyfikacja funkcji bezpośrednio w jej kodzie.**

**Z czego korzystają dekoratory technicznie?  
?  
Z funkcji jako obiektów pierwszej klasy i closure.**

**Co dekorator najczęściej opakowuje?  
?  
Funkcję, metodę lub klasę.**

**Czy dekorator musi zwrócić funkcję?  
?  
Nie — musi zwrócić _coś_, co zastąpi oryginał (funkcja, klasa, callable).**

---

## 🔗 Powiązane notatki