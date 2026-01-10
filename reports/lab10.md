# Lab 10 - CTF vaja: HackyCorp

## Najdene zastavice

### 1. Odkrivanje ranljivosti iz znanih URL naslovov

| Izziv | URL/Metoda | Zastavica |
|-------|------------|-----------|
| /admin | `https://hackycorp.com/admin` | `ad1d44d6-ab73-4640-8291-c5bf2343e2a5` |
| /key.txt | `https://hackycorp.com/key.txt` | `aeaee57f-2a82-41da-bc4c-d081c8cddfc8` |

### 2. Odkrivanje ranljivosti v Javascript datotekah

| Izziv | Lokacija | Zastavica |
|-------|----------|-----------|
| recon_26 | Hardcoded key v JS | `d6b75269-97a3-44de-be32-fff0dd55e7ef` |

### 3. Odkrivanje ranljivosti na spletnem strezniku

| Izziv | Ukaz | Zastavica |
|-------|------|-----------|
| HTTP Headers | `curl -I https://hackycorp.com/` | `99d0738b-1e52-4a00-8885-b15894b2c79e` |
| robots.txt | `curl https://hackycorp.com/robots.txt` | `af9c328a-02b4-439d-91c6-f46ab4a0835b` |
| security.txt | `curl https://hackycorp.com/.well-known/security.txt` | `99685e30-7061-4ac0-83bf-4ccc0409faac` |
| 404 Error | `curl -I https://hackycorp.com/neobstaja` | `99d0738b-1e52-4a00-8885-b15894b2c79e` |

### 4. Odkrivanje ranljivosti preko IP naslova

| Izziv | Ukaz | Zastavica |
|-------|------|-----------|
| recon_06 | `curl --insecure http://IP_STREZNIKA` | `5cf83b5d-eb6c-4eee-af6c-945f9aed8dfd` |
| Dodaten kljuc | - | `80cb2045-c8bf-4357-8931-a28dd0f3fbb9` |

### 5. Odkrivanje ranljivosti v Github repozitorijih

| Repo | Metoda | Zastavica |
|------|--------|-----------|
| repo3 | Pregled vej (branches) | `08be82ba-e5fd-4fae-b2c2-272a18d31f80` |
| repo4 (recon_21) | Datoteka v drugi veji | `a60b4aee-642a-483b-9262-ccfc2ed46f0d` |
| repo9 (recon_22) | `git log --diff-filter=D --summary` | `3ee505c2-8aa9-4d5e-810e-921778dce1e6` |
| repo0a (recon_23) | `git log --oneline --grep=key -i` | `5c75cfe9-52dd-475b-8cfa-7ffc492abeca` |

### 6. Odkrivanje ranljivosti v DNS zapisih

| Izziv | Ukaz | Zastavica |
|-------|------|-----------|
| TXT zapis | `dig key.z.hackycorp.com TXT` | `9f883f22-6ea5-4631-bbe8-95841ad63f56` |
| Zone Transfer (recon_14) | `dig AXFR z.hackycorp.com` | `e5fce970-6d94-43c1-bdd5-a06c2b235f9c` |
| VERSION.BIND | `dig -c chaos -t txt VERSION.BIND @z.hackycorp.com` | `4e5e76e1-728a-49be-aea8-4591ba11e588` |

### 7. Skriptno programiranje - Brute force

```bash
# Generiranje hosts.txt
for i in `seq 1 150`; do
    printf "0x%02x.a.hackycorp.com\n" $i >> hosts.txt
done

# Prenos slik
for i in `cat hosts.txt`; do
    curl $i/logo.png -o $i.png
done
```

Najden: `http://0x81.a.hackycorp.com/`

## Povzetek

Skupaj najdenih **14+ zastavic** z uporabo razlicnih tehnik:
- URL enumeration
- JavaScript analiza
- HTTP header pregled
- Git repository analiza
- DNS reconnaissance
- Brute force scripting
