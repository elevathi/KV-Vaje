# Lab 15 - Prepoznavanje MITM napada na GPG kljuce (Web of Trust)

## Vprasanja in odgovori

### 1. Zakaj GPG ne zazna MITM napada samodejno?

GPG (GnuPG) je le orodje za sifriranje. **Samodejno ne more vedeti**, ali javni kljuc, ki ste ga prenesli s spleta, resnicno pripada osebi, za katero se izdaja.

Napadalec lahko v sredino (Man-in-the-Middle) postavi svoj javni kljuc z laznim imenom. GPG bo tehnicno pravilno zasifrireal sporocilo s tem kljucem, vendar ga bo lahko odsifrireal le napadalec, ne pa pravi prejemnik.

### 2. Kaj je fingerprint in zakaj je pomemben?

**Fingerprint** (prstni odtis) je krajsa, edinstvena niz znakov (v obliki heksadecimalnih stevil), ki je ustvarjena iz javnega kljuca s pomocjo zgoscevalneefunkcije (hash).

**Pomembnost:** Ker so javni kljuci dolgi in nepregledni, fingerprint omogoca ljudem, da rocno preverijo, ali imajo pravi kljuc. Ce se fingerprinta ujemata, je kljuc avtentica.

```bash
gpg --fingerprint bob@example.com
```

### 3. Zakaj e-posta ni varen kanal za izmenjavo kljucev?

E-posta privzeto potuje v nesifrirani obliki preko stevilnih streznikov. Napadalec lahko:

- **Prestrezanje** - prestroze e-posto in zamenja vas javni kljuc s svojim
- **Spreminjanje** - vi mislite, da ste poslali svoj kljuc, prejemnik pa prejme napadalcevega (klasicen MITM napad)

### 4. Kako Web of Trust zmanjsa tveganje MITM?

Web of Trust (WoT) temelji na **decentraliziranem potrjevanju identitete**:

**Podpisovanje kljucev:** Ko nekomu zaupate in preverite njegovo identiteto v zivo, podpisete njegov javni kljuc s svojim zasebnim kljucem.

**Veriga zaupanja:** Ce vi zaupate osebi A in oseba A podpise kljuc osebe B, lahko vas GPG program na podlagi te povezave oceni, da je kljuc osebe B verodostojen, ceprav je osebno ne poznate.

S tem se mocno otezi MITM, saj bi moral napadalec ponarediti celotno mrezo podpisov.

## Razlika med tipi zaupanja

### 1. Podpisan kljuc (Signed Key)
**Objektivno potrdilo o identiteti.** Ko podpisete tuj kljuc, svetu sporocate: "Preveril sem, da ta javni kljuc dejansko pripada osebi, ki je navedena v ID-ju kljuca."

- Kaj naredi: Kljuc postane v vasem sistemu "veljaven" (valid)
- Ali se siri? Da - ce svoj podpis izvozite, ga lahko vidijo tudi drugi

### 2. Zaupanje (Trust / Owner Trust)
**Subjektivna ocena zanesljivosti lastnika.** Ko nekomu dodelite doloceno stopnjo zaupanja, pove GPG-ju, naj verjame podpisom, ki jih je ta oseba dala drugim kljucem.

- Kaj naredi: Ce polno zaupate osebi A, bo GPG samodejno priznal veljavnost osebe B, ce jo je oseba A podpisala
- Ali se siri? Ne - to je vasa lokalna nastavitev

### 3. Ultimativno zaupanje (Ultimate Trust)
**Najvisja stopnja zaupanja**, obicajno rezervirana le za vase lastne kljuce.

- Pomen: Pomeni, da kljucu zaupate brez kakrsnihkoli pogojev
- Vloga: Je koren (root) vase osebne mreze zaupanja, iz katere se zaupanje siri naprej

## Povzetek

| Koncept | Opis |
|---------|------|
| MITM napad | Napadalec podtakne svoj kljuc namesto pravega |
| Fingerprint | Edinstven identifikator za preverjanje kljuca |
| Web of Trust | Decentraliziran sistem za potrjevanje identitet |
| Podpis kljuca | Javno potrdilo o identiteti |
| Owner Trust | Lokalna ocena zanesljivosti osebe |
