# Lab 07 - Prepoznavanje in preprecevanje phishing napadov

## Uporabljena orodja
- Social Engineering Toolkit (SET)
- Kali Linux

## Izvedba simulacije

### SET konfiguracija
```
1) Social-Engineering Attacks
2) Website Attack Vectors
3) Credential Harvester Attack Method
2) Site Cloner
```

IP naslov: `192.168.227.129`

### Zajeti podatki
```
[*] WE GOT A HIT! Printing the output:
PARAM: GALX=SJLCkfgaqoM
PARAM: continue=https://accounts.google.com/o/oauth2/auth?...
PARAM: service=lso
POSSIBLE USERNAME FIELD FOUND: Email=Test
POSSIBLE PASSWORD FIELD FOUND: Passwd=Test1234567890_____
PARAM: signIn=Sign+in
PARAM: PersistentCookie=yes
```

### Opomba
Uporabljen je bil vgrajen Google template, ker SET ni hotel klonirati lastne strani.

## Kako prepoznati phishing stran

### Znacilnosti phishing strani
1. **Prirejeni/sumljivi URL naslovi** - posnemajo prave domene (npr. g00gle.com)
2. **Nujnost ali groznje** - "Vas racun bo blokiran v 24 urah"
3. **Vizualno sumljivi obrazci** - cudni fonti, slaba kvaliteta logotipov
4. **HTTP namesto HTTPS** - ni varnostnega certifikata
5. **Po prijavi se ne zgodi nic** - stran ne preusmeri na pravo lokacijo

### Zascita pred phishing napadi
- Preverjanje URL pred vnosom podatkov
- Uporaba 2FA (tudi ce napadalec dobi geslo, ne more dostopati)
- Password manager (avtomatsko izpolnjevanje ne deluje na laznih domenah)
- Phishing filtri v e-posti
- Varnostni trening in ozavescanje

### Zakaj moderne strani otezujejo napade
- **CSP (Content Security Policy)** - preprecuje injiciranje skript
- **HSTS** - zahteva HTTPS
- **2FA/MFA** - dodatna plast avtentikacije
- **Risk-based authentication** - zaznava sumljivih prijav
- **Anti-phishing toolbari** v brskalnikih

## Refleksija

Vaja demonstrira kako enostavno je postaviti lazno prijavno stran in zajemati podatke. Poudarek je na pomenu:
- Preverjanja URL naslovov
- Uporabe 2FA
- Neklikalnja na povezave v sumljivih e-postah

> Opomba: Vaja je izkljucno za izobrazevalne namene. Nikoli ne izvajajte teh tehnik na resnicnih uporabnikih brez njihove vednosti in dovoljenja.
