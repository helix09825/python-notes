# Callable

## 🧠 Co to jest?

`Callable` to typ używany do opisywania **funkcji** w adnotacjach typów. Pozwala określić, jakie argumenty funkcja przyjmuje i jaki typ zwraca.

## 🔧 Jak to działa?

```python
from typing import Callable

# Funkcja przyjmująca dwa inty i zwracająca int
Func = Callable[[int, int], int]

# Funkcja przyjmująca str i zwracająca bool
Validator = Callable[[str], bool]
```

## 🧪 Przykład

```python
from typing import Callable

# Definiowanie typów funkcji
MathOp = Callable[[int, int], int]
Validator = Callable[[str], bool]
Transformer = Callable[[str], str]

def add(a: int, b: int) -> int:
    return a + b

def multiply(a: int, b: int) -> int:
    return a * b

def is_valid_email(email: str) -> bool:
    return "@" in email

def to_uppercase(text: str) -> str:
    return text.upper()

def calculate(operation: MathOp, x: int, y: int) -> int:
    """Wykonuje operację matematyczną na dwóch liczbach."""
    return operation(x, y)

def validate_data(validator: Validator, data: str) -> bool:
    """Waliduje dane używając podanej funkcji walidującej."""
    return validator(data)

# Użycie
result1 = calculate(add, 5, 3)        # 8
result2 = calculate(multiply, 4, 7)   # 28
is_valid = validate_data(is_valid_email, "test@example.com")  # True
```

## 🧩 Mnemotechniki

### 🔄 Tłumaczenie jako analogia

**Callable** = przepis na funkcję - mówisz, jakie składniki (argumenty) potrzebujesz i co dostaniesz na wyjściu (wartość zwracana). To jak kontrakt dla funkcji przekazywanej jako argument.

## ✨ Metoda Feynmana (1–2 zdania)

Callable pozwala typować funkcje przekazywane jako argumenty, określając jakie argumenty przyjmują i jaki typ zwracają.

## 🗂 Fiszki (SRS) #flashcards

Jakiego typu użyjemy w Pythonie do opisania funkcji w adnotacjach typów?
?
Do opisywania funkcji używamy typu Callable.

Do czego użyjemy typu Callable w adnotacjach typów?
?
Callable służy do określania jakie argumenty funkcja przyjmuje i jaki typ zwraca, dzięki czemu możemy typować funkcje przekazywane jako argumenty.

