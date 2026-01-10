# Lab 02 - Varnost posameznikov v kibernetskem prostoru

## Analiza osebne izpostavljenosti

### Iskanje po Google
- Najdeni 2 sliki
- Profili na socialnih omrezjih: LinkedIn in Facebook

### PimEyes (obrazna prepoznava)
- Naslo slike na nekem naključnem photo blogu
- Slike iz srednje sole

### HaveIBeenPwned
- **15 data breachev** povezanih z Gmail racunom
- Priporoca se zamenjava gesel in omogocanje 2FA

### OSINTLeak
- **11 database leakov** za Gmail racun

## Google Dorking

Google dorking je zanimiv pristop za iskanje javno dostopnih, a "skritih" informacij. Primeri poizvedb:
- `filetype:pdf site:gov.si` - iskanje PDF dokumentov na vladnih straneh
- `intitle:"index of" passwords` - iskanje map z gesli
- `inurl:admin login` - iskanje admin prijavnih strani

## Refleksija

### Potencialna tveganja
- Nezasciteni strezniki z objavljenimi poverilnicami
- Javno dostopne slike omogocajo deepfake in krajo identitete
- Stare data breachi vsebujejo gesla, ki so se morda se vedno v uporabi

### Crni scenarij
V tem trenutku lahko napadalec najde katerokoli sliko na internetu, jo uredi z uporabo LLM orodij (npr. deepfake) ter jo uporabi za krajo identitete - npr. za odpiranje bancnih racunov, socialni inzeniring ali izsiljevanje.

### Ocena osebne varnosti/zasebnosti
Moja osebna varnost in zasebnost je rahlo boljsa od povprecja, vendar obstaja prostor za izboljsave:
- Uporaba password managerja
- Omogocanje 2FA povsod
- Redna preverba data breachov
- Minimizacija javno dostopnih osebnih podatkov
