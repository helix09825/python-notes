# TypedDict

## 🧠 Co to jest?

`TypedDict` to sposób na tworzenie słowników z **określonymi kluczami i typami wartości**. Idealne do struktur JSON-owych i danych, które mają stałą strukturę, ale są reprezentowane jako słowniki.

## 🔧 Jak to działa?

```python
from typing import TypedDict

class User(TypedDict):
    id: int
    name: str
    active: bool

# Użycie
user: User = {
    "id": 1,
    "name": "Jan",
    "active": True
}
```

## 🧪 Przykład

```python
from typing import TypedDict

class User(TypedDict):
    id: int
    name: str
    email: str
    active: bool

class Address(TypedDict):
    street: str
    city: str
    zip_code: str

def create_user(user_id: int, name: str, email: str) -> User:
    """Tworzy użytkownika zgodnie ze strukturą TypedDict."""
    return {
        "id": user_id,
        "name": name,
        "email": email,
        "active": True
    }

def get_user_info(user: User) -> str:
    """Wyświetla informacje o użytkowniku."""
    status = "aktywny" if user["active"] else "nieaktywny"
    return f"{user['name']} ({user['email']}) - {status}"

# Użycie
user = create_user(1, "Jan", "jan@example.com")
info = get_user_info(user)  # "Jan (jan@example.com) - aktywny"
```

## 🧩 Mnemotechniki

### 🔄 Tłumaczenie jako analogia

**TypedDict** = formularz z określonymi polami - każdy formularz ma te same pola (klucze), ale wartości mogą być różne. To jak szablon dokumentu, który zawsze ma te same sekcje.

## ✨ Metoda Feynmana (1–2 zdania)

TypedDict pozwala zdefiniować strukturę słownika z określonymi kluczami i typami wartości, co jest idealne do pracy z danymi JSON i strukturami danych o stałej formie.

## 🗂 Fiszki (SRS) #flashcards

Jakiego typu użyjemy w Pythonie do opisania słownika z określonymi kluczami i typami wartości?

?

Do opisywania słowników z określonymi kluczami i typami wartości używamy TypedDict, który pozwala zdefiniować strukturę słownika podobnie do klasy.

Do czego użyjemy TypedDict w adnotacjach typów?

?

TypedDict służy do definiowania struktury słowników z określonymi kluczami i typami wartości. Jest idealne do pracy z danymi JSON, konfiguracjami i strukturami danych o stałej formie, gdzie chcemy mieć gwarancję, że słownik ma wszystkie wymagane klucze z odpowiednimi typami.

