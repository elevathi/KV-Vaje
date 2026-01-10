# Lab 05 - Socialni inzeniring in obramba pred njim

## Analiza phishing primerov

### Primer 1: E-postno sporocilo za prevzem paketa
**Pošiljatelj:** dostava@postapaket.xyz

**Sumljivi znaki:**
- **.xyz domena** - neobicajna za uradno posto
- **.ru domena** v povezavi - ruski streznik
- **http protokol** - ni HTTPS
- **Casovna nujnost** - "v naslednjih 24 urah"
- Podpis brez uradnih podatkov/slike

### Primer 2: E-postno sporocilo glede deaktivacije racuna
**Pošiljatelj:** varnost@bankaa-si.com

**Sumljivi znaki:**
- Lazna domena (bankaa-si.com namesto uradne)
- **Nujnost** - "v naslednjih 12 urah"
- "Kliknite tukaj" brez prikaza dejanske povezave
- Banke nikoli ne zahtevajo podatkov po e-posti

### Primer 3: E-postno sporocilo glede nagrade
**Pošiljatelj:** nagrade@promocije.win

**Sumljivi znaki:**
- Cuden link (.biz domena)
- **Placilo dostave** za "brezplacno" nagrado
- Razlicne domene v sporocilu
- Tipicna "too good to be true" taktika

## Preverjanje phishing sporocil

Vecina spama prihaja preko Amazon SES streznika, zato so SPF/DKIM/DMARC preverilnice pogosto pravilne. Potrebno je rocno filtriranje.

## Lastni phishing primer (izobrazevalni namen)

```
Od: podpora@nova-lkb.si (lazna domena)
Zadeva: Nujna varnostna posodobitev vasega racuna

[LKB logotip]

Spostovani Borut,

Nas varnostni sistem je zaznal sumljivo aktivnost na vasem racunu.
Zaradi zascite vasih sredstev smo zacasno omejili dostop.

Za ponovno aktivacijo racuna prosimo potrdite svojo identiteto
v naslednjih 24 urah, sicer bo racun trajno blokiran.

> Potrdi identiteto

Potrebovali bomo:
- Uporabnisko ime
- Geslo za spletno banko
- Telefonsko stevilko za verifikacijo

Lep pozdrav,
Tehnicna podpora LKB
Tel: 01 234 5678
```

**Uporabljeni psihološki vzvodi:**
- Strah (sumljiva aktivnost, blokada racuna)
- Nujnost (24 ur)
- Avtoriteta (videz uradne banke)
- Personalizacija (ime prejemnika)

## Refleksija

### Kako hitro opazite sumljivost?
Takoj ko zahtevajo uporabnisko ime in geslo po e-posti.

### Bi lahko vsako sporocilo prepoznali kot nevarno brez headerja?
Da, z izkusnjami postanejo sumljivi znaki ocitni.

### Nasvet za novega uporabnika
Ce ni prepri�an glede sporocila:
1. Nikoli ne klikaj na povezave v sporocilu
2. Obisci uradno spletno stran neposredno
3. Kontaktiraj podporo po uradnih kanalih
4. Obisci fizicno lokacijo (banka, posta)
5. Ko dvomis - vprasaj koga z vec izkusnjami
