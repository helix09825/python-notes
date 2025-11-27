# Wzorzec projektowy Singleton w Pythonie

aliases: []  
tags: [theory, cs, programming]  
sr-due: true
graph: false

---

## 🧠 Co to jest?
**Singleton to wzorzec projektowy**, który zapewnia, że **istnieje tylko jedna instancja danej klasy w całej aplikacji** i że **wszędzie korzystasz z tego samego obiektu**.

W Pythonie niektóre zintegrowane obiekty, takie jak `None`, `True`, `False`, `-1`, `0` i `1`, są z założenia implementowane jako singletony. Oznacza to, że wartości te są tworzone tylko raz, a każde odwołanie do nich będzie wskazywać na ten sam obiekt w pamięci.

## 🔧 Jak to działa?
- Klasa ma **ukrytą (prywatną) instancję** przechowywaną w statycznym polu.
    
- Konstruktor jest **prywatny**, więc nie możesz utworzyć obiektu przez `new`.
    
- Tworzysz specjalną metodę (np. `getInstance()`), która:
    
    - jeśli instancja **nie istnieje** → tworzy ją
        
    - jeśli **istnieje** → zwraca już istniejącą
        
- Aplikacja korzysta zawsze z **tej jednej** instancji.

## 🧪 Przykład

```python
class Singleton:
    _instance = None  # przechowuje jedyną instancję

    def __new__(cls, *args, **kwargs):
        if cls._instance is None:
            cls._instance = super().__new__(cls)
        return cls._instance


# użycie
a = Singleton()
b = Singleton()

print(a is b)  # True
```

---

## 🧩 Mnemotechniki

### 🅰 Akronim

**Akronim:** S.I.N.G.L.E.T.O.N

**Rozwinięcie:**

- **S** – Single instance
    
- **I** – Instantiation controlled
    
- **N** – No multiple objects
    
- **G** – Global access
    
- **L** – Lazy creation
    
- **E** – Encapsulation (private constructor)
    
- **T** – Thread-safe (jeśli poprawnie zrobiony)
    
- **O** – One source of truth
    
- **N** – Not for everything!

---

### 🔄 Tłumaczenie jako analogia

**Analogia:** 
Singleton w koszykówce = tablica wyników (scoreboard)

Dlaczego?

- Na hali mogą grać 2 zespoły, 10 zawodników na boisku
    
- **Ale tablica wyników jest tylko jedna**
    
- Każdy zawodnik, trener, sędzia i kibic patrzy **na tę samą tablicę**
    

✔ Jedno źródło prawdy  
✔ Wszyscy widzą to samo  
✔ Nie można mieć dwóch tablic wyników pokazujących różne rzeczy  
✔ Każde odwołanie daje _ten sam obiekt_

---

### 🗃 Keyword Connections (powiązania)

- [[creational pattern]]
    
- [[design patterns]]
    
- [[global state]]
    


---

### 🖼 Rysunek / schemat / diagram ASCII

```
+----------------------+
|      Singleton       |
|----------------------|
| - instance           |  <-- prywatne statyczne pole
|----------------------|
| + getInstance()      |  <-- metoda zwracająca tę samą instancję
+----------------------+
          |
          v
   +--------------+
   |  obiekt #1   |  <-- jedyny obiekt w całym programie
   +--------------+

```

---

## ✨ Metoda Feynmana (1–2 zdania)


---

## ⚠ Typowe błędne wyobrażenie

---

## 📌 Kontrast (X vs Y)

| Cecha | Wzorzec projektowy Singleton w Pythonie | Koncepcja przeciwna |
| ----- | --------- | ------------------- |
|       |           |                     |
|       |           |                     |

---

## 🗂 Fiszki (SRS)

Pytanie 
??
Odpowiedź

---

## 🔗 Powiązane notatki