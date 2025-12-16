
<!--SR:!2025-11-27,1,226!2000-01-01,1,250--># Dynamicznie typowany język
---
aliases: ["dynamic typing", "dynamiczne typowanie", "dynamically typed language"]

tags: [#python, #python/theory, #python/typing]

sr-due: true
graph: false

---

## 🧠 Co to jest?
**Dynamicznie typowany język** to język programowania, w którym **typ zmiennej jest ustalany podczas działania programu (runtime)**, a nie na etapie kompilacji lub przed uruchomieniem. Oznacza to, że ta sama zmienna może zmieniać typ w trakcie działania programu w zależności od przypisanej wartości.

## 🔧 Jak to działa?
W językach dynamicznie typowanych interpreter sprawdza typ wartości dopiero w momencie jej użycia, a nie wcześniej. Oznacza to, że:

1. Podczas przypisania zmiennej wartości interpreter „przypina” do niej typ wynikający z tej wartości.
2. Jeśli później przypiszesz do tej samej zmiennej inną wartość, interpreter ustali nowy typ — wcześniejszy typ znika.
3. Błędy typów wykrywane są dopiero podczas wykonywania kodu (runtime), nie przed uruchomieniem.
4. To runtime decyduje, czy operacje są dozwolone (np. dodawanie liczb vs. konkatenacja stringów).


## 🧪 Przykład

```{{python}}
x = 10          # x ma teraz typ int
print(type(x))  # <class 'int'>

x = "tekst"     # teraz x ma typ str
print(type(x))  # <class 'str'>

x = [1, 2, 3]   # teraz x ma typ list
print(type(x))  # <class 'list'>
```

---

## 🧩 Mnemotechniki

### 🅰 Akronim

**Akronim:** R.A.D.A.R

**Rozwinięcie:**

- R — Runtime
	Typ ustalany dopiero podczas działania programu. nie wcześniej
- A — Assign -> type from value
    Typ zmiennej wynika bezpośrednio z przypisanej wartości
- D — Dynamic changes
    Typ może się zmieniać wielokrotnie, zależnie od kolejnych przypisań
- A — Automatic checks
	Interpreter automatycznie **sprawdza typy w czasie wykonania** (runtime checks).
- R — Runtime errors
	Błędy typów pojawiają się dopiero podczas działania (np. TypeError)

---

### 🔄 Tłumaczenie jako analogia

**Analogia:** Dynamiczne typowanie = Pudełko, do którego wkładasz różne rzeczy
Typ pudełka nie jest określony na stałe.
On zależy od tego, co akurat do niego włożysz. 
Możesz mieć pudełko na kredki w tedy typ jest równy kredce ale możesz w każdej chwili wysypać z niego kredki i włożyć tam np samochody wtedy typ automatycznie zmieni się na samochód 

---

### 🗃 Keyword Connections (powiązania)

- [[typowanie]]
- [[statyczne typowanie]]
- [[runtime]]
- [[interpreter]]
- [[duck typing]]
- [[TypeError]]
- [[system typów]]
- [[str]]
- [[int]]
- [[bolean]]
- [[list]]
- [[dict]]
- [[set]]
- [[None]]
- [[float]]
---

### 🖼 Rysunek / schemat / diagram ASCII
![[Pasted image 20251126085926.png]]

```
[Input] → [Processing] → [Output]
```

---

## ✨ Metoda Feynmana (1–2 zdania)
W Pythonie zmienna jest jak pudełko, które samo dopasowuje etykietę do tego, co do niego włożysz.

Dziś możesz włożyć skarpety (liczbę), jutro zabawkę (string), a Python automatycznie zmieni etykietę pudełka na „skarpety” lub „zabawka”.

**Typ nie jest ustalany wcześniej — powstaje dopiero wtedy, gdy coś włożysz.**

---

## ⚠ Typowe błędne wyobrażenie
Wiele osób myśli, że:

> **„Dynamiczne typowanie oznacza, że Python nie ma typów.”**

To nieprawda.

✔️ **Python ma typy — i to bardzo precyzyjne.**  
❌ To zmienne nie mają „przypisanego na stałe” typu.  
✔️ **Typ należy do wartości, nie do nazwy zmiennej.**

To znaczy, że `x` nie jest „zmienną typu str” —  
**x to tylko etykieta, która chwilowo wskazuje na wartość o określonym typie.**

W dynamicznym typowaniu zmienia się **wiązanie etykieta → obiekt**, a nie typ samego pudełka.

---

## 📌 Kontrast (X vs Y)

| Cecha                         | Dynamicznie typowany język                                   | Statyczne typowany język                                                        |
| ----------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------------------------- |
| Typ                           | Typ należy do wartości, a nie do zmiennej                    | Typ jest przypisany do zmiennej i jest znany już przy deklaracji                |
| Ustalanie typu                | Podczas runtime (w momencie przypisania wartości)            | Podczas kompilacji lub przy deklaracji                                          |
| Zmienna może zmienić swój typ | ✅                                                            | ❌                                                                               |
| Język                         | Python, JavaScript, Ruby                                     | C, C++, Java, Rust                                                              |
| Analogia – pudełko            | Pudełko, które zmienia etykietę zależnie od tego, co włożysz | Pudełko z etykietą przyklejoną na stałe — musisz wkładać tylko rzeczy tego typu |


---

## 🗂 Fiszki (SRS) #flashcards

Co to jest Dynamicznie typowany język?
?
Język, w którym **typ należy do wartości, a nie do zmiennej**, i jest ustalany **w czasie działania programu (runtime)**.
<!--SR:!2026-01-20,38,292-->


Jak działa Dynamicznie typowany język?
?
Przypisujesz wartość → język automatycznie określa jej typ → zmienna wskazuje na tę wartość.
Zmienna może później wskazać na wartość innego typu.
<!--SR:!2026-01-01,19,270-->
