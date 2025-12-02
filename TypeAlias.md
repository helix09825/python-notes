# TypeAlias

## 🧠 Co to jest?

`TypeAlias` pozwala tworzyć **czytelne nazwy** dla złożonych typów. Zamiast pisać długie definicje typów wielokrotnie, możesz stworzyć alias, który będzie łatwiejszy do zrozumienia i użycia.

## 🔧 Jak to działa?

```python
from typing import TypeAlias

# Tworzenie aliasów dla typów
UserId: TypeAlias = int
Coordinates: TypeAlias = tuple[float, float]
UserData: TypeAlias = dict[str, str | int]

# Użycie
def get_user(id: UserId) -> UserData:
    return {"name": "Jan", "age": 25}
```

## 🧪 Przykład

```python
from typing import TypeAlias

# Definiowanie aliasów
UserId: TypeAlias = int
Email: TypeAlias = str
Coordinates: TypeAlias = tuple[float, float]
UserProfile: TypeAlias = dict[str, str | int | bool]

def create_user(user_id: UserId, email: Email) -> UserProfile:
    """Tworzy profil użytkownika."""
    return {
        "id": user_id,
        "email": email,
        "active": True
    }

def get_location() -> Coordinates:
    """Zwraca współrzędne geograficzne."""
    return (52.2297, 21.0122)  # Warszawa

# Użycie
user = create_user(1, "jan@example.com")
location = get_location()  # (52.2297, 21.0122)
```

## 🧩 Mnemotechniki

### 🔄 Tłumaczenie jako analogia

**TypeAlias** = pseudonim dla typu - jak nadanie czytelnej nazwy skrótowi. Zamiast mówić "dict ze stringami i intami", mówisz "UserProfile" - od razu wiadomo, o co chodzi.

## ✨ Metoda Feynmana (1–2 zdania)

TypeAlias pozwala nadać czytelną nazwę złożonemu typowi, co czyni kod bardziej zrozumiałym i łatwiejszym w utrzymaniu.

## 🗂 Fiszki (SRS) #flashcards

Jakiego typu użyjemy w Pythonie do stworzenia czytelnej nazwy dla złożonego typu?

?

Do tworzenia czytelnych nazw dla złożonych typów używamy TypeAlias, który pozwala nadać znaczącą nazwę zamiast powtarzać długie definicje typów.

Do czego użyjemy TypeAlias w adnotacjach typów?

?

TypeAlias służy do tworzenia aliasów dla złożonych typów, co czyni kod bardziej czytelnym. Zamiast pisać `dict[str, str | int]` wielokrotnie, możemy stworzyć alias `UserProfile: TypeAlias = dict[str, str | int]` i używać go w całym kodzie.

