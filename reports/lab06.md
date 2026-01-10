# Lab 06 - Testiranje varnosti gesel z razbijanjem zgoscenih vrednosti

## Uporabljena orodja
- John the Ripper
- rockyou.txt wordlist

## Testirana gesla

| Geslo | MD5 Hash | Najdeno? | Cas |
|-------|----------|----------|-----|
| Password1 | 2ac9cb7dc02b3c0083eb70898e549b63 | Da | Instant |
| qwerty123 | 3fc0a7acf087f549ac2b266baf94b8b1 | Da | Instant |
| letmein | 0d107d09f5bbe40cade3de5c71e9e9b7 | Da | Instant |
| My$Strong&Pass2024 | - | Ne | - |
| Summer2024 | - | Ne | - |

## Analiza rezultatov

### Najdena gesla (instant)
```
user1:Password1
user2:qwerty123
user4:letmein
```
Vsa tri gesla so bila najdena takoj, ker so v rockyou.txt wordlistu.

### Nenajdena gesla
- **My$Strong&Pass2024** - Ni v wordlistu, vsebuje posebne znake in stevila
- **Summer2024** - Presenetljivo ni bilo najdeno, verjetno rockyou.txt ne vsebuje te kombinacije

## Refleksija

### Kako se povecuje varnost z dolzino?
**Linearno** - vsak dodaten znak eksponentno poveca stevilo moznih kombinacij.

### Kako vplivajo posebni znaki?
**Povecajo varnost** - napadalec mora vkljuciti dodatne znake v nabor za brute force.

### Passphrase vs. klasicno geslo
**Passphrase je boljsi** zaradi dolzine. Npr. "PravilnaKonjBaterija" je mocnejsi od "P@ss1234".

### Priporoceno geslo za vsakodnevno uporabo
Geslo ki je:
- Lahko za zapis in izgovorjavo
- Dolgo vsaj **16 znakov**
- Vsebuje velike in male crke
- Vsebuje vsaj **2 stevili**
- Vsebuje vsaj **2 posebna znaka**

Primer: `Moj-Varni-Racun-2024!`

## Zakljucek

Sibka gesla (password, qwerty, letmein) so v vseh wordlistih in se razbijejo v sekundah. Kompleksna gesla z dolzino 16+ znakov in mesanico tipov znakov so prakticno nerazbijljiva z dictionary napadi.
