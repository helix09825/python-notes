```python
from functools import wraps

def decorator_func(func):
    """Decorator doc-string"""
    @wraps(func)
    def wrapper(*args, **kwargs):
        func(*args, **kwargs)
    return wrapper
 
 
@decorator_func
def some_func(arg):
    """Function doc-string"""
    pass

print(some_func.__name__)  # some_func
print(some_func.__doc__)  # Function doc-string

```


## 🗂 Fiszki (SRS) #flashcards 

Czym możemy rozwiązać problem` __name__` oraz `__doc__` w dekoratorach
?  
Za pomocą `from functools import wraps` `@wraps(func)`

Co zrobi `from functools import wraps`
?
Functools wraps zaktualizuje dekorator o atrybuty dekorowanej funkcji 