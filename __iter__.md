---
sr-due: 2025-12-25
sr-interval: 11
sr-ease: 270
---

# Iteratory, obiekty iterowalne i generatory

aliases: []  
tags: [theory, cs, programming]  
sr-due: true
graph: false

#review 

---

## 🧠 Co to jest?
Iterator to **obiekt**, który:
- został utworzony przy użyciu funkcji `iter()`
- **potrafi zwracać kolejne elementy** sekwencji
- posiada **metodę `__next__()`**  
    (wywoływaną przez funkcję `next()`)

## 🔧 Jak to działa?
1. Wywołujesz `iter(coś)`
2. Dostajesz iterator — obiekt ze stanem wewnętrznym.
3. Każde `next(iterator)` daje:
    - **kolejny element**
    - aż do **StopIteration**


⚠️ Ważne:

- **iterator pamięta pozycję**  
    (nie zaczyna od nowa!)
    
- jeśli raz go przejdziemy → koniec

## 🧪 Przykład

```python
shoping_tuple = ("milk", "water", "apple")
shoping_iter = iter(shoping_tuple)
print(next(shoping_iter))
print(next(shoping_iter))
print(next(shoping_iter))
```

---

## 🧩 Mnemotechniki

### 🅰 Akronim

#### **I — Item by item**

> Dostarcza **kolejne elementy**, jeden po drugim.

🧠 Zapamiętaj:  
➡️ „Przewracam kartki po jednej”.

---

#### **T — Tracks the state**

> **Pamięta pozycję**, gdzie ostatnio był.

🧠 Zapamiętaj:  
➡️ „Zakładka w książce”.

---

#### **E — Ends with StopIteration**

> Gdy skończą się elementy → **StopIteration**.

🧠 Zapamiętaj:  
➡️ „Koniec książki = brak stron”.

---

#### **R — Returned by iter()**

> Tworzony przez **`iter(obj)`**.

🧠 Zapamiętaj:  
➡️ „Z książki robię zakładkę”.

---

### 🔄 Tłumaczenie jako analogia

Wyobraź sobie, że masz **program do oglądania shortów na YouTubie**.

- Otwierasz playlistę → **to jest iterowalne**
    
- Tworzysz „asystenta głosowego” → **to jest iterator**
    

Asystent ma jedną magiczną komendę:

👉 **„NEXT!”**

Za każdym razem, kiedy powiesz „NEXT!”:

- przełącza cię do **kolejnego shortsa**
    
- **pamięta swoją aktualną pozycję**
    
- robi to aż skończy się playlista
    

Gdy obejrzysz ostatni film i powiesz „NEXT!” jeszcze raz:

👉 usłyszysz odpowiedź **„StopIteration – koniec shortów. Wracaj do nauki :D”**

---

### 🗃 Keyword Connections (powiązania)

- [[StopIteration]]
    
- [[iter()]]
    
- [[next()]]
	 
-  [[__next__]]

---

### 🖼 Rysunek / schemat / diagram ASCII

![[Pasted image 20251210211230.png]]

---

## ✨ Metoda Feynmana (1–2 zdania)
Obiekt iterowalny to jak **lista zakupów**. Wywołujesz `iter`, dostajesz narzędzie ze słowem-komendą `next`, i idziesz po sklepie wrzucając kolejne rzeczy do koszyka. Gdy krzyczysz „next” po ostatnim produkcie — asystent odpowiada **StopIteration**, bo zakupy są skończone.

---

## ⚠ Typowe błędne wyobrażenie
moim typowym błędnym założeniem była myśl, że można po iteratorze przechodzić wiele razy, tak jak po obiekcie literowalnym. 

W rzeczywistości po iteratorze możemy przejść tylko raz, ponieważ, zapamiętuje, w którym miejscu się znajduje. 

Tak naprawdę, jeżeli mamy obiekt literowalny i tworzymy przez niego pętlę for, to zawsze iterujemy przez iterator, który jest dla niego stworzony, a nie przez sam obiekt. 

Kolejnym moim błędnym założeniem było myślenie, że pętla for wymaga metody iter. 
Gdzie w rzeczywistości, jeżeli nie posiada metody `iter`, użyje po prostu `__getitem__()`. 

Obiekt może być jednocześnie iteratorem i iterowalny, jeśli `__iter__` zwraca `self`. 

---

## 📌 Kontrast (X vs Y)
| Cecha                       | Iterator            | Iterowalny                            |
| --------------------------- | ------------------- | ------------------------------------- |
| Posiada __next__            | ✅                   | ❌                                     |
| Posiada __iter__            | ✅ (zwraca self)     | ✅ (zwraca nowy iterator)              |
| Pamięta stan (pozycję)      | ✅                   | ❌                                     |
| Można użyć wielokrotnie     | ❌                   | ✅                                     |
| Zużywa się podczas iteracji | ✅                   | ❌                                     |
| Przechodzi elementy         | ✅                   | ❌                                     |
| Użycie w pętli for          | Bezpośrednio działa | Tworzy się z niego iterator           |
| Tworzy nowe iteratory       | ❌                   | ✅                                     |
| Reset po iteracji           | ❌                   | ✅ (przez stworzenie nowego iteratora) |
| Relacja do next()           | Obsługuje next()    | Deleguje do iteratora                 |

---

## 🗂 Fiszki (SRS) #flashcards 

Czy lista jest iteratorem?
?
Lista jest iterowalna, ale nie jest iteratorem; iterator dostajemy dopiero przez iter(lista).
<!--SR:!2025-12-26,12,270-->

---

Czy mogę użyć iteratora wiele razy w pętli for?
?
Nie, iterator zużywa się; po pierwszym przejściu jest wyczerpany.
<!--SR:!2025-12-30,15,290-->

---

Czy pętla for iteruje po kolekcji?
?
Nie, pętla for zawsze działa na iteratorze stworzonym z kolekcji.
<!--SR:!2025-12-16,3,250-->

---

Czy obiekt iterowalny musi mieć metodę **next**?
?
Nie, obiekt iterowalny musi mieć **iter**, **next** znajduje się w iteratorze.
<!--SR:!2025-12-17,3,230-->

---

Czy każdy obiekt z **next** jest iteratorem?
?
Nie, prawdziwy iterator musi mieć zarówno **next** jak i **iter** zwracającą self.
<!--SR:!2025-12-18,3,210-->

---

Czy generator jest iteratorem?
?
Generator jest iteratorem i iterowalny, ponieważ iter(generator) zwraca jego samego.
<!--SR:!2025-12-29,14,290-->

---

Czy obiekt może być jednocześnie iteratorem i iterowalnym?
?
Tak, jeśli **iter** zwraca self, ale wtedy można przejść po nim tylko raz.
<!--SR:!2025-12-26,12,270-->

---

Czy pętla for zawsze wymaga **iter**?
?
Nie zawsze, jeśli obiekt nie ma **iter**, Python użyje **getitem** z indeksami aż do IndexError.
<!--SR:!2025-12-16,2,210-->

---

Czy iterowalne i iterator to to samo?
?
Nie, iterowalne tworzy nowy iterator, iterator zwraca kolejne elementy przez next.
<!--SR:!2025-12-26,12,270-->

---

Czy StopIteration oznacza, że kolekcja się skończyła?
?
Nie, StopIteration oznacza, że skończył się iterator, kolekcja może istnieć dalej i można stworzyć nowy iterator.
<!--SR:!2025-12-17,3,230-->

---

## 🔗 Powiązane notatki

- [Iteratory](https://www.w3schools.com/python/python_iterators.asp)
    
- [Generatory, yield](https://realpython.com/introduction-to-python-generators/)
    
- [Różnice pomiędzy iteratorami a generatorami](https://www.geeksforgeeks.org/difference-between-iterator-vs-generator/)