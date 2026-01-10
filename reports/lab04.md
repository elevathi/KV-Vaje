# Lab 04 - MetaOSINT: Kaj vse razkrije fotografija?

## Analiza testne fotografije

### Uporabljeno orodje
- pic2map.com

### Izvleceni EXIF metapodatki

| Podatek | Vrednost |
|---------|----------|
| Kamera | NIKON COOLPIX P6000 |
| Datum | 22. oktober 2008 (sreda) |
| Drzava | Italija |
| Mesto | Arezzo, Toskana |
| Naslov | Via del Saracino, Arezzo, Tuscany, 52100, Italy |
| GPS koordinate | 43° 27' 57.64" N, 11° 52' 44.80" E |
| Google Maps | https://maps.app.goo.gl/NxEafmB6sjvZq3Fo8 |

## Analiza in porocilo

### 1. Natancna lokacija
- **Koordinate:** 43° 27' 57.64" N, 11° 52' 44.80" E
- **Naslov:** Via del Saracino, Arezzo, Tuscany, 52100, Italy

### 2. Cas nastanka
- 22. oktober 2008

### 3. Drugi metapodatki
- Model kamere (Nikon Coolpix P6000)
- Ni bilo drugih metapodatkov (verjetno ze ocisceni)

### 4. Kaj presenetilo?
- Kako natancno lahko dolocimo lokacijo iz fotografije
- GPS podatki so shranjeni v standardnem formatu

### 5. Priporocila za objavljanje slik
- Onemogoci GPS oznacevanje v nastavitvah kamere/telefona
- Pred objavo ocisti EXIF podatke z orodji (exiftool, verexif.com)
- Vecina socialnih platform avtomatsko odstrani EXIF podatke, a ni zagotovljeno

## Refleksija

### Ali bi moral vsak pred objavo slike odstraniti EXIF podatke?
Da, sploh ce objavlja slike iz zasebnih lokacij (dom, delovno mesto). Socialne platforme sicer vecino podatkov odstranijo, vendar ni zagotovljeno.

### Kako se zascititi pred zlorabo?
- Izkljuci lokacijo v fotoaparatu/telefonu
- Uporabi orodja za odstranitev metapodatkov
- Preveri slike pred objavo

### Ali sem ze kdaj objavil sliko z metapodatki?
Ne.

## Odstranitev EXIF podatkov

```bash
# Z exiftool
exiftool -all= slika.jpg

# Z prepisovanjem originala
exiftool -all= -overwrite_original slika.jpg
```
