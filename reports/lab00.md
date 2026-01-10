# Lab 00 - Uvod v Linux: osnove dela v ukazni lupini

## Naloga 1: Krmarjenje po sistemu
Premik v domači imenik, ustvarjanje mape in vstop vanjo:
```bash
cd                    # premik v domači imenik
mkdir linux-vaja      # ustvarjanje imenika
cd linux-vaja         # vstop v imenik
```

## Naloga 2: Delo z datotekami in imeniki
Ustvarjanje datoteke, zapis vsebine, ustvarjanje imenika in premik datoteke:
```bash
touch opis.txt            # ustvarjanje prazne datoteke
echo Gregor > opis.txt    # zapis imena v datoteko
mkdir testni              # ustvarjanje imenika
mv opis.txt testni        # premik datoteke v imenik
```

## Naloga 3: Premikanje in kopiranje
Preimenovanje datoteke in kopiranje v domačo mapo:
```bash
cd testni
mv opis.txt moj_profil.txt           # preimenovanje
cp moj_profil.txt ~/moj_profil.txt   # kopiranje v domačo mapo
```

## Naloga 4: Pravice in velikosti
Preverjanje velikosti in spreminjanje pravic:
```bash
ls -lh                      # prikaz velikosti in pravic
chmod 444 moj_profil.txt    # samo branje za vse (r--r--r--)
```
> Opomba: `chmod 644` omogoča pisanje lastniku, `chmod 444` je samo za branje za vse.

## Naloga 5: Prikaz sistemskih informacij
```bash
whoami      # izpis uporabniškega imena
cd          # premik v domači imenik
ls -lh      # velikost domačega imenika
df -h       # prikaz prostora na disku
```

## Dodatna naloga
Iskanje 5 največjih datotek v domačem imeniku:
```bash
du -ah ~ | sort -rh | head -n 5
```
