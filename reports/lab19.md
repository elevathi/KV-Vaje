# Lab 19 - Preverjanje integritete programske opreme z GPG

## Namen vaje
Demonstracija preverjanja integritete datotek z uporabo SHA256 checksumov in GPG podpisov.

## Koraki vaje

### 1. Ustvarjanje SHA256 checksuma
```bash
sha256sum install.sh > install.sh.sha256
```

### 2. Generiranje GPG kljuca
```bash
gpg --full-generate-key
gpg --list-keys
```

### 3. Podpisovanje checksuma z GPG
```bash
gpg --detach-sign install.sh.sha256
# ali z dolocenim uporabnikom:
gpg --local-user <LOCAL_USER> --detach-sign install.sh.sha256
```

### 4. Preverjanje integritete

**Preverjanje checksuma:**
```bash
sha256sum -c install.sh.sha256
# install.sh: OK
```

**Preverjanje GPG podpisa:**
```bash
gpg --verify install.sh.sha256.sig install.sh.sha256
# gpg: Good signature from ...
```

### 5. Simulacija napada
```bash
# Napadalec spremeni datoteko
echo "echo NAPAD" >> install.sh

# Ponovimo preverjanje
sha256sum -c install.sh.sha256
# install.sh: FAILED
# sha256sum: WARNING: 1 computed checksum did NOT match
```

### 6. Zagon (ce bi bilo preverjanje uspesno)
```bash
./install.sh
```

## Analiza

### Kaj zagotavlja SHA256?
- **Integriteta** - zaznava spremembe v datoteki
- NE zagotavlja avtenticnosti (kdo je ustvaril datoteko)

### Kaj zagotavlja GPG podpis?
- **Avtenticnost** - potrjuje, da je datoteko podpisala oseba z zasebnim kljucem
- **Integriteta** - zaznava spremembe po podpisu

### Postopek varne namestitve programske opreme

1. Prenesi datoteko in checksum
2. Preveri checksum: `sha256sum -c file.sha256`
3. Preveri GPG podpis: `gpg --verify file.sha256.sig`
4. Sele nato zazeni namestitev

## Povzetek

| Mehanizem | Zagotavlja |
|-----------|------------|
| SHA256 checksum | Integriteta |
| GPG podpis | Avtenticnost + integriteta |
| Oba skupaj | Popolna zascita pred manipulacijo |

Kombinacija SHA256 checksumov in GPG podpisov je standardna praksa za distribucijo programske opreme (npr. Linux distribucije, Tor Browser, itd.).
