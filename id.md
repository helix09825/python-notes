
aliases: []  
tags: [theory, cs, programming]  
sr-due: true
graph: false

---

## 🧠 Co to jest?
`id()` w Pythonie **zwraca unikalny identyfikator obiektu w pamięci** – czyli _adres_, pod którym ten obiekt aktualnie istnieje.

`id(x)` → zwraca liczbę całkowitą, która reprezentuje _miejsce w pamięci_, gdzie przechowywany jest obiekt `x`.


## 🔧 Jak to działa?
Zawsze gdy tworzysz nowy objekt Python znajduje wolny kawałek pamięci, wkłada tam objekt, zapamiętuje gdzie on się znajduje

To miejsce (adres) to właśnie to, co zwraca id(obj)

## 🧪 Przykład

```{{python}}
x = 10

id(x) # 7482123312 
```

---

## 🧩 Mnemotechniki

### 🅰 Akronim

**Akronim:** ID = "Inne Domy"
**Obiekt to dom, a ID to jego adres.**

- zmienna to osoba z karteczką z adresem
    
- mutowalne = dom stoi dalej w tym samym miejscu
    
- niemutowalne = stary dom burzą, budują nowy → inny adres
    


---

### 🔄 Tłumaczenie jako analogia

**Analogia:** Twój adres zamieszkania to twoje obecne ID za każdym razem gdy ktoś chce Cię znaleźć odwoła się do tego ID i już wie gdzie jesteś. Tak samo działa python, sprawdza ID objektu i w ten sposób we gdzie znaleźć jego wartość w pamięci 

---

### 🗃 Keyword Connections (powiązania)

- [[obiekt]]
- [[adres-w-pamięci]]
- [[mutowalność]]
- [[niemutowalność]]
- [[zmienna-jako-referencja]]
- [[dynamiczne-typowanie]]
- [[python-id]]
---

### 🖼 Rysunek / schemat / diagram ASCII

```
# x = [1, 2]

     ┌───────────────────────────┐
x ───►   OBIEKT: [1, 2]          │
     │   id = 140498195121552    │
     └───────────────────────────┘

```
- obiekt ma _adres_ (ID),
    
- zmienna `x` tylko **wskazuje** na obiekt.
---

## ✨ Metoda Feynmana (1–2 zdania)

`id()` zwraca adres w pamięci, gdzie przechowywany jest obiekt.  
Zmienna nie przechowuje wartości, tylko referencję do tego adresu.  
Obiekty mutowalne zachowują ten sam adres, a niemutowalne tworzą nowy.

---

## ⚠ Typowe błędne wyobrażenie
ID to numer przypisany do zmiennej.

To nieprawda. 

**Dlaczego to błędne:**
Zmienna nie ma własnego ID.
To obiekt (wartość w pamięci) ma ID.
Zmienna to tylko etykieta / wskazanie na obiekt.

```
x ───►  [ 10 ]
          ▲
          │
         ID (adres w pamięci)

```

---

## 📌 Kontrast (X vs Y)

| Cecha                                                 | id                                   | Koncepcja przeciwna (mylny/intuicyjny model) |
| ----------------------------------------------------- | ------------------------------------ | -------------------------------------------- |
| Do czego należy?                                      | Do obiektu                           | Do zmiennej                                  |
| Co opisuje?                                           | Miejsce w pamięci, gdzie stoi obiekt | Samą zmienną (błędne)                        |
| Czy zmienia się przy modyfikacji mutowalnego obiektu? | ❌ Nie                                | —                                            |
| Czy zmienia się przy zmianie wartości niemutowalnej?  | ✅ Tak (nowy obiekt → nowe ID)        | —                                            |
| Czy dwie zmienne mogą mieć ten sam id?                | ✅ Tak, jeśli wskazują na 1 obiekt    | ❌ W błędnym modelu byłoby to niemożliwe      |
| Czy id opisuje typ?                                   | ❌ Nie                                | —                                            |
| Czy id oznacza identyfikator zmiennej?                | ❌ Nie                                | Tak (w błędnym modelu)                       |
| Mentalny model                                        | Adres domu, w którym stoi pudełko    | Etykieta przyklejona do pudełka              |

---

## 🗂 Fiszki (SRS)

Czym jest id() w Pythonie? 
??
Liczbowy adres w pamięci, pod którym przechowywany jest obiekt.

Czy `id` należy do zmiennej?
??
❌ Nie.
id należy do obiektu, nie do zmiennej.

Dlaczego id mutowalnego obiektu się nie zmienia?
??
Bo obiekt jest modyfikowany w miejscu — nie powstaje nowy obiekt.

Dlaczego `id` niemutowalnego obiektu zmienia się po przypisaniu nowej wartości?
??
Bo Python tworzy **nowy obiekt** i nadaje mu **nowy adres**.

Czy dwie zmienne mogą mieć ten sam `id()`?
??
Tak — jeśli **wskazują na ten sam obiekt**.

Jakie jest najczęstsze błędne wyobrażenie o `id()`?
??
Że `id` należy do **zmiennej**, a nie do obiektu.

Jaki jest dobry mentalny model `id()`?
??
**Adres domu**, w którym stoi pudełko (obiekt).  
Zmienna to tylko **karteczka** wskazująca na ten adres.

---

## 🔗 Powiązane notatki