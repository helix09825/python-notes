# Final

## 🧠 Co to jest?

`Final` oznacza, że zmienna lub atrybut **nie powinien być nadpisywany** po inicjalizacji. To wskazówka dla programisty i narzędzi typu checker, że wartość powinna pozostać stała.

## 🔧 Jak to działa?

```python
from typing import Final

# Stała wartość
API_KEY: Final = "secret-key-123"
MAX_RETRIES: Final = 3

# Final w klasie
class Config:
    VERSION: Final = "1.0.0"
    TIMEOUT: Final = 30
```

## 🧪 Przykład

```python
from typing import Final

# Stałe konfiguracyjne
API_BASE_URL: Final = "https://api.example.com"
MAX_CONNECTIONS: Final = 100
DEFAULT_TIMEOUT: Final = 30

class DatabaseConfig:
    """Konfiguracja bazy danych z wartościami Final."""
    HOST: Final = "localhost"
    PORT: Final = 5432
    PROTOCOL: Final = "postgresql"

def connect_to_api() -> None:
    """Łączy się z API używając stałego URL."""
    print(f"Łączenie z {API_BASE_URL}")

# Użycie
connect_to_api()  # Łączenie z https://api.example.com

# Próba nadpisania (błąd w type checkerze)
# API_BASE_URL = "nowy-url"  # Błąd!
```

## 🧩 Mnemotechniki

### 🔄 Tłumaczenie jako analogia

**Final** = stała wartość, która nie powinna się zmieniać - jak numer wersji aplikacji, klucz API, czy maksymalna liczba połączeń. To jak napis "Nie dotykać" - wartość jest ustawiona raz i powinna pozostać niezmieniona.

## ✨ Metoda Feynmana (1–2 zdania)

Final oznacza, że zmienna nie powinna być nadpisywana po inicjalizacji - to wskazówka dla programisty i narzędzi, że wartość powinna pozostać stała.

## 🗂 Fiszki (SRS) #flashcards

Jakiego typu użyjemy w Pythonie do oznaczenia zmiennej, która nie powinna być nadpisywana?
?
Do oznaczenia zmiennej, która nie powinna być nadpisywana, używamy typu Final, który wskazuje, że wartość powinna pozostać stała po inicjalizacji.

Do czego użyjemy typu Final w adnotacjach typów?
?
Final służy do oznaczenia zmiennych, stałych konfiguracyjnych i atrybutów klas, które nie powinny być nadpisywane. Jest używane do wartości takich jak klucze API, numery wersji, limity i inne stałe, które powinny pozostać niezmienione przez cały czas życia programu.

