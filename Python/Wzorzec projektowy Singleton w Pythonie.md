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
 - [[__new__]]
 - [[__init__]]


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


Singleton to jak pudełko z zabawkami, które zawsze istnieje tylko jedno.  
Nawet jeśli ktoś spróbuje stworzyć nowe pudełko, to i tak otrzyma dokładnie to samo jedyne pudełko.  
Nie da się mieć dwóch — każda próba stworzenia kolejnego zwraca tę samą instancję.

---

## ⚠ Typowe błędne wyobrażenie

Wiele osób błędnie uważa, że Singleton to wzorzec, który tworzy „taki sam obiekt” za każdym razem.  
W rzeczywistości obiekt powstaje tylko raz — a każda kolejna próba jego utworzenia zwraca wyłącznie referencję do tej pierwszej, jedynej instancji.
---

## 📌 Kontrast (X vs Y)

| Cecha            | Singelton    | Przeciwieństwo               |
| ---------------- | ------------ | ---------------------------- |
| Liczba instancji | 1            | dowolnie wiele               |
| Tworzenie        | kontrolowane | każdy new tworzy nowy obiekt |
| Dzielenie stanu  | wspólne      | brak                         |
| Punkt dostępu    | globalny     | indywidualne instancje       |

---

## 🗂 Fiszki (SRS) #flashcards 

Co to jest wzorzec Singleton?
?
To wzorzec projektowy, który gwarantuje, że klasa ma **tylko jedną instancję**, a każdy dostęp do niej zwraca **ten sam obiekt**.
<!--SR:!2025-12-18,10,230-->

Dlaczego stosuje się Singleton?
?
Aby zapewnić jedną wspólną instancję w całej aplikacji — jedno źródło prawdy dla elementów takich jak konfiguracja, logger, połączenie do bazy czy cache.
<!--SR:!2026-01-04,26,288-->

Na czym polega działanie Singletona?
?
Przy pierwszym tworzeniu instancji obiekt jest tworzony, a przy każdej kolejnej próbie tworzenia zwracana jest **referencja do pierwszego obiektu**, zamiast tworzyć nowy.
<!--SR:!2025-12-17,9,268-->

Gdzie przechowywana jest jedyna instancja Singletona
?
W **atrybucie klasowym** (np. `_instance` w Pythonie).
<!--SR:!2026-01-07,23,252-->

Czemu w Singletonie nadpisuje się `__new__` zamiast `__init__`?
?
`__new__` tworzy obiekt — więc tam mamy kontrolę, czy powstanie nowa instancja.
`__init__` uruchamia się **po stworzeniu obiektu**, więc jest już za późno, by blokować mnożenie instancji.
<!--SR:!2025-12-18,10,252-->

---

## 🔗 Powiązane notatki