---
sr-due: 2025-12-15
sr-interval: 1
sr-ease: 227
---

# pakiety

aliases: []  
tags: [theory, cs, programming]  
sr-due: true
graph: false

#review 

---

## 🧠 Co to jest?
Pakiet (_package_) w Pythonie to **sposób organizacji kodu w foldery**, tak aby można było go importować jak moduły.

#### Najprostsza definicja

**Pakiet = katalog z modułami (plikami `.py`)**, który Python traktuje jako importowalną „przestrzeń nazw”.

#### Czy `__init__.py` jest wymagany?

- **Historycznie / klasycznie:** tak — katalog z plikiem `__init__.py` był rozpoznawany jako pakiet.
    
- **Dzisiaj (Python 3.3+):** istnieją też **namespace packages**, które **mogą działać bez `__init__.py`** (ale `__init__.py` nadal jest bardzo często używany, bo pozwala kontrolować inicjalizację pakietu).
    

### Po co jest `__init__.py`?

- uruchamia się przy `import moj_pakiet`
    
- może definiować, co pakiet „wystawia” na zewnątrz (np. przez importy w środku, `__all__`, ustawienia itp.)

## 🔧 Jak to działa?
Wyobraź sobie, że Python ma „mapę” miejsc, z których może ładować kod. Pakiet działa, bo import:

1. Szuka nazwy w ścieżkach importu (sys.path)
	sys.path to lista katalogów, które Python przegląda (m.in. katalog, w którym uruchamiasz skrypt + site-packages).
2. Rozpoznaje, co znalazł
	Dla import utils Python próbuje znaleźć:
	utils.py (zwykły moduł) albo
	katalog utils/ (kandydat na pakiet)a
3. Jeśli to katalog: ładuje pakiet
	Gdy w katalogu jest utils/__init__.py, Python:
		tworzy obiekt modułu utils
		uruchamia kod z __init__.py
		ustawia ważne pola: utils.__file__, utils.__path__, itp.
		zapisuje wynik w cache: sys.modules["utils"] (żeby drugi import był „za darmo”)
	
4. Import submodułów
	`from utils import strings:`
		jeśli w __init__.py jest from . import strings, to strings jest już dostępne
		jeśli nie ma, Python i tak może dodatkowo załadować utils/strings.py, ale to zależy od formy importu i tego co już jest w namespace pakietu.

## 🧪 Przykład

```python
my_app/
  main.py
  utils/
    __init__.py
    strings.py
    dates.py
    

from utils import strings
from utils.dates import today

import utils.strings
# albo
from utils import strings
# albo
from utils.strings import slugify

```

---

## 🧩 Mnemotechniki

### 🅰 Akronim

**PAKIET**

- **P**lik `__init__.py` (opcjonalnie dziś, ale klasycznie)
    
- **A**dresowalny przez `import`
    
- **K**atalog z modułami
    
- **I**nicjalizacja (kod w `__init__.py`)
    
- **E**ksport API (co wystawiasz na zewnątrz)
    
- **T**ożsamość w `sys.modules` (cache importu)
    

**IMPORT**

- **I**dzie po `sys.path`
    
- **M**oduł lub katalog
    
- **P**ali `__init__.py` (jeśli pakiet)
    
- **O**garnia submoduły (`pkg.mod`)
    
- **R**az ładuje, potem cache
    
- **T**rzyma w `sys.modules`
    

**PATH**

- **P**ython szuka
    
- **A**ktualny folder + site-packages
    
- **T**ropy w `sys.path`
    
- **H**it: pierwszy pasujący wygrywa
---

### 🔄 Tłumaczenie jako analogia

**Analogia:**
Pakiet to jak **szafa z szufladami**: sama szafa to folder, a każda szuflada to osobny plik/moduł z narzędziami.  
`import` to jak **sięganie po konkretną szufladę po nazwie**, a `__init__.py` to **karteczka na drzwiach**, która mówi „co jest w środku” i może od razu przygotować rzeczy na wierzchu.

---

### 🗃 Keyword Connections (powiązania)

[[package]]  
[[pakiet]]  
[[module]]  
[[moduł]]  
[[__init__.py]]  
[[import]]  
[[sys.path]]  
[[PYTHONPATH]]  
[[sys.modules]]  
[[namespace package]]  
[[relative import]]  
[[absolute import]]  
[[__all__]]  
[[__name__]]  
[[__package__]]  
[[__pycache__]]  
[[.pyc]]

---

### 🖼 Rysunek / schemat / diagram ASCII

![[Pasted image 20251213071131.png]]
---

## ✨ Metoda Feynmana (1–2 zdania)

---

## ⚠ Typowe błędne wyobrażenie
`from pkg import mod` nie importuje „tylko funkcji” — importuje **obiekt `mod`** (czyli submoduł), a nie „jedną funkcję”. Żeby wziąć funkcję: `from pkg.mod import func`.

`sys.path` nie „trzyma info o pakietach” — to lista **ścieżek folderów**, w których Python **szuka** modułów/pakietów.

Kropka w `from . import x` to nie „obecny katalog na dysku” w sensie CWD, tylko **pakiet aktualnego modułu** (relative import działa tylko w kontekście pakietu).




---

## 📌 Kontrast (X vs Y) ✅❌

| Cecha                                                              | pakiety | moduł |
| ------------------------------------------------------------------ | ------- | ----- |
| Jest katalogiem (folderem)                                         | ✅       | ❌     |
| Jest pojedynczym plikiem `.py`                                     | ❌       | ✅     |
| Może zawierać submoduły (np. `pkg.sub`)                            | ✅       | ❌     |
| Może zawierać inne pakiety (podpakiety)                            | ✅       | ❌     |
| Ma plik `__init__.py` (klasyczny pakiet)                           | ✅       | ❌     |
| Może działać bez `__init__.py` (namespace package)                 | ✅       | ❌     |
| Import wykonuje kod top-level (przy pierwszym imporcie)            | ✅       | ✅     |
| Ma `__file__` wskazujący na `.py` (zwykle)                         | ✅       | ✅     |
| Ma `__path__` (miejsca szukania submodułów)                        | ✅       | ❌     |
| Możesz zrobić `python -m X` żeby uruchomić „w kontekście importów” | ✅       | ✅     |
| `from X import *` może być kontrolowane przez `__all__`            | ✅       | ✅     |
| Jest wpisywany do `sys.modules` po imporcie                        | ✅       | ✅     |

---

## 🗂 Fiszki (SRS) #flashcards 

Czym różni się `from pkg import mod` od `from pkg.mod import func`?
?
`from pkg import mod` importuje submoduł jako obiekt `mod`; żeby importować funkcję, użyj `from pkg.mod import func`.
<!--SR:!2025-12-17,4,270-->

Czy `from pkg import mod` wykonuje kod z `pkg/mod.py`?
?
Tak. Import submodułu wykonuje jego kod top-level (globalny) przy pierwszym imporcie.
<!--SR:!2025-12-16,3,250-->

Co tak naprawdę robi `import pkg.mod`?
?
Ładuje pakiet `pkg`, potem ładuje submoduł `pkg.mod` i udostępnia go jako atrybut `pkg.mod`.
<!--SR:!2025-12-17,2,210-->

Czym jest `sys.path`?
?
To lista katalogów (ścieżek), w których Python szuka modułów i pakietów podczas `import`.
<!--SR:!2025-12-16,3,250-->

Czy `sys.path` przechowuje „listę zainstalowanych pakietów”?
?
Nie. `sys.path` to miejsca do przeszukania; informacje o już załadowanych modułach są w `sys.modules`.
<!--SR:!2025-12-16,2,230-->

Po co jest `sys.modules`?
?
To cache już załadowanych modułów/pakietów; drugi import tej samej nazwy zwykle nie wykonuje kodu ponownie.
<!--SR:!2025-12-17,3,245-->

Co oznacza kropka w `from . import x`?
?
To relative import względem bieżącego pakietu (pakietu modułu), a nie względem aktualnego folderu uruchomienia programu.
<!--SR:!2025-12-16,3,250-->

Kiedy relative import (`from . import x`) zadziała?
?
Gdy moduł jest uruchamiany jako część pakietu (ma ustawione `__package__`), np. przez `python -m pkg.mod` albo normalny import.
<!--SR:!2025-12-17,3,250-->

Dlaczego `python pkg/mod.py` często psuje relative importy?
?
Bo wtedy plik działa jako „skrypt” z `__name__ == "__main__"` i zwykle nie ma poprawnego kontekstu pakietu (`__package__`), więc `from . import ...` nie wie skąd importować.
<!--SR:!2025-12-16,1,185-->

Co robi `python -m pkg.mod`?
?
Uruchamia moduł jako część pakietu, ustawiając poprawnie kontekst importów (m.in. `__package__`), dzięki czemu relative importy działają.
<!--SR:!2025-12-16,2,225-->

Do czego służy `__all__`?
?
Kontroluje, co zostanie zaimportowane przez `from module import *` (nie wpływa na zwykły `import module`).
<!--SR:!2025-12-16,2,230-->

Czy `__all__` „ukrywa” rzeczy przed normalnym importem?
?
Nie. Nadal można importować nazwy bezpośrednio; `__all__` dotyczy głównie `import *`.
<!--SR:!2025-12-16,3,265-->

Czym jest `__path__` w pakiecie?
?
To lista ścieżek, w których Python szuka submodułów danego pakietu (`pkg.something`).
<!--SR:!2025-12-20,5,245-->

Po co istnieje `__path__`?
?
Pozwala pakietowi mieć submoduły w wielu lokalizacjach (ważne m.in. dla namespace packages).
<!--SR:!2025-12-17,2,210-->

Czy folder bez `__init__.py` może być pakietem?
?
Tak, jako namespace package (Python 3.3+), ale wtedy nie masz miejsca na kod inicjalizacyjny w `__init__.py`.
<!--SR:!2025-12-17,3,245-->

---

## 🔗 Powiązane notatki