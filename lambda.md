Jest to anonimowa funkcja, która przyjmuje dowolną liczbę argumentów, ale może mieć tylko jedno wyrażenie.

```python
sum = lambda a, b: a + b
double = lambda x: x * 2
```

Funkcji lambda możemy też użyć jako parametru w innej funkcji:
```python
add = lambda x: x + 2
subtract = lambda x: x - 2 
double = lambda x: x * 2
divided = lambda x: x / 2
 
def calculate(operation, number):
	return operation(number)
 
calculate(add, 10)		# 12
calculate(subtract, 10)	# 8
calculate(double, 10)		# 20
calculate(divided, 10)		# 5
```

