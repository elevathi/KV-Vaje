Enako Lab12.
# Lab 12 - Priprava varnostne politike

## Aktivnost 1: Analiza obstojece politike UL

Analizirana je bila Krovna politika informacijske varnosti Univerze v Ljubljani (podrobna analiza v [lab18.md](lab18.md)).

### Kljucne ugotovitve iz analize UL politike

| Kriterij | Ocena | Komentar |
|----------|-------|----------|
| Struktura | 4/5 | Logicna, skladna z ISO 27001 |
| Pokritost grozenj | 3/5 | Splosno dobro, manjkajo specifike |
| Jasnost jezika | 2/5 | Prevec birokratski |
| Prakticna uporabnost | 2/5 | Premalo konkretnih primerov |

**Glavne pomanjkljivosti za manjsa podjetja:**
- Prevec formalen in birokratski jezik
- Primanjkujejo konkretni primeri
- Ni vizualnih elementov
- Ne omenja sodobnih grozenj (phishing, ransomware)

---

## Aktivnost 2: Varnostna politika za podjetje s 50 zaposlenimi

### Opis podjetja

| Podatek | Vrednost |
|---------|----------|
| Dejavnost | Spletna trgovina (e-commerce) |
| Stevilo zaposlenih | 50 |
| IT infrastruktura | Cloud (AWS/Azure), lokalna pisarna |
| Obcutljivi podatki | Osebni podatki strank, placilni podatki |

---

## Predlog varnostne politike

### 1. Namen in cilji

**Namen:** Zascita informacijskih sredstev podjetja, podatkov strank in zagotavljanje neprekinjenega poslovanja.

**Cilji:**
- Zagotoviti zaupnost, celovitost in razpolozljivost podatkov
- Zascititi osebne podatke strank (skladnost z GDPR)
- Prepreciti financne izgube zaradi kibernetskih napadov
- Vzpostaviti kulturo varnostnega zavedanja

### 2. Podrocje uporabe

Politika velja za:
- Vse zaposlene (redno in pogodbeno)
- Vse informacijske sisteme in naprave
- Vse lokacije (pisarna, delo od doma)
- Vse zunanje izvajalce z dostopom do sistemov

### 3. Odgovornosti

| Vloga | Odgovornosti |
|-------|--------------|
| **Vodstvo** | Odobritev politike, zagotavljanje virov, strateske odlocitve |
| **IT skrbnik** | Tehnicna implementacija, nadzor, odziv na incidente |
| **Vodje oddelkov** | Nadzor skladnosti v oddelku, porocanje |
| **Vsi zaposleni** | Upostevanje pravil, javljanje incidentov |

### 4. Pravila za uporabo sistemov

#### Gesla
- Minimalno **12 znakov**, vsaj 1 velika crka, 1 stevilka, 1 poseben znak
- Menjava vsakih **90 dni**
- Uporaba **password managerja** (npr. Bitwarden)
- **2FA obvezno** za vse kriticne sisteme

#### Elektronska posta
- Ne odpirati prilog od neznanih posiljateljev
- Preverjati URL naslove pred klikom
- Sumljiva sporocila takoj prijaviti IT

#### Delovne postaje
- Samodejno zaklepanje po **5 minutah** neaktivnosti
- Sifrirani diski (BitLocker/FileVault)
- Samo odobrena programska oprema
- Samodejne posodobitve omogocene

#### Delo od doma
- Obvezna uporaba **VPN**
- Prepoved uporabe javnih WiFi omrezij brez VPN
- Locitev sluzbenega in zasebnega dela

### 5. Postopki ob incidentih

```
KORAK 1: ZAZNAVA
    └── Zaposleni opazi sumljivo aktivnost

KORAK 2: PRIJAVA (takoj!)
    └── E-mail: security@podjetje.si
    └── Telefon: interna 100

KORAK 3: IZOLACIJA
    └── IT skrbnik izolira prizadeti sistem

KORAK 4: ANALIZA
    └── Preiskava obsega in vzroka

KORAK 5: SANACIJA
    └── Odstranitev groznje, obnovitev

KORAK 6: POROCILO
    └── Dokumentacija, ukrepi za preprecevanje
```

**Primeri incidentov:**
- Phishing e-mail (klik na zlonamerno povezavo)
- Ransomware okuzba
- Izguba/kraja naprave
- Nepooblascen dostop do podatkov

### 6. Klasifikacija podatkov

| Kategorija | Primeri | Ukrepi |
|------------|---------|--------|
| **JAVNO** | Marketing materiali, cenik | Ni omejitev |
| **INTERNO** | Interni postopki, sestanki | Samo zaposleni |
| **ZAUPNO** | Financni podatki, pogodbe | Omejen dostop, sifriranje |
| **STROGO ZAUPNO** | Placilni podatki strank, gesla | Sifriranje, 2FA, revizijska sled |

### 7. Fizicna varnost

- Dostop do pisarne s kartico/PIN
- Cista miza (clean desk policy)
- Zaklepanje predalov z dokumenti
- Obiskovalci vedno v spremstvu

### 8. Izobraževanje

| Aktivnost | Pogostost |
|-----------|-----------|
| Osnovno varnostno usposabljanje | Ob zaposlitvi |
| Osvezitev znanja | Letno |
| Phishing simulacije | 2x letno |
| Obvestila o novih groznjah | Sproti |

### 9. Skladnost in nadzor

- **Letni pregled** varnostne politike
- **Kvartalni** pregled dostopnih pravic
- **Mesecno** preverjanje posodobitev sistemov
- **Revizija** ob vecjih spremembah

### 10. Sankcije

Krsitev varnostne politike lahko pomeni:
- Opomin
- Disciplinski postopek
- Prekinitev delovnega razmerja (hujse krsitve)
- Odskodninska odgovornost

---

## Komunikacija zaposlenim

### Priporoceni pristopi

1. **Kratka verzija (1 stran)**
   - DOs in DON'Ts format
   - Vizualno privlacna
   - Na vidnem mestu v pisarni

2. **E-learning modul**
   - Interaktiven, 30 minut
   - Obvezen za vse zaposlene
   - Test na koncu

3. **Periodicna opominjanja**
   - Mesecni e-mail nasveti
   - Slack/Teams kanal za varnost

4. **Prakticne vaje**
   - Phishing simulacije
   - "Kaj bi naredili, ce..." scenariji

---

## Kratka verzija za zaposlene

### NAREDI (DOs)

- Uporabljaj mocna gesla (12+ znakov) in password manager
- Omogoci 2FA povsod, kjer je mozno
- Zakleni racunalnik, ko zapustis delovno mesto (Win+L)
- Preveri posiljatelja, preden kliknes na povezavo
- Prijavi sumljive e-maile na security@podjetje.si
- Shranjuj podatke samo na odobrene lokacije (cloud, ne USB)
- Posodabljaj programsko opremo

### NE NAREDI (DON'Ts)

- Ne deli gesel s kolegi
- Ne odpiri prilog od neznanih posiljateljev
- Ne prikljucuj neznanih USB naprav
- Ne uporabljaj javnega WiFi brez VPN
- Ne shranuj gesel v brskalnik ali besedilne datoteke
- Ne ignorira varnostnih opozoril

### OB INCIDENTU

1. **USTAVI** - ne nadaljuj z delom
2. **PRIJAVI** - security@podjetje.si ali int. 100
3. **POCAKAJ** - ne izkljucuj racunalnika, ne brisi dokazov

---

## Zakljucek

Ta varnostna politika je prilagojena za manjse podjetje (50 zaposlenih) in uposteva:
- Prakticnost in razumljivost
- Omejene vire za IT varnost
- Potrebo po hitri implementaciji
- Skladnost z GDPR

Za razliko od UL politike je poudarek na **konkretnih pravilih** in **razumljivem jeziku** za zaposlene brez tehnicnega znanja.
