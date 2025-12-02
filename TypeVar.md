# TypeVar i Generic

## 🧠 Co to jest?

`TypeVar` i `Generic` pozwalają tworzyć **parametryzowane typy** - typy z "dziurą" do wypełnienia. To jak szablony w C++ lub generyki w TypeScript/Java - możesz stworzyć klasę lub funkcję, która działa z różnymi typami, zachowując bezpieczeństwo typów.

## 🔧 Jak to działa?

```python
from typing import TypeVar, Generic

T = TypeVar("T")

class Box(Generic[T]):
    def __init__(self, value: T):
        self.value = value
```

## 🧪 Przykład

```python
from typing import TypeVar, Generic

T = TypeVar("T")

class Box(Generic[T]):
    """Pudełko, które może przechowywać wartość dowolnego typu."""
    def __init__(self, value: T):
        self.value = value
    
    def get(self) -> T:
        return self.value

def first_item(items: list[T]) -> T:
    """Zwraca pierwszy element listy dowolnego typu."""
    return items[0]

# Użycie
int_box = Box(42)           # Box[int]
str_box = Box("hello")      # Box[str]
numbers = [1, 2, 3]
first_num = first_item(numbers)  # int

# Type checker wie, że:
# int_box.value jest typu int
# str_box.value jest typu str
# first_num jest typu int
```

## 🧩 Mnemotechniki

### 🔄 Tłumaczenie jako analogia

**TypeVar** = szablon z pustym miejscem - jak formularz, gdzie możesz wpisać różne typy danych, ale struktura pozostaje taka sama. To jak pudełko, które może przechowywać różne rzeczy, ale zawsze jest pudełkiem.

## ✨ Metoda Feynmana (1–2 zdania)

TypeVar i Generic pozwalają tworzyć parametryzowane typy - klasy i funkcje, które działają z różnymi typami, zachowując bezpieczeństwo typów dzięki "dziurom" wypełnianym konkretnymi typami.

## 🗂 Fiszki (SRS) #flashcards

Jakiego typu użyjemy w Pythonie do tworzenia parametryzowanych typów (generyków)?

?

Do tworzenia parametryzowanych typów używamy TypeVar i Generic, które pozwalają stworzyć typ z "dziurą" do wypełnienia konkretnym typem.

Do czego użyjemy TypeVar i Generic w adnotacjach typów?

?

TypeVar i Generic służą do tworzenia generyków - klas i funkcji, które działają z różnymi typami, zachowując bezpieczeństwo typów. Pozwalają stworzyć uniwersalne struktury danych (np. Box[T]) lub funkcje (np. first_item(list[T])), które zachowują informację o typie w czasie kompilacji.

