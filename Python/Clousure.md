aliases: []  
tags: [theory, cs, programming]  
sr-due: true
graph: false

---

## 🧠 Co to jest?
W Pythonie używamy _domknięć_ (ang. _closure_), gdy funkcje wewnętrzne są zamknięte w zewnętrznej funkcji – innymi słowy, gdy zagnieżdżona funkcja odwołuje się do wartości w zamykającym ją zakresie. Dzięki temu możemy uniknąć nadużywania wartości globalnych.

Domknięcia przydają się, gdy musimy zaimplementować kilka metod, ale ich liczba nie wystarcza do utworzenia klasy. Domknięcie zwiększy wtedy czytelność naszego rozwiązania. Jeśli liczba atrybutów i metod jest znacząca, lepiej będzie zaimplementować klasę.

## 🔧 Jak to działa?
1️⃣**Python wykrywa**, że funkcja wewnętrzna używa zmiennych z funkcji zewnętrznej.  
2️⃣ Dla tych zmiennych tworzone są **cell objects** (specjalne kontenery).  
3️⃣ Funkcja wewnętrzna dostaje **referencje do tych cellów** (a nie same wartości).  
4️⃣ Gdy funkcja zewnętrzna skończy działać, cell objects **nie znikają**, bo trzyma je funkcja wewnętrzna.  
5️⃣ Przy każdym wywołaniu funkcja wewnętrzna **czyta lub zmienia** wartości z cell objects → i to właśnie jest closure.

## 🧪 Przykład

```python
def make_counter():
    count = 0       # ← zmienna, która trafi do closure (plecaka)

    def inner():
        nonlocal count   # ← modyfikujemy zmienną z closure
        count += 1
        return count

    return inner         # ← zwracamy funkcję z plecakiem

counter = make_counter()

print(counter())  # 1
print(counter())  # 2
print(counter())  # 3

```

---

## 🧩 Mnemotechniki

### 🅰 Akronim

**Akronim:** C.L.O.S.E.

**Rozwinięcie:**

- C - Capute variable 
	- Funkcja zewnętrzna łapie zmienne z funkcji zewnętrznej.
- L - life longer.
	- Te zmienne żyją dłużej niż funkcja, która je stworzyła.
- O - outer scope stored.
	- Python pakuje potrzebne zmienne, specjalne obiekty, cel → plecak.
- S - Stored in function
	- Funkcja wewnętrzna przechowuje **referencje** do tych cellów w `__closure__`.
- E - Execute with memory
	- Przy każdym wywołaniu funkcja korzysta z wartości, które pamięta.

---

### 🔄 Tłumaczenie jako analogia

**Analogia:**
**Closure to taki plecak, który zabierasz ze sobą w podróż jako funkcja.**  
W tym plecaku znajdują się wszystkie potrzebne rzeczy (zmienne), które spakowałeś w domu — czyli w _outer scope_.

Nawet jeśli dom już dawno zniknął z mapy (funkcja zewnętrzna skończyła działanie),  
**plecak wciąż istnieje i podróżuje razem z tobą**,  
a ty możesz z niego korzystać w dowolnym momencie.

Jeśli w plecaku coś zmienisz (`nonlocal`), zmiana zostaje —  
bo to cały czas _ten sam plecak_, a nie kopia.

---

### 🗃 Keyword Connections (powiązania)

- [[nonlocal]]
- [[cell_contents]]
- [[enclosing scope]]
- [[free variables]]
- [[cell]]
- [[cell holding]]
- [[LOAD_DEREF]]

---

### 🖼 Rysunek / schemat / diagram ASCII

![[Pasted image 20251201220606.png]]
---

## ✨ Metoda Feynmana (1–2 zdania)

Closure to taki plecak, który zabierasz ze sobą, a w nim masz zabawki (zmienne) spakowane w domu. Nawet jeśli dom już nie istnieje, wciąż masz dostęp do wszystkiego, co spakowałeś.

---

## ⚠ Typowe błędne wyobrażenie

Wielu początkujących programistów uważa, że closure powstaje tylko w funkcjach wyższego rzędu, czyli wtedy, gdy funkcja zwraca inną funkcję. W rzeczywistości closure tworzy się zawsze wtedy, gdy funkcja wewnętrzna korzysta ze zmiennych zewnętrznych i zostaje wyniesiona poza swój pierwotny zakres.
return jest tylko jednym z możliwych sposobów opuszczenia zakresu — nie jedynym.

### 🔹 1. **Przypisanie do zmiennej globalnej**

`global_ref = inner`

### 🔹 2. **Włożenie funkcji do listy / dict / obiektu**

`storage.append(inner)`

### 🔹 3. **Przekazanie funkcji jako argument dalej**

`register_callback(inner)`

### 🔹 4. **Zwrócenie funkcji przez inną funkcję pośrednią**

(nie musi być bezpośrednio `return inner`)

### 🔹 5. **Zapisanie funkcji jako atrybut obiektu**

`obj.handler = inner`

### 🔹 6. **Ustawienie jej w module (np. przez przypisanie)**

`module.fn = inner`


---

## 📌 Kontrast (X vs Y)

| Cecha                     | Clousure                                                      | Koncepcja przeciwna                                      |
| ------------------------- | ------------------------------------------------------------- | -------------------------------------------------------- |
| Przechowywanie zmiennych  | Funkcja pamięta zmienne z outer scope                         | Funkcja nie pamięta nic poza lokalnym/globalnym zakresem |
| Czas życia zmiennych.     | Zmienne żyją dłużej niż funkcja, która je stworzyła           | Zmienne znikają po zakończeniu zakresu                   |
| Mechanizm działania.      | Używa cell objects i referencji (LOAD_DEREF)                  | Korzysta tylko z lokalnych i globalnych zmiennych        |
| Modyfikacja zmiennych.    | Możliwa dzięki nonlocal                                       | Zmiennych spoza zakresu nie da się modyfikować           |
| Izolacja instancji        | Każda funkcja ma swój własny plecak                           | Wszystkie funkcje używają tego samego globalnego stanu   |
| Warunek powstania.        | Wystarczy, że funkcja opuści zakres z użyciem outer-variables | Funkcja żyje wyłącznie w swoim zakresie, nic nie wynosi  |
| Pamięć między wywołaniami | Funkcja zachowuje stan                                        | Funkcja startuje od zera przy każdym wywołaniu           |

---

## 🗂 Fiszki (SRS) #flashcards 

Co przechowuje closure — wartości czy referencje?
?
Closure przechowuje referencje do cell objects, nie skopiowane wartości.
<!--SR:!2025-12-13,5,230-->

pytanie
Czy closure powstaje wyłącznie wtedy, gdy funkcja zwraca inną funkcję?
?
Nie, closure powstaje zawsze, gdy funkcja wewnętrzna opuszcza swój zakres i używa zmiennych z outer scope.
<!--SR:!2025-12-19,11,270-->

pytanie
Czy closure może działać na zmiennych globalnych?
?
Nie, zmienne globalne nie tworzą closure.
<!--SR:!2025-12-22,16,290-->

pytanie
Czy każda funkcja wewnętrzna tworzy closure?
?
Nie, tylko taka, która korzysta z zmiennych z zewnętrznego scope.
<!--SR:!2025-12-21,15,290-->

pytanie
Czy różne wywołania funkcji zewnętrznej współdzielą ten sam closure?
?
Nie, każde wywołanie tworzy własny, niezależny plecak (closure).
<!--SR:!2025-12-15,10,270-->

pytanie
Czy `nonlocal` jest potrzebne do odczytu zmiennej z closure?
?
Nie, jest potrzebne tylko do jej modyfikacji.
<!--SR:!2025-12-22,16,290-->

pytanie
Jak closure zachowuje zmienne po zakończeniu działania funkcji zewnętrznej?
?
Przechowuje je w cell objects, które żyją dalej dzięki referencjom funkcji wewnętrznej.
<!--SR:!2025-12-11,2,210-->

pytanie
Jaki jest warunek powstania closure?
?
Funkcja wewnętrzna musi używać zmiennych z outer scope i przetrwać dłużej niż ten scope.
<!--SR:!2025-12-18,10,270-->

---

## 🔗 Powiązane notatki