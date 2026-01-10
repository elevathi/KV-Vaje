# Lab 14 - GPG: ustvarjanje kljucev, sifriranje in podpisovanje

## Generiranje GPG para kljucev

```bash
gpg --full-generate-key
```

### Izbrane nastavitve
- **Tip kljuca:** RSA and RSA
- **Velikost:** 4096 bitov
- **Veljavnost:** 1 leto
- **Ime:** Student Gregor
- **Email:** student@example.com

### Rezultat
```
pub   rsa4096 2026-01-04 [SC] [expires: 2027-01-04]
      495ECCFE96D209164F08FD6096FB24DE993F5EC8
uid                      Student Gregor <student@example.com>
sub   rsa4096 2026-01-04 [E] [expires: 2027-01-04]
```

## Pregled kljucev

```bash
gpg --list-keys
```

```
/home/kali/.gnupg/pubring.kbx
-----------------------------
pub   rsa4096 2026-01-04 [SC] [expires: 2027-01-04]
      495ECCFE96D209164F08FD6096FB24DE993F5EC8
uid           [ultimate] Student Gregor <student@example.com>
sub   rsa4096 2026-01-04 [E] [expires: 2027-01-04]
```

## Izvoz javnega kljuca

```bash
gpg --armor --export student@example.com > student_pubkey.asc
```

## Sifriranje in podpis

```bash
gpg --encrypt --sign --armor --recipient peer@example.com message.txt
```

## Desifriranje

```bash
gpg --decrypt message.txt.asc > decrypted_message.txt
```

## Vprasanja in odgovori

### 1. Razlika med sifriranjem in podpisom

| Aspekt | Sifriranje | Digitalni podpis |
|--------|-----------|------------------|
| Namen | Zaupnost | Avtenticnost in celovitost |
| Delovanje | Spremeni v necitljivo obliko | Dokaze izvor in nespremenjenost |
| Kdo lahko bere | Samo imetnik kljuca | Vsi lahko preverijo |

### 2. Vloga javnega in zasebnega kljuca

| Kljuc | Uporaba |
|-------|---------|
| **Javni** | Sifriranje podatkov za lastnika, preverjanje podpisa |
| **Zasebni** | Desifriranje prejetih sporocil, ustvarjanje podpisa |

> **Pomembno:** Zasebni kljuc mora ostati tajen!

### 3. Kaj se zgodi ob spremembi sifrirane datoteke?

1. **Desifriranje neuspesno** - algoritmi zaznajo napako in zavrnejo desifriranje
2. **Poskodovani podatki** - ce bi desifriranje izvedli, bi dobili nesmiselne podatke ("garbage data")
3. **Neveljaven podpis** - ce je bila datoteka tudi podpisana, podpis postane neveljaven

## Povzetek

- **Sifriranje** zagotavlja zaupnost
- **Digitalni podpis** zagotavlja avtenticnost in integriteto
- **GPG** uporablja asimetricno kriptografijo (RSA)
