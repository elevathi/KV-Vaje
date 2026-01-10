# Lab 13 - Projektna naloga: Zunanji varnostni kibernetski pregled

> **Status:** Projektna naloga oddana na Moodle (januar 2026)

## Osnovni podatki

| Podatek | Vrednost |
|---------|----------|
| Organizacija | Premogovnik Velenje d.o.o. |
| Vrsta pregleda | Zunanji varnostni kibernetski pregled |
| Datum pregleda | 6. - 10. januar 2026 |
| Izvajalec | Gregor Klinc |
| Obseg strani | 48 strani |

## Povzetek

Zunanji varnostni kibernetski pregled organizacije Premogovnik Velenje d.o.o., ki se ukvarja z izkopom premoga. Pregled je bil izveden z namenom identifikacije potencialnih varnostnih ranljivosti in priprave priporocil za izboljsanje kibernetske varnosti.

## Metodologija

### Pristop
- OSINT (Open Source Intelligence) preiskava
- Skeniranje omrezja in storitev
- Analiza SSL/TLS konfiguracij
- Pregled DNS zapisov
- Testiranje e-postnih streznikov

### Uporabljena orodja
1. **Nmap** - skeniranje odprtih vrat in storitev
2. **SSL Labs** - analiza SSL/TLS konfiguracij
3. **MXToolbox** - pregled DNS in e-postnih nastavitev
4. **WHOIS** - pregled domenskih podatkov
5. **Shodan** - pregled javno dostopnih naprav
6. **Have I Been Pwned** - preverjanje uhajanja podatkov

## Identificirana sredstva

### Infrastruktura
- Glavni spletni streznik (rlv.si)
- E-postni streznik
- VPN dostop
- Interna omrezna infrastruktura

### Digitalna prisotnost
- Glavna domena: rlv.si
- Poddomena: www.rlv.si
- E-postna infrastruktura

## Kljucne ugotovitve

### Pozitivno
- SSL certifikat pravilno konfiguriran
- Osnovne varnostne nastavitve prisotne
- SPF zapisi konfigurirani

### Ranljivosti in pomanjkljivosti
1. **Zastarele programske komponente** - nekateri sistemi potrebujejo posodobitve
2. **E-postna varnost** - moznost izboljsav DMARC politik
3. **Odprta vrata** - nekaj nepotrebno odprtih storitev
4. **Informacijsko razkrivanje** - pretirano razkrivanje tehnicnih podrobnosti

## Ocena tveganja

| Kategorija | Stopnja tveganja |
|------------|------------------|
| Zunanja izpostavljenost | Srednja |
| E-postna varnost | Srednja |
| SSL/TLS konfiguracija | Nizka |
| Upravljanje posodobitev | Srednja-Visoka |

## Priporocila

### Takojsnji ukrepi
1. Posodobitev zastarelih sistemov
2. Zapiranje nepotrebnih vrat in storitev
3. Implementacija strozjih DMARC politik

### Srednjerocni ukrepi
1. Redno skeniranje ranljivosti
2. Implementacija WAF (Web Application Firewall)
3. Izboljsanje nadzora in belezenja

### Dolgorocni ukrepi
1. Vzpostavitev programa za upravljanje ranljivosti
2. Redno izvajanje penetracijskih testov
3. Usposabljanje zaposlenih o kibernetski varnosti

## Zakljucek

Pregled je pokazal, da organizacija Premogovnik Velenje ima vzpostavljene osnovne varnostne mehanizme, vendar obstaja prostor za izboljsave. Priporoceno je redno izvajanje varnostnih pregledov in takojsnja implementacija predlaganih ukrepov.

## Priloge

Podrobno porocilo s posnetki zaslona in tehnicnimi podrobnostmi je prilozeno v PDF dokumentu, oddanem na Moodle.

---

*Porocilo pripravljeno v okviru predmeta Kibernetska varnost*
