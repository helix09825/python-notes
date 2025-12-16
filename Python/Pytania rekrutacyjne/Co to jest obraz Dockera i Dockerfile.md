---
sr-due: 2025-12-17
sr-interval: 3
sr-ease: 250
---

 
aliases: []  
tags: [theory, cs, programming]  
sr-due: true
graph: false

#review 
#pytania

---

**❓ Pytanie:**  
Co to jest obraz Dockera i Dockerfile?  
?  
Odpowiedź:  
Obraz Dockera to gotowa “paczka” ze środowiskiem i aplikacją, którą można uruchomić jako kontener.  
Dockerfile to przepis, z którego powstaje obraz — linijka po linijce mówi, co zainstalować, skopiować i uruchomić.

---

**✅ Krótka odpowiedź (na rozmowę, max 3–4 zdania):**

1. **Definicja**  
    Obraz to niezmienny snapshot środowiska, które uruchamiamy jako kontener.  
    Dockerfile to skrypt-instrukcja jak zbudować ten obraz.
    
2. **Po co / kiedy używamy**  
    Używamy, gdy chcemy powtarzalne środowisko: jedna komenda buduje obraz, a potem uruchamiamy go wszędzie tak samo — dev, test, produkcja.
    
3. **Przykład 1 zdanie**  
    Np. piszę Dockerfile z Pythonem i wymaganiami, buduję obraz `myapp:1.0`, a potem startuję kontener `docker run myapp:1.0`.
    

---

**🔑 Keywords (hasła do “zahaczenia”):**  
– obraz = “snapshot, gotowa paczka, niezmienny”  
– Dockerfile = “przepis, instrukcja build”  
– build → run  
– powtarzalność środowiska  
– dev/test/prod ta sama konfiguracja