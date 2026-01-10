# Lab 17 - Analiza varnostnih grozenj in ranljivosti

> **Opomba:** Porocilo za to vajo ni bilo oddano.

## Povzetek naloge

### Cilji
- Razumeti najpogostejse vrste ranljivosti spletnih aplikacij
- Spoznati OWASP Top 10 v kontekstu e-poslovanja
- Prepoznati ranljivosti in razpravljati o njihovih posledicah

## Uporabljeno orodje
**HostedScan OWASP Vulnerability Scan**
https://hostedscan.com/owasp-vulnerability-scan

## OWASP Top 10 (2021)

| # | Ranljivost | Opis |
|---|------------|------|
| 1 | Broken Access Control | Neustrezna kontrola dostopa |
| 2 | Cryptographic Failures | Napake v kriptografiji |
| 3 | Injection | SQL, NoSQL, OS command injection |
| 4 | Insecure Design | Napake v zasnovi aplikacije |
| 5 | Security Misconfiguration | Napacne varnostne nastavitve |
| 6 | Vulnerable Components | Zastarele/ranljive komponente |
| 7 | Authentication Failures | Napake pri avtentikaciji |
| 8 | Software Integrity Failures | Napake v integriteti programske opreme |
| 9 | Logging/Monitoring Failures | Pomanjkljivo belezenje in nadzor |
| 10 | SSRF | Server-Side Request Forgery |

## Navodila za porocilo

Za vsako zaznano ranljivost zapisite:
1. Ime ranljivosti
2. Ocena resnosti (nizka, srednja, visoka)
3. Kratko pojasnilo, zakaj je nevarna
4. Kako bi jo odpravili

## TODO
- [ ] Izvesti pregled testne spletne strani
- [ ] Prenesti porocilo (PDF ali HTML)
- [ ] Analizirati rezultate
- [ ] Dokumentirati vsaj 3 zaznane ranljivosti

> **Opozorilo:** Pregledujte samo pripravljene testne spletne strani - ne izvajajte pregledov na tujih produkcijskih sistemih brez dovoljenja!
