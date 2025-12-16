---
sr-due: 2025-12-16
sr-interval: 2
sr-ease: 247
---


aliases: []  
tags: [theory, cs, programming]  
sr-due: true
graph: false

#review 

---

## 🧠 **Co to jest moduł w Pythonie (proste, rozmowowe wyjaśnienie)**

**Moduł** w Pythonie to _po prostu plik z kodem_, który możemy **zaimportować**, aby użyć funkcji, klas albo zmiennych, które ktoś już napisał.  
Dzięki modułom nie musimy pisać wszystkiego od zera — możemy **organizować kod w mniejsze części** oraz używać kodu innych osób (standard library, pip packages).

**Jedno zdanie na rozmowę:**

> Moduł to plik z definicjami funkcji, klas i zmiennych, który można zaimportować do innego pliku, aby ponownie wykorzystać kod i organizować projekt w logiczne części.

### 📦 **Jak importować moduły?**

#### 1️⃣ `import time`

Importujesz cały moduł.

```python
import time

time.sleep(1)
print(time.time())

```

**Kiedy używać?**  
Gdy chcesz wyraźnie widzieć, _z którego modułu coś pochodzi_. Dobre do czytelności.

#### 2️⃣ `import time as t` — aliasowanie

```python
import time as t

t.sleep(1)
```

**Po co?**  
– skrócenie nazwy  
– czytelność w dużych projektach (np. `import numpy as np`)

#### 3️⃣ `from time import time`

```python
from time import time
print(time())
```

**Co to robi?**  
– importuje _konkretną funkcję_ z modułu  
– nie musisz pisać `time.time()`  
– ale możesz dostać konflikt nazw, jeśli masz własną funkcję `time()`

#### 4️⃣ `from time import time, sleep`

Importujesz kilka funkcji naraz:

```python
from time import time, sleep
```

**Kiedy używać?**  
Gdy korzystasz z 2–3 funkcji i chcesz czystego kodu **bez aliasów modułów**.

#### 5️⃣ ❌ `from time import *` — dlaczego to jest zły pomysł

```python
from time import *
```

**Problemy:**

- Nie wiesz, co dokładnie importujesz
- Ryzyko nadpisania nazw
- Kod jest nieczytelny
- Lintery i PEP8 odradzają tego używania
- Może spowolnić start aplikacji

**Kiedy używać?**  
→ **Nigdy na rozmowie nie mów, że używasz.**  
Wyjątek: notebooki edukacyjne lub szybkie eksperymenty.

#### 🔍 **Narzędzia do eksplorowania modułów**

### ✅ `dir(time)`

Pokazuje listę atrybutów modułu.

```python
import time print(dir(time))
```

**Do czego na rozmowie?**  
Pokazujesz, że potrafisz eksplorować API modułu, kiedy nie znasz funkcji.

#### ✅ `help(time)`

Wyświetla dokumentację modułu.

```python
help(time)
```

**Dlaczego to jest super?**  
– pokazuje, że umiesz samodzielnie czytać dokumentację  
– to jest _najbardziej seniorskie narzędzie_ jakie początkujący ignorują

## 🧩 **Bonus — jak Python odnajduje moduły? (krótko na rozmowę)**

Python szuka modułów w kolejności:

1. katalog bieżący
2. katalogi na `PYTHONPATH`
3. standardowa biblioteka
4. moduły zainstalowane przez pip

To mechanizm **module search path** (`sys.path`).

> To świadczy, że rozumiesz podstawy importów.

## ` if __name__ == "__main__"`

```python
print ("Always executed") 

if __name__ == "__main__": 
	print ("Executed when invoked directly") 
else: 
	print ("Executed when imported")
```

## 🔧 Jak to działa?


## 🧪 Przykład

```python
from time import sleep
```

---

## 🧩 Mnemotechniki

### 🅰 Akronim

#### 🧠 **Akronim PL: „B-Ś-S-P” → „**B**rak **Ś**cieżki? **S**zukaj **P**aczek”**

**B** – _Bieżący katalog_  
**Ś** – _Ścieżki z `PYTHONPATH`_  
**S** – _Standardowa biblioteka_  
**P** – _Pip packages (zainstalowane moduły)_

👉 Zapamiętanie:  
**„Brak Ścieżki? Szukaj Paczek”**  
Czyli: najpierw bieżący katalog, potem `PYTHONPATH`, następnie standard library, a na końcu paczki pip.


---

### 🔄 Tłumaczenie jako analogia

Moduły w Pythonie wyobrażam sobie jako skrzynki z narzędziami stojące w warsztatowych szafkach. `import` przynosi całą skrzynkę na stół, `from` wyciąga pojedyncze narzędzie, aliasy skracają etykiety, a wildcard import to wysypanie całej skrzynki na blat. Python szuka skrzynek kolejno: w bieżącym katalogu, w prywatnych półkach PYTHONPATH, w standardowej bibliotece i w paczkach pip.

---

### 🗃 Keyword Connections (powiązania)

- [[import]]
    
- [[from_import]]
    
- [[alias]]
    
- [[wildcard_import]]
    
- [[module_namespace]]
    
- [[sys_path]]
    
- [[module_search_order]]
    
- [[PYTHONPATH]]
    
- [[dir]]
    
- [[help]]
    
- [[package]]
    
- [[__init__file]]
	
- [[pip]]
	
- [__name__]

---

### 🖼 Rysunek / schemat / diagram ASCII

![[Pasted image 20251212074840.png]]

---

## ✨ Metoda Feynmana (1–2 zdania)
Moduły w Pythonie to **skrzynki z narzędziami zawierające funkcje, klasy i zmienne**, które możemy wczytać do naszego pliku tak, by korzystać z gotowych elementów zamiast budować wszystko od zera.  
Możemy importować **całą skrzynkę**, wyciągnąć z niej **konkretne narzędzie**, albo nadać jej **alias**, aby wygodniej z niej korzystać w kodzie.


---

## ⚠ Typowe błędne wyobrażenie
1. Każdy moduł nie musi być zawsze plikiem `.py`, mogą to być moduł wbudowane lub ładowane z C
2. Moim błędnym założeniem była informacja, że moduł jest ładowany przy każdym imporcie. Tak naprawdę moduł jest ładowany raz i cache'owany w `sys.modules`.
3. `pip` instaluje paczki w lokalizacji, która **już znajduje się na `sys.path`** (site-packages).

---


---

## 🗂 Fiszki (SRS) #flashcards 

Czy moduł w Pythonie to zawsze plik `.py`?
?
Nie, moduł może być też wbudowany lub ładowany dynamicznie, a nie tylko z pliku `.py`.
<!--SR:!2025-12-18,3,228-->

Czy `import time` ładuje moduł od nowa przy każdym imporcie?
?
Nie, moduł jest ładowany raz i przechowywany w cache w `sys.modules`.
<!--SR:!2025-12-16,2,230-->

Czy `import` wykonuje kod znajdujący się na top-level modułu?
?
Tak, cały kod na najwyższym poziomie modułu wykonuje się przy pierwszym imporcie.
<!--SR:!2025-12-16,3,250-->

Czy `import time` pozwala wywołać `sleep()` bez prefiksu?
?
Nie, funkcje modułu są dostępne przez namespace, np. `time.sleep()`.
<!--SR:!2025-12-16,3,250-->

Czy `from time import sleep` dodaje `sleep` do namespace bieżącego pliku?
?
Tak, dlatego można wywołać `sleep()` bez użycia `time.`.
<!--SR:!2025-12-16,3,250-->

Czy alias w imporcie zmienia nazwę modułu globalnie?
?
Nie, alias to tylko lokalna referencja w danym pliku.
<!--SR:!2025-12-17,4,270-->

Czy dwa pliki mogą korzystać z tego samego modułu bez jego ponownego ładowania?
?
Tak, oba pliki odwołują się do tego samego obiektu modułu w `sys.modules`.
<!--SR:!2025-12-16,3,250-->

Czy Python zawsze sprawdza bieżący katalog jako pierwszy przy imporcie?
?
Tak, dlatego lokalny plik może nadpisać moduł standardowej biblioteki.
<!--SR:!2025-12-16,3,250-->

Czy plik `time.py` w projekcie może przechwycić `import time`?
?
Tak, jeśli znajduje się w bieżącym katalogu lub wcześniej na `sys.path`.
<!--SR:!2025-12-20,5,248-->

Czy `from module import *` importuje tylko funkcje?
?
Nie, importuje wszystko zdefiniowane w `__all__` lub wszystkie publiczne nazwy.
<!--SR:!2025-12-16,2,230-->

Czy używanie `from module import *` jest dobrą praktyką w produkcyjnym kodzie?
?
Nie, ponieważ prowadzi do konfliktów nazw i utraty czytelności.
<!--SR:!2025-12-16,3,250-->

Czy `dir(module)` pokazuje tylko funkcje modułu?
?
Nie, pokazuje wszystkie atrybuty modułu, w tym klasy i zmienne.
<!--SR:!2025-12-17,3,248-->

Czy `help(module)` korzysta z docstringów?
?
Tak, wyświetla dokumentację opartą głównie na docstringach.
<!--SR:!2025-12-16,2,228-->

Czy `pip install` działa niezależnie od `sys.path`?
?
Nie, paczki instalowane przez pip trafiają do lokalizacji, która znajduje się na `sys.path`.
<!--SR:!2025-12-16,1,188-->

Czy `sys.modules` ma wpływ na szybkość kolejnych importów?
?
Tak, ponieważ Python nie ładuje ponownie już zaimportowanych modułów.
<!--SR:!2025-12-17,3,250-->

Czym jest PYTHONPATH?
?
PYTHONPATH to zmienna środowiskowa, która dodaje własne katalogi do sys.path przy starcie Pythona, zanim sprawdzona zostanie standard library i site-packages.
<!--SR:!2025-12-16,2,246-->


---

## 🔗 Powiązane notatki
https://realpython.com/python-import/
https://stackoverflow.com/questions/419163/what-does-if-name-main-do