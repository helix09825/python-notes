---
sr-due: 2025-12-15
sr-interval: 4
sr-ease: 270
---

aliases: []  
tags: [theory, cs, programming]  
sr-due: true
graph: false

#review 

---

## 🧠 Co to jest?

Generator to **specjalny rodzaj iteratora** tworzony przez funkcję generatorową (czyli funkcję zawierającą słowo kluczowe `yield`) albo przez _generator comprehension_ w nawiasach okrągłych.

Po wywołaniu funkcji generatorowej **nie wykonuje się od razu cała funkcja** – zamiast tego dostajesz obiekt generatora. Taki obiekt:

- **zapamiętuje swój stan** (miejsce, w którym przerwał),
    
- przy każdym `next(...)` albo kolejnym obrocie pętli `for` **wznawia działanie od tego miejsca**,
    
- jest jednorazowy – **po wyczerpaniu nie da się go „zresetować”**, trzeba utworzyć nowy generator, ponownie wywołując funkcję generatorową.
    

Generator jest zarówno **iterowalny, jak i iteratorem** – `iter(generator)` zwraca jego samego, a do przejścia po nim używamy `for` albo `next(...)`.
## 🔧 Jak to działa?

1. **Definicja**  
    Piszesz funkcję z `yield` → Python traktuje ją jako _funkcję generatorową_, a nie zwykłą funkcję.
    
2. **Wywołanie funkcji**  
    Gdy wywołasz taką funkcję (`g = my_gen()`), **ciało funkcji się nie wykonuje**.  
    Zamiast tego dostajesz **obiekt generatora**.
    
3. **Pierwsze `next()` / start pętli `for`**  
    Python zaczyna wykonywać funkcję **od początku**, aż do pierwszego `yield`.  
    W momencie `yield`:
    
    - zwraca wartość na zewnątrz,
        
    - **pauzuje** funkcję w tym miejscu.
        
4. **Zapamiętanie stanu**  
    Generator **zapamiętuje cały swój stan**:
    
    - aktualną linię w kodzie (gdzie przerwał),
        
    - wartości zmiennych lokalnych,
        
    - kontekst wykonywania.
        
5. **Kolejne `next()` / kolejne obroty pętli `for`**  
    Przy następnym `next(g)`:
    
    - funkcja **wznawia działanie tuż za `yield`**,
        
    - biegnie dalej, aż do kolejnego `yield`,
        
    - znowu zwraca wartość i pauzuje.
        
6. **Zakończenie generatora**  
    Gdy funkcja:
    
    - dojdzie do `return`, albo
        
    - do końca bloku kodu,  
        generator **się wyczerpuje** i przy następnym `next()` rzuca `StopIteration`.
        
7. **Jednorazowość**  
    Gdy generator się wyczerpie:
    
    - pętla `for` się kończy,
        
    - kolejne `next()` już nic nie „resetuje” – trzeba stworzyć **nowy generator**, znowu wywołując funkcję.
        
8. **`for` pod spodem**  
    Pętla `for` sama:
    
    - wywołuje `iter(generator)`,
        
    - w kółko woła `next(...)`,
        
    - kończy, gdy dostanie `StopIteration`.
        

Czyli w skrócie: _generator to funkcja, która działa „na raty” – `yield` zwraca wartość i pauzuje, `next`/`for` ją wznawia, aż do wyczerpania._

## 🧪 Przykład

```python
def count_up_to(n):
    print("Start generatora")
    current = 1
    while current <= n:
        print(f"Przed yield: {current}")
        yield current  # zwracamy wartość i pauzujemy
        print(f"Po yield (wznowione): {current}")
        current += 1

g = count_up_to(3)

print(next(g))  # odpala funkcję do pierwszego yield → 1
print(next(g))  # wznawia od miejsca po yield → 2
print(next(g))  # znowu wznowienie → 3

# kolejne next(g) rzuci StopIteration

```

1. Czytanie ogromnych plików linijka po linijce
2. Streamowanie odpowiedzi HTTP.
3. Przetwarzanie dużych CSV, dużych danych z bazy w porcjach.
4. Pipeline przetwarzania danych, logi ETL.  Data Engineering.

---

## 🧩 Mnemotechniki

### 🅰 Akronim

- **G – Generuje stopniowo**  
    Zwraca kolejne wartości **na żądanie**, a nie wszystko naraz (lazy).
    
- **E – Eksportuje i zapamiętuje stan**  
    Przy `yield` **oddaje wartość na zewnątrz i pauzuje**, zachowując pozycję i lokalne zmienne.
    
- **N – Nieodnawialny**  
    Po wyczerpaniu generator jest **jednorazowy** – nie resetuje się, trzeba stworzyć nowy.
---

### 🔄 Tłumaczenie jako analogia

**Analogia:**
#### Jak książka = generator?

1. **Czytasz stronę po stronie (lazy, nie wszystko naraz)**  
    Nie wciągasz całej książki do głowy w jednej sekundzie.  
    Czytasz **jedną stronę**, odkładasz książkę → to jak jedno `next()`.
    
2. **Zakładka = zapamiętany stan generatora**  
    Gdy kończysz czytać:
    
    - wkładasz zakładkę w miejsce, gdzie skończyłeś,
        
    - książka „pamięta”, gdzie przerwałeś.
        
    
    Generator robi to samo: przy `yield` **pauzuje** i pamięta:
    
    - w którym „miejscu w kodzie” skończył,
        
    - jakie miały wartości zmienne.
        
3. **Kolejny raz = wznawiasz od zakładki**  
    Następnego dnia:
    
    - otwierasz książkę **dokładnie w tym miejscu**, gdzie była zakładka,
        
    - czytasz dalej kolejną stronę → kolejne `next()`.
        
4. **Koniec książki = StopIteration**  
    Gdy dojdziesz do końca:
    
    - książka się kończy, nie ma więcej stron,
        
    - kolejne próby „czytania” już nic nowego nie dadzą.  
        To jak wyczerpany generator – przy kolejnym `next()` dostajesz `StopIteration`.
        
5. **Chcesz czytać od początku?**  
    Musisz:
    
    - zamknąć książkę,
        
    - otworzyć ją znowu od pierwszej strony.
        
    
    W Pythonie: tworzysz **nowy generator**, znowu wywołując funkcję generatorową.
---

### 🗃 Keyword Connections (powiązania)

- [[yield]]
    
- [[__iter__]]
    
- [[__next__]]
    

---

### 🖼 Rysunek / schemat / diagram ASCII

![[Pasted image 20251211195422.png]]

---

## ✨ Metoda Feynmana (1–2 zdania)

Wyobraź sobie magiczną książkę: każda strona pojawia się tylko raz, a po jej przeczytaniu zostawiasz w środku złotą zakładkę `yield`, dzięki której przy kolejnym otwarciu wracasz dokładnie w to miejsce i dostajesz następne zaklęcie. Gdy skończą się strony, dostajesz `StopIteration` – koniec magii, żeby czytać dalej musisz stworzyć nową książkę, czyli nowy **generator** w Pythonie.

---

## ⚠ Typowe błędne wyobrażenie

Okej, więc moimi błędnymi założeniami było to, że przy użyciu pętli `for` możemy po prostu wyrzucić `StopIteration`. W rzeczywistości, wyjątek ten jest generowany dopiero w metodzie `next`, a pętla `for` sama go obsługuje, dzięki czemu nie napotkamy żadnego błędu. Kolejną kwestią jest to, że generator tworzy iterator; generator jest zatem obiektem, który działa jako iterator, tworząc obiekt generatora

---

## 📌 Kontrast (X vs Y)

| Cecha                                                                | Generator | Lista (tworzona w całości, np. list comprehension) |
| -------------------------------------------------------------------- | --------- | -------------------------------------------------- |
| Leniwe obliczanie wartości (tylko gdy iterujemy)                     | ✅         | ❌                                                  |
| Oblicza wszystkie wartości od razu w momencie tworzenia obiektu      | ❌         | ✅                                                  |
| Zużywa mało pamięci dla bardzo dużych sekwencji                      | ✅         | ❌                                                  |
| Przechowuje wszystkie wygenerowane wartości w pamięci jednocześnie   | ❌         | ✅                                                  |
| Jest jednorazowy – po wyczerpaniu nie można po nim przejść drugi raz | ✅         | ❌                                                  |
| Można wielokrotnie iterować po tym samym obiekcie                    | ❌         | ✅                                                  |
| Zwracany przez funkcję z `yield` / generator comprehension           | ✅         | ❌                                                  |
| Zwracany przez zwykłą funkcję z `return` / list comprehension        | ❌         | ✅                                                  |

---

## 🗂 Fiszki (SRS) #flashcards 

Czym generator różni się od zwykłej funkcji z `return`?  
?  
Zwykła funkcja z `return` zwraca wartość i kończy działanie, tracąc cały stan. Funkcja generatorowa z `yield` zwraca wartość, ale tylko pauzuje — zachowuje swój stan i wznawia działanie przy kolejnym `next` lub obrocie pętli `for`.

---

Czy generator tworzy osobny obiekt iteratora?  
?  
Nie. Obiekt generatora sam jest iteratorem i jednocześnie jest iterowalny — ma `__next__` i `__iter__`, a `iter(generator)` zwraca jego samego.

---

Co zrobi druga pętla `for` na już wyczerpanym generatorze?  
?  
Druga pętla `for` nic nie wypisze, bo generator jest wyczerpany. Pętla `for` wewnętrznie łapie wyjątek `StopIteration` i po prostu kończy iterację, bez błędu na ekranie.

---

Czy pętla `for` może wyrzucić `StopIteration` na zewnątrz?  
?  
Nie. `StopIteration` rzuca sam generator (iterator) w `__next__`, a pętla `for` ten wyjątek łapie wewnętrznie i kończy działanie bez pokazywania błędu.

---

Jak przejść drugi raz po tych samych danych z funkcji generatorowej?  
?  
Nie da się „zresetować” istniejącego generatora. Trzeba ponownie wywołać funkcję generatorową, aby otrzymać nowy obiekt generatora i dopiero po nim iterować.

---

Jaka jest główna różnica w pamięci między list comprehension a generator comprehension?  
?  
List comprehension tworzy od razu całą listę wszystkich wyników i trzyma je w pamięci. Generator comprehension tworzy wartości leniwie, tylko na żądanie podczas iteracji, więc nie trzyma wszystkich rezultatów naraz w pamięci.

---

Kiedy obliczane są wartości w generatorze (np. w generator comprehension)?  
?  
W generatorze wartości są obliczane leniwie — dopiero w momencie, gdy rzeczywiście po nie sięgamy (`next`, `for`, `list(g)`), a nie w chwili tworzenia generatora.

---

Czy kod wewnątrz generatora wykona się, jeśli nigdy po nim nie ziterujemy?  
?  
Nie. Jeśli nie użyjemy `next`, `for`, `list(g)` ani innej formy iteracji, kod wewnątrz generatora (np. `expensive(x)`) w ogóle się nie wykona.

---

Co dokładnie sygnalizuje wyjątek `StopIteration` w kontekście generatora?  
?  
`StopIteration` oznacza, że generator nie ma już żadnych wartości do zwrócenia. Generator jest wyczerpany i dalsza iteracja nie zwróci kolejnych elementów.

---

Czy można ponownie iterować po tym samym obiekcie generatora po jego wyczerpaniu?  
?  
Nie. Po rzuceniu `StopIteration` generator jest wyczerpany i nie da się go użyć ponownie. Kolejne próby iteracji nic nie zwrócą — trzeba stworzyć nowy generator.

---

Czy każde iterowalne w Pythonie jest generatorem?  
?  
Nie. Iterowalne to każdy obiekt, który potrafi zwrócić iterator (ma `__iter__`), np. lista, string, dict. Generator jest konkretnym rodzajem iteratora tworzonym przez funkcję generatorową lub generator comprehension.

---

Co robi `yield` w funkcji generatorowej na poziomie zachowania?  
?  
`yield` zwraca wartość na zewnątrz i pauzuje wykonanie funkcji w tym miejscu, zachowując stan lokalnych zmiennych. Przy kolejnym `next` lub obrocie pętli `for` działanie wznawiane jest dokładnie od miejsca tuż za `yield`.

---

## 🔗 Powiązane notatki