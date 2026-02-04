
aliases: []  
tags: [theory, cs, programming]  
sr-due: true
graph: false

#review 

---

## 🧠 Co to jest?
Dzięki zasadzie hermetyzacji dane i metody są opakowane w unikalną jednostkę, co ogranicza dostęp do zmiennych i metod, zapobiegając w ten sposób przypadkowej modyfikacji danych. Ograniczenia te można wprowadzić za pomocą trzech modyfikatorów dostępu:

1. **Public** (publiczny)
2. **Protected** (chroniony)
3. **Private** (prywatny)

## 🔧 Jak to działa?
#### 1️⃣ Publiczne atrybuty (default)

```python
class User:
    def __init__(self, name):
        self.name = name

u = User("Kamil")
print(u.name)        # Kamil
u.name = "Admin"     # OK
```

#### 2️⃣_protected - konwencja (jeden podkreślnik)
```python
class User:
    def __init__(self, name):
        self._name = name
```
- `_name` **nie jest prywatne technicznie**
    
- To **sygnał dla devów**:  
    👉 „Nie używaj tego poza klasą / dziedziczeniem”


#### 3️⃣ __private – name mangling (dwa podkreślniki)

```python
class User:
    def __init__(self, name):
        self.__name = name

```

Python **zmienia nazwę pola wewnętrznie**:

`print(u.__name)        # ❌ AttributeError print(u._User__name)  # ✅ działa`

➡️ To się nazywa **name mangling**  
➡️ Chroni przed:

- przypadkowym nadpisaniem w klasach dziedziczących
    
- kolizjami nazw
    

💡 To nadal _da się obejść_, ale **musisz chcieć**
## 🧪 Przykład

```python
class Wepon: 
	def __init__(self, name, power):
		self.__name = name
		self.__power = power 
		
sword = Wepon('sword', 20)
sword.name = 'mace' # nie zadziała 
sword._Wepon__name = 'mace' # zadziała ale nie powinieneś
```


### ✅ Pythonic way:
[[@property]]
Python **nie wymusza getterów/setterów** jak Java  
Zamiast tego używa **@property**
---

## 🧩 Mnemotechniki

### 🅰 Akronim

**Akronim:** H -> P

**Rozwinięcie:**

- H — Hermetyzacja
    
- P — Property
    
---

### 🔄 Tłumaczenie jako analogia

**Analogia:** 
Hermetyzacja to sytuacja, w której wiele osób korzysta z tego samego obiektu,  
ale tylko określone akcje są dostępne dla wybranych ról — przez jasno zdefiniowane API.

Hermetyzacja to zamknięcie danych i wystawienie tylko bezpiecznych drzwi (API) do ich obsługi.

---

### 🗃 Keyword Connections (powiązania)

- [[OOP]]
- [[@property]]
---

### 🖼 Rysunek / schemat / diagram ASCII

![[Pasted image 20260120210346.png]]
---

## ✨ Metoda Feynmana (1–2 zdania)

Hermetyzacja w Pythonie to zamykanie danych i blokowanie do nich dostępu, kontrolowanie dostępu do niej za pomocą API obiektu. Najczęściej stosowaną techniką jest małpa property, dzięki któremu kontrolujemy zapis oraz odczyt danych.  W Pythonie nie ma sztywnych zasad dotyczących hermetyzacji, ale stosuje się trzy konwencje. 

---

## ⚠ Typowe błędne wyobrażenie

 **Nie — celem hermetyzacji nie jest security, tylko kontrola złożoności i stabilność API.**
**Tak — bo hermetyzacja chroni API klasy, nawet bez dziedziczenia.**

---

## 📌 Kontrast (X vs Y)

| Cecha      | public    | protected                               | private                                      |
| ---------- | --------- | --------------------------------------- | -------------------------------------------- |
| zapis      | self.name | self._name                              | self.__name                                  |
| dostęp     | wszędzie  | **konwencja:** „do użytku wewnętrznego” | **technicznie możliwy**, ale z name mangling |
| Wymuszanie | ❌ brak    | ❌ brak                                  | ❌ brak (tylko utrudnienie)                   |

* Jest to tylko umowne, python tego nie wymusza ale używanie tego poza tymi zakresami jest uznawane za złą praktykę

---

## 🗂 Fiszki (SRS) #flashcards 

**Czym jest hermetyzacja w Pythonie?**  
?  
Ukrycie danych i dostęp do nich **tylko przez API obiektu**.

---

**Jak realizuje się hermetyzację w Pythonie w praktyce?**  
?  
Przez `@property` — dane w środku, kontrola odczytu i zapisu na zewnątrz.

---

**Co oznaczają `_attr` i `__attr` w kontekście hermetyzacji?**  
?  
`_attr` to sygnał „wewnętrzne”, a `__attr` chroni nazwę przez _name mangling_.

---

## 🔗 Powiązane notatki