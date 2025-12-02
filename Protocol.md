# Protocol

## 🧠 Co to jest?

`Protocol` to sposób na definiowanie **zachowania** zamiast konkretnego typu klasy. Implementuje koncepcję "duck typing" z typami - jeśli obiekt ma wymagane metody, pasuje do protokołu, niezależnie od jego klasy.

## 🔧 Jak to działa?

```python
from typing import Protocol

class Flyer(Protocol):
    def fly(self) -> None: ...

def lift_off(obj: Flyer) -> None:
    obj.fly()
```

## 🧪 Przykład

```python
from typing import Protocol

class Flyer(Protocol):
    """Protokół dla obiektów, które mogą latać."""
    def fly(self) -> None: ...

class Bird:
    """Ptak - implementuje protokół Flyer."""
    def fly(self) -> None:
        print("Ptak leci!")

class Airplane:
    """Samolot - implementuje protokół Flyer."""
    def fly(self) -> None:
        print("Samolot startuje!")

class Car:
    """Samochód - NIE implementuje protokołu Flyer."""
    def drive(self) -> None:
        print("Samochód jedzie!")

def lift_off(obj: Flyer) -> None:
    """Funkcja przyjmuje dowolny obiekt, który ma metodę fly()."""
    obj.fly()

# Użycie
bird = Bird()
plane = Airplane()
car = Car()

lift_off(bird)   # OK - Bird ma metodę fly()
lift_off(plane)  # OK - Airplane ma metodę fly()
# lift_off(car)  # Błąd - Car nie ma metody fly()
```

## 🧩 Mnemotechniki

### 🔄 Tłumaczenie jako analogia

**Protocol** = kontrakt zachowania - nie ważne, czy to ptak, samolot czy superman, jeśli ma metodę `fly()`, może być użyty w funkcji `lift_off()`. To jak sprawdzanie umiejętności zamiast dyplomu - ważne jest, co obiekt potrafi, nie skąd pochodzi.

## ✨ Metoda Feynmana (1–2 zdania)

Protocol definiuje zachowanie zamiast konkretnego typu - jeśli obiekt ma wymagane metody, pasuje do protokołu, niezależnie od jego klasy. To duck typing z typami.

## 🗂 Fiszki (SRS) #flashcards

Jakiego typu użyjemy w Pythonie do definiowania zachowania zamiast konkretnego typu klasy?

?

Do definiowania zachowania zamiast konkretnego typu klasy używamy Protocol, który pozwala określić, jakie metody obiekt musi mieć, aby pasować do protokołu.

Do czego użyjemy typu Protocol w adnotacjach typów?

?

Protocol służy do definiowania kontraktów zachowania - jeśli obiekt ma wymagane metody (np. fly()), pasuje do protokołu niezależnie od swojej klasy. To implementacja "duck typing" z typami, gdzie ważne jest zachowanie obiektu, a nie jego konkretna klasa.

