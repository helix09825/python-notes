aliases: []  
tags: [theory, cs, programming]  
sr-due: true
graph: false

---

## 🧠 Co to jest?

**Pakowanie** to mechanizm, w którym **wiele wartości jest automatycznie łączonych w jedną strukturę** — najczęściej _krotkę_ (tuple) — i przypisywanych do **jednej zmiennej**.
## 🔧 Jak to działa?

Python widzi kilka wartości oddzielonych przecinkami i automatycznie pakuje je w jedną krotkę.

Aby przypisać zmienne do listy należy użyć zmiennej z * ale tylko jeśli będzie w krotce lub liście   
## 🧪 Przykład

```python

a = 1, 2, 3 # tuple 

*a, = 1, 2, 3, 4, 5		# a = [1, 2, 3, 4, 5]
(*a,) = 1, 2, 3, 4, 5		# a = [1, 2, 3, 4, 5]
[*a] = 1, 2, 3, 4, 5		# a = [1, 2, 3, 4, 5]
*a = 1, 2, 3, 4, 5		# SyntaxError: starred assignment target must be in a list or tuple

```

### 📌 **Pakowanie przy argumentach funkcji**

Python używa pakowania także wtedy, gdy funkcja zbiera wiele argumentów

```python
def f(*args, **kwargs):
	pass
```
- `*args` pakuje wszystkie _argumenty pozycyjne_ w **krotkę**
    
- `**kwargs` pakuje wszystkie _argumenty nazwane_ w **słownik**
    

Ważne są *  a nie same słowa 

To również jest **pakowanie**, tylko w kontekście parametrów funkcji.
---

## 🧩 Mnemotechniki

### 🅰 Akronim

**Akronim:** **ASTA**

### **A** _— Asterisk_

### **S** _— Stays in a_

### **T** _— Tuple or_

### **A** _— Array (lista)_


---

### 🔄 Tłumaczenie jako analogia

**Analogia:**
**Pakowanie** możesz wyobrazić sobie jak **szatnię teatralną**.

Goście przychodzą na spektakl i oddają swoje płaszcze — **każdy płaszcz to wartość**.  
Szatniarz bierze je **dokładnie w kolejności**, w jakiej przyszły, i odkłada je **do jednego wieszaka zbiorczego**.  
Ten wieszak to **krotka**, czyli jedno miejsce, w którym lądują wszystkie płaszcze razem.

- Goście = wartości
    
- Oddanie płaszczy = zapis `a = 1, 2, 3`
    
- Wieszak zbiorczy = tuple
    
- Zmienna = nazwa szatni
    

Kiedy używasz `*` (np. `a, *b, c = ...`), to tak, jakbyś powiedział szatniarzowi:

> „Zbierz **wszystkie nadmiarowe płaszcze**, które nie zmieściły się na pozostałe wieszaki.”

Czyli:

- `a` dostaje **pierwszy płaszcz**
    
- `c` dostaje **ostatni**
    
- a `b` dostaje **całą resztę** — pakowaną automatycznie do listy.
    

---

### 🧠 Dlaczego to działa dobrze?

- Szatnia = krotka → nie możesz dopchać tam kolejnych płaszczy
    
- `*` = „zbieracz reszty” → bierze wszystko, czego nie przydzielono
    
- kolejność oddawania = kolejność pakowania

---

### 🗃 Keyword Connections (powiązania)

[[*args]]
[[*kwargs]]
[[starred target]]
[[starred-assignment]]

---

### 🖼 Rysunek / schemat / diagram ASCII

![[Pasted image 20251130180211.png]]

---

## ✨ Metoda Feynmana (1–2 zdania)
Pakowanie zmiennych to wrzucenie wszystkich swoich zabawek do 1 skrzynki w której występują jako Krotka. 

---

## ⚠ Typowe błędne wyobrażenia

### **1. „Pakowanie powoduje tworzenie listy.”**

Nie. **Pakowanie zawsze tworzy krotkę (tuple)** — lista pojawia się jedynie przy `*` po lewej stronie przypisania, bo taka jest reguła składni.

---

### **2. „`*b` to argument pozycyjny.”**

W przypisaniu `a, *b = ...` `b` **nie ma nic wspólnego z argumentami funkcji**.  
To **starred target** — zmienna, która zbiera resztę wartości.

---

### **3. „W jednym przypisaniu może być tylko jeden argument pozycyjny `*x`.”**

Nie chodzi o argumenty.  
Python nie pozwala na więcej niż **jeden starred target** w jednej strukturze po lewej stronie:

`*a, *b = ...  # SyntaxError`

To ograniczenie składni przypisania, nie funkcji.

---

## 📌 Kontrast (X vs Y)

| Cecha                                                | Pakowanie | Rozpakowywanie |
| ---------------------------------------------------- | --------- | -------------- |
| Łączy wiele wartości w jedną strukturę.              | ✅         | ❌              |
| Rozdziela jedną strukturę na wiele wartości.         | ❌         | ✅              |
| Zachodzi automatycznie przy przecinku.               | ✅         | ❌              |
| Wymaga dopasowania liczby zmiennych po lewej stronie | ❌         | ✅              |
| Może używać `*` jako „zbieracza reszty”              | ✅         | ❌              |
| Używane przy `return x, y, z`                        | ✅         | ❌              |
| **Używane przy `a, b, c = ...`**                     | ❌         | ✅              |
| **Powstaje tuple (krotka)**                          | ✅         | ❌              |
| Jedna wartość → wiele zmiennych                      | ❌         | ✅              |
| Wiele wartości → jedna zmienna                       | ✅         | ❌              |

---

## 🗂 Fiszki (SRS) #flashcards 

Co tak naprawdę tworzy tuple — nawiasy () czy przecinek?
?
Tuple powstaje od przecinka, nawiasy są opcjonalne i służą tylko do czytelności.
<!--SR:!2025-12-03,3,250-->

Dlaczego `a = (1)` nie tworzy tuple?
?
Bo nie ma przecinka; `(1)` to zwykła liczba w nawiasie.
<!--SR:!2025-12-04,4,270-->

Co oznacza `*b` po lewej stronie przypisania (`a, *b = ...`)?
?
To starred target — zmienna zbierająca wszystkie pozostałe elementy, zawsze jako listę.
<!--SR:!2025-12-04,4,270-->

Dlaczego w przypisaniu `*a, *b = [1, 2, 3]` wystąpi błąd?
?
Bo w jednej strukturze przypisania może istnieć tylko jeden starred target (`*x`).
<!--SR:!2025-12-03,3,250-->

Czym różni się `*` w przypisaniu od `*` w wywołaniu funkcji?
?
W przypisaniu `*` zbiera resztę, a w wywołaniu funkcji `*` rozpakowuje elementy do argumentów.
<!--SR:!2025-12-04,4,270-->

Co dokładnie pakuje `*args` w definicji funkcji?
?
Pakuje wszystkie argumenty pozycyjne do jednej krotki (`tuple`).
<!--SR:!2025-12-03,3,250-->

Co dokładnie pakuje `**kwargs` w definicji funkcji?
?
Pakuje wszystkie argumenty nazwane do słownika (`dict`).
<!--SR:!2025-12-04,4,270-->

Czy pakowanie może stworzyć listę?
?
Nie — pakowanie zawsze tworzy tuple; lista pojawia się tylko przy starred assignment (`*b = ...`).
<!--SR:!2025-12-04,4,270-->

Dlaczego `return 1, 2, 3` zwraca tuple, mimo że nie ma nawiasów?
?
Bo Python automatycznie pakuje wartości oddzielone przecinkami do tuple.
<!--SR:!2025-12-03,3,250-->

Czy `b` w `a, *b = ...` jest „argumentem pozycyjnym”?
?
Nie — to zwykła zmienna zbierająca resztę elementów, nie ma związku z argumentami funkcji.
<!--SR:!2025-12-04,3,250-->

Co jest przeciwieństwem pakowania?
?
Rozpakowywanie — dzielenie jednej struktury na wiele zmiennych.
<!--SR:!2025-12-04,4,270-->

Dlaczego rozpakowywanie może dać błąd „too many values to unpack”?
?
Bo liczba zmiennych po lewej musi zgadzać się z liczbą elementów po prawej — chyba że używasz `*`.
<!--SR:!2025-12-04,4,270-->

---

## 🔗 Powiązane notatki
[[Rozpakowywanie]]