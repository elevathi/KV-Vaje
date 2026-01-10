# Lab 08 - Uporaba varne komunikacije

## Uporabljeni strezniki
- **MailHog** - SMTP testni streznik brez TLS (port 1025)
- **Postfix** - SMTP streznik s STARTTLS (port 587)

## Simulacija ranljivosti - Nesifriran SMTP

### Zajet prometa
```bash
sudo tcpdump -i any tcp port 1025 -w smtp.pcap &
swaks --server 127.0.0.1 --port 1025 \
  --from ti@example.com --to test@example.com \
  --data "Subject: Codespace SWAKS Test\n\nPozdrav iz FIS!"
```

### Zajeti cleartext promet
```
220 mailhog.example ESMTP MailHog
EHLO codespaces-1fbaf2
250-Hello codespaces-1fbaf2
250-PIPELINING
250 AUTH PLAIN
MAIL FROM:<ti@example.com>
250 Sender ti@example.com ok
RCPT TO:<test@example.com>
250 Recipient test@example.com ok
DATA
354 End data with <CR><LF>.<CR><LF>
Subject: Codespace SWAKS Test

Pozdrav iz FIS!
.
250 Ok: queued
QUIT
221 Bye
```

**Ugotovitev:** Celotno sporocilo je vidno v cleartext - pošiljatelj, prejemnik, zadeva in vsebina.

## Sifriran SMTP s STARTTLS

### Zajem prometa
```bash
sudo tcpdump -i any tcp port 587 -w smtpssl.pcap &
swaks --server 127.0.0.1 --port 587 --tls \
  --from test@localdomain --to demo@localdomain \
  --header 'Subject: STARTTLS test' \
  --body 'Pozdrav prek TLS!'
```

### Zajeti sifrirani promet
```
220 postfix.local ESMTP Postfix (Debian)
EHLO codespaces-1fbaf2
250-postfix.local
250-STARTTLS
...
STARTTLS
220 2.0.0 Ready to start TLS

...........k........*1..m.4....g5..%g.....
(sifrirani podatki - neberljivi)
```

**Ugotovitev:** Po STARTTLS je celotna komunikacija sifirana - vidno je samo da je bilo sporocilo poslano, ne pa vsebina.

## Refleksija

### Razlika med nesifriranim in sifriranim SMTP

| Aspekt | Brez TLS (port 1025) | S STARTTLS (port 587) |
|--------|----------------------|-----------------------|
| Pošiljatelj | Viden | Delno viden (do STARTTLS) |
| Prejemnik | Viden | Delno viden |
| Zadeva | Vidna | Sifirana |
| Vsebina | Vidna | Sifirana |
| Napadalec vidi | Vse | Samo metapodatke povezave |

### Zakaj je PGP fingerprint pomemben?
PGP fingerprint je edinstven identifikator javnega kljuca. Preverimo ga prek zaupanja vrednega kanala (osebno, telefonsko), da zagotovimo, da komuniciramo s pravo osebo in ne z napadalcem, ki bi lahko zamenjal javni kljuc s svojim (MITM napad).

### Kdaj PGP, kdaj Signal?
- **PGP** - za asinhronno komunikacijo (e-posta), kjer potrebujemo dolgotrajno shranjevanje in podpisovanje sporocil
- **Signal** - za sinhronno takojsnjo komunikacijo (chat), kjer je pomembna preprostost uporabe in forward secrecy

### Ali bi moralo biti E2E sifriranje privzeto?
**Da.** End-to-end sifriranje sciti zasebnost uporabnikov pred vdori, prisluskovanjem in zlorabami brez negativnega vpliva na uporabnisko izkusnjo (kot dokazuje Signal). Potencialni izzivi pri boju proti kriminalu zahtevajo alternativne preiskovalne metode, ne pa sibkejse varnosti za vse.
