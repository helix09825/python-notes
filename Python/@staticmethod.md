aliases: []  
tags: [theory, cs, programming]  
sr-due: true
graph: false

---

## 🧠 Co to jest?

`@staticmethod` to **metoda należąca do klasy**, ale **niepowiązana ani z instancją (`self`), ani z klasą (`cls`)**.  
To po prostu **zwykła funkcja umieszczona w przestrzeni nazw klasy**.

Można ją wywołać przez klasę **lub** instancję, ale **nie ma dostępu** do:

- atrybutów instancji → brak `self`
    
- atrybutów klasy → brak `cls`

## 🔧 Jak to działa?
- Pobiera obiekt `staticmethod` z klasy
    
- Z tego obiektu wyciąga oryginalną funkcję
    
- Wywołuje ją **bez wstrzykiwania żadnych dodatkowych argumentów**  
    → żadnego `self`, żadnego `cls`.

## 🧪 Przykład

```python
class MathTools:
    @staticmethod
    def double(value):
        return value * 2

print(MathTools.double(10))   # 20

```

---

## 🧩 Mnemotechniki

---

### 🔄 Tłumaczenie jako analogia

**Analogia:** 

Narzędzie przechowywane w klasie dla porządku, ale działające niezależnie od klasy i jej instancji.

---

### 🗃 Keyword Connections (powiązania)

- [[Class]]

---

### 🖼 Rysunek / schemat / diagram ASCII

```
+--------------------------------------+
|           SZAFKA KLUBOWA             |
|         (przestrzeń klasy)           |
|                                      |
|  +-------------+   +--------------+  |
|  |  Piłka      |   |  Opaska      |  |
|  | (instancja) |   | (instancja)  |  |
|  +-------------+   +--------------+  |
|                                      |
|  +-------------------------------+   |
|  |   KALKULATOR (staticmethod)   |   |
|  |  - nie zna drużyny            |   |
|  |  - nie zna zawodników         |   |
|  |  - działa na podanych danych  |   |
|  +-------------------------------+   |
|                                      |
+--------------------------------------+

 ZAWODNIK (instancja) ---> może użyć kalkulatora
 TRENER   (klasa)     ---> może użyć kalkulatora

ALE kalkulator nie wie nic o nich — tylko liczy to, co mu podasz.

```

---

## ✨ Metoda Feynmana (1–2 zdania)
`@staticmethod` to po prostu **narzędzie umieszczone w klasie dla porządku**, które nie korzysta ani z instancji, ani z klasy. Działa jak **kuchenna waga** — kładziesz na niej dane, ona wykonuje swoje zadanie i niczego w klasie ani instancji nie zmienia.

---

## ⚠ Typowe błędne wyobrażenie
#### ❗ Myślisz, że `@staticmethod` jest _delikatnie szybszy_, bo nie dostaje ukrytego argumentu (`self` / `cls`).

To brzmi logicznie, ale **nie jest prawdziwe**.

### ✔️ Jak jest naprawdę?

`@staticmethod` **nie jest szybszy** od zwykłej funkcji — działa _dokładnie z tą samą prędkością_, bo:

- funkcja i tak musi zostać wyciągnięta z obiektu `staticmethod`,
    
- overhead wywołania jest praktycznie identyczny,
    
- różnica nie jest mierzona nawet w mikrosekundach — jest statystycznie _zerowa_.
    

**Staticmethod nie jest optymalizacją wydajności — jest optymalizacją organizacji kodu (czyli struktury i czytelności).**

### Dlaczego to jest ważne?

Bo jeśli myślisz:

> „użyję staticmethod, bo będzie szybszy”

to później takie „intuicyjne” przekonanie wpływa na decyzje architektoniczne.  
Staticmethod istnieje **wyłącznie** po to, żeby powiedzieć:

> „Ta funkcja logicznie należy do tej klasy, ale nie dotyka klasy ani instancji”.

**Zero optymalizacji wydajnościowej.**

---

## 📌 Kontrast (X vs Y)

|Cecha|`@staticmethod`|`@classmethod`|
|---|---|---|
|Dostęp do klasy|❌ Brak dostępu do `cls`|✔️ Otrzymuje `cls` automatycznie|
|Dostęp do instancji|❌ Brak `self`|❌ Brak `self`|
|Automatycznie przekazywany argument|❌ Żaden|✔️ `cls`|
|Modyfikowanie stanu klasy|❌ Niemożliwe (bez ręcznego podania klasy)|✔️ Tak, może zmieniać atrybuty klasy|
|Zastosowanie|Funkcje narzędziowe, walidacje, transformacje|Fabryki, alternatywne konstruktory, logika klasowa|
|Logiczna przynależność|Funkcja trzymana w klasie „dla porządku”|Metoda, która _reprezentuje zachowanie klasy_|
|Dziedziczenie|Nie reaguje na dziedziczenie|Działa w pełni z dziedziczeniem (działa na podklasie)|
|Wywołanie|`C.func()` lub `obj.func()` — brak różnicy|`C.func()` lub `obj.func()` → zawsze działa na klasie|

---

## 🗂 Fiszki (SRS) #flashcards 

Czego nie dostaje metoda oznaczona @staticmethod?
?
Nie dostaje żadnego ukrytego argumentu — ani self, ani cls.
<!--SR:!2025-12-24,11,270-->

---

Kiedy używamy @staticmethod zamiast zwykłej funkcji w module?
?
Gdy funkcja logicznie należy do klasy, ale nie korzysta z jej stanu — trzymamy ją tam dla porządku.
<!--SR:!2025-12-22,7,270-->

---

Jaka jest największa różnica między @staticmethod a @classmethod?
?
@classmethod dostaje cls i działa na klasie; @staticmethod nie dostaje nic i działa jak zwykła funkcja.
<!--SR:!2025-12-28,15,290-->

---

## 🔗 Powiązane notatki