
aliases: []  
tags: [theory, cs, programming]  
sr-due: true
graph: false

#review 

---

## 🧠 Co to jest?
 **`@property`** to dekorator w Pythonie, który pozwala **udostępnić metodę jak atrybut**.  
Dzięki temu możemy **kontrolować sposób odczytu i zapisu danych**, zachowując prosty interfejs obiektu.

@property to Descriptor czyli objekt z metodami `__get__, __set__, __delete__`  

## 🔧 Jak to działa?
`@property` przechwytuje dostęp do atrybutu i zamienia go w wywołanie metody, pozwalając kontrolować odczyt i zapis danych.

## 🧪 Przykład

```python
class User:
    @property
    def age(self):
        return self._age

    @age.setter
    def age(self, value):
        if value < 0:
            raise ValueError("Age must be positive")
        self._age = value
```

---

## 🧩 Mnemotechniki

### 🅰 Akronim

**Akronim:**

**Rozwinięcie:**

- A —
    
- B —
    
- C —
    

---

### 🔄 Tłumaczenie jako analogia

**Analogia:** 
**Property = portier przy drzwiach**

- **Drzwi** → atrybut (`user.age`)
    
- **Portier** → `@property`
    
- **Pomieszczenie** → prawdziwe dane (`_age`)
---

### 🗃 Keyword Connections (powiązania)

- [[Class]]
    
- [[__set__]]
    
- [[__get__]]
    
- [[__delete__]] 
	
-  [[descriptor]]

---

### 🖼 Rysunek / schemat / diagram ASCII

```
[user.age = 20]  →  [@property.setter]  →  [_age = 20]
[user.age]       →  [@property.getter]  →  [return _age]
```

![[Pasted image 20260122074825.png]]

---

## ✨ Metoda Feynmana (1–2 zdania)

`@property` to szatniarz: wygląda jak proste oddanie i odebranie płaszcza, ale to on zarządza dostępem do wieszaków.

---

## ⚠ Typowe błędne wyobrażenie

Nie wiedziałem, który scenariusz zajdzie, ale poprawnie intuicyjnie rozpoznałem, że `self.age = value` w setterze prowadzi do nieskończonej rekurencji zakończonej `RecursionError`, a nie do losowego zachowania.


---

## 📌 Kontrast (X vs Y)

| Cecha | @property | Koncepcja przeciwna |
| ----- | --------- | ------------------- |
|       |           |                     |
|       |           |                     |

---

## 🗂 Fiszki (SRS) #flashcards 

Czy `@property` przechowuje dane?  
?  
Nie. `@property` tylko zarządza dostępem do danych lub je oblicza.

---

Gdzie faktycznie są przechowywane dane obsługiwane przez `@property`?  
?  
W osobnych atrybutach (np. `_age`) albo wcale, jeśli property jest obliczeniowe.

---

Co dokładnie dzieje się, gdy odczytujesz `obj.age`?  
?  
Python wywołuje metodę deskryptora (`__get__`) zamiast czytać pole.

---

Co się stanie, jeśli w setterze napiszesz `self.age = value`?  
?  
Setter wywoła samego siebie w nieskończonej rekurencji zakończonej `RecursionError`.

---

Czy brak setter’a sprawia, że dane są readonly?  
?  
Nie. Readonly jest tylko property; dane (_age) nadal można zmienić bezpośrednio.

---

Czy `@property` musi opierać się na stanie obiektu?  
?  
Nie. Property może być czysto obliczeniowe i nie przechowywać żadnych danych.

---

Czy użytkownik może ominąć `@property` i zmienić `_age`?  
?  
Tak. To dozwolone, ale łamie konwencję i kontrakt obiektu.

---

Czym mentalnie jest `@property`?  
?  
Warstwą logiki między API obiektu a jego stanem lub obliczeniami.

---

## 🔗 Powiązane notatki