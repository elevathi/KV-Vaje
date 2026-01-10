# Lab 11 - OverTheWire Bandit CTF

Bandit je zacetni CTF izziv za ucenje Linux ukazov in varnosti.
Server: `bandit.labs.overthewire.org`, port: `2220`

## Level 0
```bash
ssh bandit0@bandit.labs.overthewire.org -p 2220
# password: bandit0
ls
cat readme
# password za level 1: ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If
```

## Level 1
Datoteka z imenom `-` (posebni znak).
```bash
ssh bandit1@bandit.labs.overthewire.org -p 2220
cat ./-
# password: 263JGJPfgU6LtdEvgfWU1XP5yac29mFx
```

## Level 2
Datoteka s presledki v imenu.
```bash
ssh bandit2@bandit.labs.overthewire.org -p 2220
cat "spaces in this filename"
# password: MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx
```

## Level 3
Skrita datoteka (zacne se s piko).
```bash
ssh bandit3@bandit.labs.overthewire.org -p 2220
cd inhere
ls -la
cat ...Hiding-From-You
# password: 2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ
```

## Level 4
Najdi berljivo datoteko med vec datotekami.
```bash
ssh bandit4@bandit.labs.overthewire.org -p 2220
file ./-file*
cat ./-file07
# password: 4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw
```

## Level 5
Poisci datoteko z doloceno velikostjo (1033 bajtov).
```bash
ssh bandit5@bandit.labs.overthewire.org -p 2220
find . -size 1033c
cat ./maybehere07/.file2
# password: HWasnPhtq9AVKe0dmk45nxy20cvUa6EG
```

## Level 6
Poisci datoteko po lastniku in skupini.
```bash
ssh bandit6@bandit.labs.overthewire.org -p 2220
find / -user bandit7 -group bandit6 2>/dev/null
cat /var/lib/dpkg/info/bandit7.password
# password: morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj
```

## Level 7
Poisci vrstico z doloceno besedo v datoteki.
```bash
ssh bandit7@bandit.labs.overthewire.org -p 2220
cat data.txt | grep millionth
# password: dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc
```

## Level 8
Poisci unikatno vrstico (pojavi se samo enkrat).
```bash
ssh bandit8@bandit.labs.overthewire.org -p 2220
sort data.txt | uniq -u
# password: 4CKMh1JI91bUIZZPXDqGanal4xvAg0JM
```

## Level 9
Izvleci berljive nize iz binarne datoteke.
```bash
ssh bandit9@bandit.labs.overthewire.org -p 2220
strings data.txt | grep "="
# password: FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey
```

## Level 10
Dekodiraj base64 kodiran tekst.
```bash
ssh bandit10@bandit.labs.overthewire.org -p 2220
base64 -d data.txt
# password: dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr
```

## Level 11
Dekodiraj ROT13 kodiran tekst.
```bash
ssh bandit11@bandit.labs.overthewire.org -p 2220
tr 'A-Za-z' 'N-ZA-Mn-za-m' < data.txt
# password: 7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4
```

## Povzetek naucenih tehnik

| Level | Tehnika |
|-------|---------|
| 0 | Osnovna uporaba SSH in cat |
| 1 | Delo s posebnimi imeni datotek |
| 2 | Escape presledkov v imenih |
| 3 | Prikaz skritih datotek (ls -la) |
| 4 | Uporaba file za identifikacijo tipov |
| 5-6 | Napredna uporaba find |
| 7 | grep za iskanje v datotekah |
| 8 | sort in uniq za analizo |
| 9 | strings za binarno analizo |
| 10 | base64 dekodiranje |
| 11 | ROT13 dekodiranje |
