aliases: []  
tags: [theory, cs, programming]  
sr-due: true
graph: false

#review 

---

## 🧠 Co to jest?
**Polimorfizm** to mechanizm programowania obiektowego, który pozwala traktować różne obiekty w jednolity sposób, ponieważ **to samo wywołanie metody może mieć różne implementacje w zależności od typu obiektu**.  W Pythonie polimorfizm nie wynika z hierarchii klas, ale z zachowania obiektów.

## 🔧 Jak to działa? 

Ta sama metoda może oznaczać różne zachowanie — wszystko zależy od obiektu, który ją wykonuje.

## 🧪 Przykład

```python
class Animal: 
	def __init__(self, name): 
		self.name
	
	def voice(self): 
		return f"{self.name} make a voice"
		

class Dog(Animal):
	def voice(self):
		return f"{self.name} barks"
		
```

---

## 🧩 Mnemotechniki

### 🅰 Akronim

**Akronim:** TORI

**Rozwinięcie:**

- T — to samo wywołanie
    
- O — objekt decyduje
    
- R — runtime
    
- I — Interfejs

---

### 🔄 Tłumaczenie jako analogia

**Analogia:** 
Wyobraź sobie **wielki ośrodek ekspedycyjny**, który korzysta z różnych środków transportu — **statków i samochodów**.  
Każdy z nich potrafi **wysyłać ładunek** (`send`), ale **każdy robi to na swój sposób**.

Dla ośrodka nie ma znaczenia, czy wysyła statek czy samochód — **zawsze wywołuje tę samą komendę `send`**, a konkretne wykonanie zależy od pojazdu.

---

### 🗃 Keyword Connections (powiązania)

- [[OOP]]
    
- [[duck typing]]
    

---

### 🖼 Rysunek / schemat / diagram ASCII

![[Pasted image 20260121193335.png]]

---

## ✨ Metoda Feynmana (1–2 zdania)

Wiele obiektów w naszym otoczeniu może wykonywać tę samą czynność, ale każdy robi to na swój własny sposób.  
Na przykład **rower, samochód i pociąg** potrafią _jechać_, jednak każdy z nich realizuje tę czynność inaczej — i dokładnie na tym polega polimorfizm.

---

## ⚠ Typowe błędne wyobrażenie

Polimorfizm nie polega na tym, że metody mają tę samą nazwę, tylko na tym, że obiekty są używane zamiennie przez wspólny interfejs.

---

## 🗂 Fiszki (SRS) #flashcards 


Czy dwie metody o tej samej nazwie zawsze oznaczają polimorfizm?  
?  
Nie — polimorfizm wymaga **wspólnego kontekstu użycia i zamienności obiektów**, nie tylko tej samej nazwy.

---

Co decyduje o tym, która implementacja metody zostanie wykonana?  
?  
**Rzeczywisty obiekt w runtime**, a nie nazwa zmiennej ani klasa bazowa.

---

Czy polimorfizm polega na sprawdzaniu typu obiektu (`if isinstance`)?  
?  
Nie — sprawdzanie typu **łamie polimorfizm**, zamiast z niego korzystać.

---

Dlaczego interfejs jest ważniejszy niż implementacja w polimorfizmie?  
?  
Bo **kod wywołujący komunikuje się przez zachowanie**, a nie przez konkretną klasę.

---

Jak rozpoznać prawdziwy polimorfizm jednym pytaniem?  
?  
Czy **te same wywołanie** działa na **różnych obiektach**, bez zmiany kodu wywołującego?


---

## 🔗 Powiązane notatki