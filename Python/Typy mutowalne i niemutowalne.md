
aliases: []  
tags: [theory, cs, programming]  
sr-due: true
graph: false

---

## 🧠 Co to jest?
Niektóre obiekty w Pythonie umożliwiają nam zmianę ich stanu wewnętrznego. Nazywmy je _obiektami mutowalnymi_. Jeśli nie możemy zmienić stanu wewnętrznego danego obiektu – jest on _niemutowalny_. W tej lekcji dowiemy się jak działają, jak ich używać – i dlaczego.

## Obiekty niemutowalne
Obiekt niemutowalny to taki, którego zachowania nie możemy zmienić przez cały czas jego istnienia. W Pythonie są to takie obiekty o rodzajach `int`, `float`, `string`, `boolean`, and `tuple`.

Krotki są niemutowalne ale wciąż mozęmy zmieniać mutowalne objekty zandujące się wewnąć takich zmienncyh 

## 🔧 Jak to działa?
Zmiana obiekty niemutowalnego przypisuje po prostu nowy objekt w praktyce to oznacza że wartość posiada nowy id. W krotkach mamy sytuacje w której samej krotki nie możemy zmienić ale jej wartości jeśli są mutowalne już tak

## 🧪 Przykład

```{{python}}
age = 18	
print(id(age)) 		# 9789536

age += 1	
print(id(age)) 		# 9789568

my_bag = (["phone charger", "laptop charger"], "napkins")

# Not allowed due to an error — tuple is an immutable object
my_bag[0] = ["phone charger", "laptop charger", "tablet charger"]

# Allowed because we change mutable objects inside
my_bag[0].append("tablet charger")


```

---

## 🧩 Mnemotechniki

### 🅰 Akronim

**Akronim:** IF B STuFf
Czytaj: _“if stuff”_ — pamiętasz, że **IF** to warunek = stałe / niezmienne.

**Rozwinięcie:**

- I — int
    
- F — float
    
- B — bool
	
- S — str
    
- Tu — tuple
    
-  Ff— frozenset

**Akronim:** LDS - Łatwo Da Się zmienić

**Rozwinięcie:**

- L — list
    
- D — dict
    
- S — set


---

### 🔄 Tłumaczenie jako analogia

**Analogia:**
W Pythonie wszystkie typy danych to jak skrzynki, do których wkładamy wartości.

#### **🔓 Mutowalne = skrzynki otwarte**

Możesz do nich **dokładać, wyjmować i zmieniać zawartość**, bez wymiany samej skrzynki.

To są:

- **list** – otwarta skrzynka z uporządkowanymi elementami
    
- **dict** – otwarta skrzynka z przegródkami na klucze
    
- **set** – otwarta skrzynka, ale bez duplikatów
    

👉 _Możesz grzebać w środku, ale skrzynka zostaje ta sama._

#### **🔒 Niemutowalne = skrzynki zamknięte**

Tych skrzynek **nie da się otworzyć**. Jeśli chcesz zmienić zawartość, musisz **wymienić całą skrzynkę** na nową.

To są:

- **int**
    
- **float**
    
- **bool**
    
- **str**
    
- **tuple**
    
- **frozenset**
    

#### 👉 _Nie zmieniasz środka — wymieniasz całą skrzynkę._
---

### 🗃 Keyword Connections (powiązania)

- [[mutowalne]]
    
- [[niemutowalne]]
    
- [[python-typing]]
    
- [[id]]

---

### 🖼 Rysunek / schemat / diagram ASCII

![[Pasted image 20251126222310.png]]
---

## ✨ Metoda Feynmana (1–2 zdania)
Wyobraź sobie, że typy mutowalne to **skrzynki przykręcone do podłogi** — możesz dowolnie wymieniać ich zawartość (list, dict, set), ale sama skrzynka i jej „ID” pozostaje na miejscu.  
Typy niemutowalne to **skrzynki zamknięte i nieprzytwierdzone** — żeby zmienić ich zawartość, musisz wynieść starą skrzynkę i wnieść nową z nową etykietą (int, float, bool, str, tuple, frozenset).

---

## ⚠ Typowe błędne wyobrażenie
Wiele osób myśli, że przy typach niemutowalnych nie można zmienić zmiennej.
To nieprawda.

Możemy zmieniać wartość zmiennej, możemy wykonywać na niej operacje, możemy „modyfikować” jej zawartość — ale nie modyfikujemy samego obiektu, tylko:

👉 zmienna zaczyna wskazywać na nowy obiekt o nowym id()

---

## 📌 Kontrast (X vs Y)

| Typ       | Mutowalne | Niemutowalne |
| --------- | --------- | ------------ |
| int       | ❌         | ✅            |
| float     | ❌         | ✅            |
| bool      | ❌         | ✅            |
| str       | ❌         | ✅            |
| tuple     | ❌         | ✅            |
| frozenset | ❌         | ✅            |
| list      | ✅         | ❌            |
| dict      | ✅         | ❌            |
| set       | ✅         | ❌            |

---

## 🗂 Fiszki (SRS) #flashcards 

Wymień niemutowalne typy danych
?
int, float, bool, string, tuple, frozenset
<!--SR:!2025-12-01,4,275-->

Wymień mutowalne typy danych
?
list, dict, set
<!--SR:!2025-12-01,4,275-->

Co znaczy że typ jest mutowalny?
?
Można zmieniać jego zawartość _bez tworzenia nowego obiektu_, ID w pamięci pozostaje to samo.
<!--SR:!2025-12-01,4,275-->

Co znaczy że typ jest niemutowalny?
?
Po każdej próbie zmiany powstaje _nowy obiekt_ — a więc obiekt dostaje nowe ID.
<!--SR:!2025-12-01,4,275-->

Jak sprawdzić, czy obiekt jest mutowalny w praktyce?
?
Zmienić jego wartość i porównać `id()` przed i po.
<!--SR:!2025-12-16,15,295-->

---

## 🔗 Powiązane notatki