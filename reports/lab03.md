# Lab 03 - OSINT: Zbiranje informacij o posameznikih na spletu

## Uporabljena orodja

### Sherlock
- Ze namescen v Kali Linux
- Zagon: `sherlock blacklights`

### Maigret
- Uporabljen preko Telegram bota
- Generira HTML porocilo z dodatnimi metapodatki

## Rezultati iskanja za username "blacklights"

### Sherlock rezultati
**Stevilo najdenih profilov: 104**

Primeri najdenih platform:
| Kategorija | Platforme |
|------------|-----------|
| Gaming | Steam, Chess.com, Roblox, Minecraft, osu!, Pokemon Showdown |
| Social | Reddit, VK, TikTok, Snapchat, Pinterest, Mastodon |
| Video | YouTube, Twitch, Vimeo, DailyMotion, Kick |
| Coding | GitHub, GitLab, Codeforces, GeeksforGeeks |
| Music | SoundCloud, Spotify, Bandcamp, MixCloud, last.fm |
| Art/Design | DeviantArt, Behance, Flickr, Giphy |
| Professional | LinkedIn (ni najden), Freelancer, Docker Hub |

### Maigret rezultati
**Stevilo najdenih racunov: 72**

#### Izluseni osebni podatki
- **Polno ime:** black light
- **Geografija:** US (22), RU (11), IN (9), JP (4), KR (1), CN (1), BR (1)
- **Interesi:** gaming (7), coding (5), music (5), wiki (4), sharing (4), photo (4)
- **Prvo opazeno:** 2012-11-09

#### Najdeni email naslovi
- blacklights@bk.ru
- blacklights@mail.ru

#### Steam ID
- 76561198992878976

## Primerjava orodij

| Kriterij | Sherlock | Maigret |
|----------|----------|---------|
| Stevilo zadetkov | 104 | 72 |
| Metapodatki | Ne | Da (ime, geo, interesi) |
| Email naslovi | Ne | Da |
| HTML porocilo | Ne | Da |
| Hitrost | Hitrejsi | Pocasnejsi |

**Zakljucek:** Sherlock najde vec profilov, Maigret pa ponuja boljso analizo z izvlecenjem dodatnih podatkov.

## Nepricakovane najdbe
- Veliko .ru (ruskih) platform - VK, Mail.ru, pikabu
- Fandom wiki strani
- Starejsi datum registracije (2012)

## Refleksija

### Najlazje najdene informacije
- Uporabniska imena na javnih platformah
- Slike profilov
- Javne objave

### Najtezje najdene informacije
- Realno ime (razen ce je javno objavljeno)
- Kontaktni podatki
- Zasebni profili

### Kako se zascititi
- Uporaba unikatnega usernamea za vsako stran
- Omejitev javno dostopnih informacij
- Uporaba privacy nastavitev na platformah
- Izogibanje povezovanju racunov med seboj

### Eticnost OSINT
OSINT ni eticno sporen sam po sebi. Je upravicen v naslednjih primerih:
- Varnostne preiskave
- Novinarstvo in research
- Preverjanje lastne izpostavljenosti
- Penetracijski testi z dovoljenjem
- Iskanje izgubljenih oseb

Ni upravicen za:
- Zalezovanje (stalking)
- Izsiljevanje
- Krajo identitete
