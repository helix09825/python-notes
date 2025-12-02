# Never

## 🧠 Co to jest?

`Never` oznacza, że funkcja **nigdy nie zwraca wartości** - zawsze kończy się wyjątkiem, nieskończoną pętlą, lub innym sposobem, który uniemożliwia normalny powrót.

## 🔧 Jak to działa?

```python
from typing import Never

def fail(msg: str) -> Never:
    raise RuntimeError(msg)

def infinite_loop() -> Never:
    while True:
        pass
```

## 🧪 Przykład

```python
from typing import Never

def fail(message: str) -> Never:
    """Funkcja, która zawsze rzuca wyjątek - nigdy nie zwraca wartości."""
    raise RuntimeError(message)

def assert_positive(value: int) -> Never | None:
    """Sprawdza czy wartość jest dodatnia, jeśli nie - rzuca wyjątek."""
    if value <= 0:
        fail(f"Wartość {value} musi być dodatnia")
    # Jeśli dotarliśmy tutaj, funkcja zwraca None (lub mogłaby zwrócić wartość)

def infinite_loop() -> Never:
    """Nieskończona pętla - nigdy nie zwraca wartości."""
    while True:
        print("Działam w nieskończoność...")

def process_data(data: list[int]) -> int:
    """Przetwarza dane, ale rzuca wyjątek jeśli lista jest pusta."""
    if not data:
        fail("Lista nie może być pusta")
    # Type checker wie, że jeśli dotarliśmy tutaj,
    # data nie jest pusta, bo fail() nigdy nie zwraca
    return sum(data)

# Użycie
try:
    result = process_data([1, 2, 3])  # 6
    # process_data([])  # RuntimeError: Lista nie może być pusta
except RuntimeError as e:
    print(f"Błąd: {e}")
```

## 🧩 Mnemotechniki

### 🔄 Tłumaczenie jako analogia

**Never** = ślepa uliczka bez wyjścia - funkcja wchodzi, ale nigdy nie wraca normalnie. To jak funkcja, która zawsze kończy się awarią lub działa w nieskończoność.

## ✨ Metoda Feynmana (1–2 zdania)

Never oznacza, że funkcja nigdy nie zwraca wartości - zawsze kończy się wyjątkiem, nieskończoną pętlą lub innym sposobem uniemożliwiającym normalny powrót.

## 🗂 Fiszki (SRS) #flashcards

Jakiego typu użyjemy w Pythonie do oznaczenia funkcji, która nigdy nie zwraca wartości?

?

Do oznaczenia funkcji, która nigdy nie zwraca wartości, używamy typu Never, który wskazuje, że funkcja zawsze kończy się wyjątkiem, nieskończoną pętlą lub innym sposobem uniemożliwiającym normalny powrót.

Do czego użyjemy typu Never w adnotacjach typów?

?

Never służy do oznaczenia funkcji, które nigdy nie zwracają wartości - np. funkcji rzucających wyjątki (fail()), nieskończonych pętli, lub funkcji, które zawsze przerywają wykonanie programu. Type checker może użyć tej informacji do lepszej analizy przepływu kodu.

