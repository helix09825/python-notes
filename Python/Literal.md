# Literal

## 🧠 Co to jest?

`Literal` pozwala określić, że wartość może być **tylko jedną z konkretnych, predefiniowanych wartości**. To jak enum, ale dla wartości literałowych (stringi, liczby, itp.).

## 🔧 Jak to działa?

```python
from typing import Literal

Status = Literal["ok", "error", "pending"]
Mode = Literal["strict", "safe"]
Priority = Literal[1, 2, 3, 4, 5]

# Użycie
status: Status = "ok"  # OK
status = "error"       # OK
status = "unknown"     # Błąd typu!
```

## 🧪 Przykład

```python
from typing import Literal

Status = Literal["ok", "error", "pending"]
Mode = Literal["strict", "safe"]
LogLevel = Literal["DEBUG", "INFO", "WARNING", "ERROR"]

def process_data(data: str, mode: Mode = "strict") -> Status:
    """Przetwarza dane w określonym trybie."""
    if mode == "strict":
        if not data:
            return "error"
        return "ok"
    else:  # safe mode
        return "ok"

def log_message(message: str, level: LogLevel) -> None:
    """Loguje wiadomość na określonym poziomie."""
    print(f"[{level}] {message}")

# Użycie
result = process_data("test", mode="strict")  # "ok"
log_message("Aplikacja uruchomiona", "INFO")   # [INFO] Aplikacja uruchomiona
```

## 🧩 Mnemotechniki

### 🔄 Tłumaczenie jako analogia

**Literal** = wybór z ograniczonej listy - jak wybór rozmiaru koszulki (S, M, L, XL) lub statusu zamówienia (nowe, w trakcie, zakończone). Możesz wybrać tylko jedną z dozwolonych wartości.

## ✨ Metoda Feynmana (1–2 zdania)

Literal ogranicza wartość do konkretnych, predefiniowanych literałów, co jest idealne do parametrów API, konfiguracji i statusów, gdzie chcemy mieć kontrolę nad dozwolonymi wartościami.

## 🗂 Fiszki (SRS) #flashcards

Jakiego typu użyjemy w Pythonie do ograniczenia wartości do konkretnych literałów (np. tylko "ok", "error", "pending")?
?
Do ograniczania wartości do konkretnych literałów używamy typu Literal, który pozwala określić dokładnie jakie wartości są dozwolone.
<!--SR:!2025-12-20,12,270-->

Do czego użyjemy typu Literal w adnotacjach typów?
?
Literal służy do ograniczania wartości parametrów do konkretnych, predefiniowanych literałów. Jest idealne do parametrów API, trybów działania, statusów i konfiguracji, gdzie chcemy mieć gwarancję, że wartość będzie jedną z dozwolonych opcji (np. mode: Literal["strict", "safe"]).
<!--SR:!2025-12-14,9,250-->

