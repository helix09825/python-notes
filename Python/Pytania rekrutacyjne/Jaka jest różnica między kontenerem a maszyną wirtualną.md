
aliases: []  
tags: [theory, cs, programming]  
sr-due: true
graph: false

#review 
#pytania

---



**❓ Pytanie:**  
Jaka jest różnica między kontenerem a maszyną wirtualną?  
?  
Kontener współdzieli kernel systemu operacyjnego z hostem i jest “lżejszy”, a maszyna wirtualna emuluje cały sprzęt i uruchamia pełny system operacyjny w środku. VM daje mocniejszą izolację, ale jest cięższa i wolniej się uruchamia.

---

**✅ Krótka odpowiedź (na rozmowę, max 3–4 zdania):**

1. **Definicja**  
    Kontener to odizolowane środowisko uruchomieniowe współdzielące kernel z hostem.  
    Maszyna wirtualna to pełny system operacyjny działający na wirtualizowanym sprzęcie.
    
2. **Po co / kiedy używamy**  
    Kontenery – gdy chcemy szybko i lekko pakować aplikacje z zależnościami, skalować mikroserwisy, dev/stage/prod.  
    VM – gdy potrzebujemy mocnej izolacji, różnych systemów operacyjnych lub “całej maszyny” pod aplikację.
    
3. **Przykład 1 zdanie**  
    Np. aplikację webową w mikroserwisach uruchamiamy w kontenerach Docker, a bazę danych klienta trzymamy na osobnej maszynie wirtualnej z dedykowanym systemem i zasobami.
    

---

**🔑 Keywords (hasła do “zahaczenia”):**  
– współdzielenie kernel vs pełny OS  
– lekkość / szybkość startu vs ciężar / overhead  
– poziom izolacji / bezpieczeństwo  
– scenariusze: mikroserwisy / dev vs różne OS / legacy apps

![[Pasted image 20251210203410.png]]# **Walizka vs Kamper**

### 🧳 **KONTENER = Walizka**

- Lekki
    
- Łatwo spakować
    
- Wkładasz tylko to, co potrzebujesz
    
- Korzystasz z tego, co już istnieje wokół (czyli **współdzielisz “dom” — kernel**)
    

> Wchodzisz do hotelu → rozkładasz ubrania z walizki → gotowe.  
> Nie budujesz całego domu od nowa, po prostu **minimum potrzebne do działania**.

---

### 🚐 **MASZYNA WIRTUALNA = Kamper**

- Ma wszystko ze sobą: kuchnię, łazienkę, łóżko
    
- **Nie potrzebuje niczego od hotelu**
    
- Cięższy, wolniejszy, ale daje **pełną izolację**
    

> Jedziesz kamperem → ustawiasz na parkingu → możesz żyć **niezależnie od świata**.