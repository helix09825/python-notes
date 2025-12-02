# Annotated

## 🧠 Co to jest?

`Annotated` pozwala dodać **metadane do typu** bez zmiany samego typu. Te metadane mogą być używane przez narzędzia do walidacji, generowania API, dokumentacji i innych celów.

## 🔧 Jak to działa?

```python
from typing import Annotated

Age = Annotated[int, "must be >= 0"]
Email = Annotated[str, "email format"]
```

## 🧪 Przykład

```python
from typing import Annotated

# Typy z metadanymi
Age = Annotated[int, "must be >= 0 and <= 150"]
Email = Annotated[str, "must be valid email format"]
PositiveInt = Annotated[int, "must be positive"]

def create_user(name: str, age: Age, email: Email) -> dict:
    """Tworzy użytkownika z walidacją na podstawie metadanych."""
    # W rzeczywistej aplikacji, metadane mogą być używane przez
    # frameworki do automatycznej walidacji (np. FastAPI, Pydantic)
    return {
        "name": name,
        "age": age,
        "email": email
    }

# Użycie
user = create_user("Jan", 25, "jan@example.com")

# W FastAPI/Pydantic metadane mogą być używane tak:
# from pydantic import Field
# Age = Annotated[int, Field(ge=0, le=150)]
```

## 🧩 Mnemotechniki

### 🔄 Tłumaczenie jako analogia

**Annotated** = etykieta z dodatkowymi informacjami - typ to podstawowa informacja (np. "to jest int"), a metadane to dodatkowe wskazówki (np. "musi być >= 0"). To jak naklejka na produkcie z dodatkowymi informacjami.

## ✨ Metoda Feynmana (1–2 zdania)

Annotated pozwala dodać metadane do typu bez zmiany samego typu - te metadane mogą być używane przez narzędzia do walidacji, generowania API i dokumentacji.

## 🗂 Fiszki (SRS) #flashcards

Jakiego typu użyjemy w Pythonie do dodania metadanych do typu bez zmiany samego typu?

?

Do dodawania metadanych do typu używamy Annotated, który pozwala dołączyć dodatkowe informacje (np. ograniczenia, opisy) do typu bez zmiany jego podstawowego znaczenia.

Do czego użyjemy typu Annotated w adnotacjach typów?

?

Annotated służy do dodawania metadanych do typów, które mogą być używane przez narzędzia do walidacji (np. Pydantic), generowania API (np. FastAPI), dokumentacji i innych celów. Pozwala określić dodatkowe ograniczenia lub informacje o typie (np. Age = Annotated[int, "must be >= 0"]).

