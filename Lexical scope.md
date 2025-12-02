# ✅ **2. Lexical scope (statyczny zakresem) — to jest klucz**

To odpowiada bezpośrednio na Twój punkt 5.

**Python patrzy na ułożenie kodu w pliku, a nie na to, w jakiej kolejności funkcje są wywoływane.**

To znaczy:

- Funkcja pamięta **gdzie została zdefiniowana**, a nie gdzie została wywołana.
    
- Scope nie „pływa”.
    
- W momencie definiowania funkcji Python ustala drzewo scope’ów.
    

To daje Ci super przewidywalny model:

`Global └── outer     └── inner`

Każde szukanie zmiennej idzie zawsze taką kolejnością:

1. Local
    
2. Enclosing (outer → nonlocal)
    
3. Global (module)
    
4. Builtins (print, len...)