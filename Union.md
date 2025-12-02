# Union i Optional

## 🧠 Co to jest?

`Union` i `Optional` to adnotacje typów w Pythonie, które pozwalają określić, że zmienna może mieć jeden z kilku typów.

- `Union[A, B]` = może być typu A **lub** typu B
- `Optional[A]` = `Union[A, None]` = może być typu A **lub** None
- `A | B` = nowa składnia (Python 3.10+) równoważna `Union[A, B]`

## 🔧 Jak to działa?

```python
from typing import Union, Optional

# Union - może być int lub str
age: Union[int, str] = 25
age = "dwadzieścia pięć"  # też OK

# Nowa składnia (Python 3.10+)
age2: int | str = 25

# Optional - może być str lub None
name: Optional[str] = "Jan"
name = None  # też OK

# Optional[str] jest równoważne Union[str, None]
name2: str | None = "Jan"
```

## 🧪 Przykład

```python
from typing import Union, Optional

def process_age(age: Union[int, str]) -> int:
    """Konwertuje wiek na int, niezależnie od tego czy jest int czy str."""
    if isinstance(age, str):
        return int(age)
    return age

def get_user_name(user_id: int) -> Optional[str]:
    """Zwraca nazwę użytkownika lub None jeśli nie istnieje."""
    users = {1: "Jan", 2: "Anna"}
    return users.get(user_id)  # Zwraca str lub None

# Użycie
age1 = process_age(25)        # OK
age2 = process_age("30")      # OK
name = get_user_name(1)       # "Jan"
name2 = get_user_name(999)    # None
```

## 🧩 Mnemotechniki

### 🔄 Tłumaczenie jako analogia

**Union** = "lub" w logice - zmienna może być **jednym z** podanych typów, jak wybór z menu.

**Optional** = "może być, ale nie musi" - jak opcjonalne pole w formularzu, które może pozostać puste (None).

## ✨ Metoda Feynmana (1–2 zdania)

Union pozwala określić, że zmienna może mieć jeden z kilku typów, a Optional to specjalny przypadek Union, gdzie drugim typem jest None.

## 🗂 Fiszki (SRS) #flashcards

Jakiego typu użyjemy w Pythonie do opisania zmiennej, która może być typu int lub str?

?

Do opisywania zmiennej, która może być jednego z kilku typów, używamy typu Union (lub składni | w Pythonie 3.10+).

Do czego użyjemy typu Optional w adnotacjach typów?

?

Optional służy do określania, że zmienna może być danego typu lub None. Jest to skrót dla Union[T, None] i jest często używany do opcjonalnych parametrów funkcji lub wartości, które mogą nie istnieć.

