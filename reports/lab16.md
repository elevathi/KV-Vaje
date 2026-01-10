# Lab 16 - Secrets Management z uporabo GPG

## Vprasanja in odgovori

### 1. Zakaj skrivnosti ne sodijo v izvorno kodo?

Varnostna gesla, API kljuci in certifikati ne smejo biti v kodi iz vec kriticnih razlogov:

**Zgodovina verzij:** Tudi ce skrivnost kasneje izbrisete, ostane zapisana v zgodovini (npr. Git history). Vsak, ki ima dostop do repozitorija, jo lahko najde.

**Sirjenje dostopa:** Koda se pogosto kopira na lokalne racunalnike razvijalcev, streznike za testiranje in v oblak. Vec mest kot ima dostop do kode, vecja je verjetnost kraje skrivnosti.

**Tezko rotiranje:** Ce je geslo v kodi, zahteva vsaka sprememba gesla nov "commit", ponovno prevajanje in namestitev aplikacije.

### 2. Razlika med simetricnim in asimetricnim sifriranjem

| Aspekt | Simetricno | Asimetricno |
|--------|-----------|-------------|
| Kljuci | Isti kljuc za sifriranje in desifriranje | Par: javni + zasebni |
| Primer | AES | RSA, GPG |
| Hitrost | Hitro | Pocasnejse |
| Prednost | Ucinkovito | Varnejse za komunikacijo |
| Slabost | Tezava z dostavo kljuca | Vecja racunska zahtevnost |

### 3. Kaj se zgodi, ce izgubimo zasebni kljuc?

Izguba zasebnega kljuca je brez ustrezne priprave **katastrofalna**:

- **Izguba dostopa:** Podatkov, sifriranih s pripadajocim javnim kljucem, ni vec mogoce desifrirati. Postanejo trajno neuporabni.
- **Onemogocen podpis:** Ne morete vec dokazati svoje identitete ali digitalno podpisovati dokumentov/kode.
- **Preklic:** Ce imate pripravljen preklicni certifikat (revocation certificate), lahko javnost obvestite, da kljuc ni vec veljaven.

### 4. Kako bi to resili v vecjem podjetju?

Podjetja uporabljajo profesionalne sisteme:

| Resitev | Opis |
|---------|------|
| **Secrets Management** | HashiCorp Vault, AWS Secrets Manager, Azure Key Vault |
| **HSM** | Hardware Security Module - fizicno varuje kljuce |
| **RBAC** | Role-Based Access Control - omejitev dostopa |
| **Key Escrow** | Varnostne kopije kljucev, razdeljene med vec oseb |

## Prakticni ukazi

### Simetricno sifriranje (z geslom)
```bash
# Sifriranje
gpg -c secrets.env
# Rezultat: secrets.env.gpg

# Desifriranje
gpg secrets.env.gpg
```

### Asimetricno sifriranje (s kljucem)
```bash
# Sifriranje za enega prejemnika
gpg --encrypt --recipient student@example.com secrets.env

# Sifriranje za vec prejemnikov
gpg --encrypt --recipient alice@example.com --recipient bob@example.com secrets.env
```

### Uporaba skrivnosti v aplikaciji
```bash
# Nalozi spremenljivke
source secrets.env
echo $API_KEY

# Po uporabi pocisti
unset API_KEY
unset DB_PASSWORD
```

## Povzetek

- **Secrets management** je kljucni del kibernetske varnosti
- **GPG** omogoca osnovno, a ucinkovito zascito skrivnosti
- V praksi se uporabljajo orodja kot so Vault, SOPS, AWS Secrets Manager
- Skrivnosti **nikoli** ne sodijo v izvorno kodo ali repozitorije
