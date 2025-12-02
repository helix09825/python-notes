# Optional

## 🧠 Co to jest?

`Optional` to specjalny przypadek `Union`, który oznacza, że wartość może być danego typu **lub** `None`. Jest to równoważne `Union[T, None]`.

## 🔧 Jak to działa?

```python
from typing import Optional

# Optional[str] = Union[str, None]
name: Optional[str] = "Jan"
name = None  # też OK

# Nowa składnia (Python 3.10+)
name2: str | None = "Jan"
```

## 🧪 Przykład

```python
from typing import Optional

def find_user(user_id: int) -> Optional[dict]:
    """Zwraca użytkownika lub None jeśli nie istnieje."""
    users = {
        1: {"name": "Jan", "age": 25},
        2: {"name": "Anna", "age": 30}
    }
    return users.get(user_id)  # Zwraca dict lub None

def greet_user(user_id: int) -> str:
    """Wita użytkownika lub zwraca komunikat o braku użytkownika."""
    user = find_user(user_id)
    if user is None:
        return "Użytkownik nie istnieje"
    return f"Witaj, {user['name']}!"

# Użycie
user1 = find_user(1)    # {"name": "Jan", "age": 25}
user2 = find_user(999)  # None
greeting = greet_user(1)  # "Witaj, Jan!"
```

## 🧩 Mnemotechniki

### 🔄 Tłumaczenie jako analogia

**Optional** = opcjonalne pole w formularzu - może być wypełnione (ma wartość) lub puste (None). To jak pytanie "Czy masz drugie imię?" - możesz odpowiedzieć lub zostawić puste.

## ✨ Metoda Feynmana (1–2 zdania)

Optional to skrót dla Union[T, None], który oznacza, że wartość może być danego typu lub None - idealne do opcjonalnych parametrów i wartości, które mogą nie istnieć.

## 🗂 Fiszki (SRS) #flashcards

Jakiego typu użyjemy w Pythonie do opisania zmiennej, która może być str lub None?

?

Do opisywania zmiennej, która może być danego typu lub None, używamy typu Optional (lub składni T | None w Pythonie 3.10+).

Do czego użyjemy typu Optional w adnotacjach typów?

?

Optional służy do określania, że zmienna może być danego typu lub None. Jest to skrót dla Union[T, None] i jest często używany do opcjonalnych parametrów funkcji lub wartości, które mogą nie istnieć (np. wynik wyszukiwania, które może nic nie znaleźć).

