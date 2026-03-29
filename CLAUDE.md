# Davčni kalkulator za Freelancerje

## Opis projekta
Single-page HTML/CSS/JS aplikacija za primerjavo obdavčitve freelancerjev v 18 državah. Ciljna skupina: programerji in konzultanti z nizkimi dejanskimi stroški.

## Arhitektura
- Ena datoteka: `index.html` (HTML + CSS + JS, brez odvisnosti)
- Hosted na GitHub Pages: https://knagode.github.io/freelancers_and_taxes/

## Ključni podatkovni viri za davčne parametre

### Slovenija (Normiran S.P.)
- Zakon ZPZR (veljaven od 1.1.2026): normirani odhodki 80% na prvih 60.000 EUR, cedularno 20%/35%
- Prispevki: FURS / ZPIZ - 40,20% (vklj. OZDO od jul. 2025)
- Min. osnova za prispevke: 60% povprečne plače (SURS)
- Vir: data.si, finras.si, racunovodstvo.net

### Hrvaška (Paušalni obrt)
- 7 fiksnih davčnih razredov (203-1.080 EUR/leto)
- Prispevki ~291 EUR/mesec fiksno
- Vir: hok.hr, fiskalopedija.hr

### Estonija (OÜ)
- 0% na zadržan dobiček, 20% ob izplačilu
- 33% socialni davek na plačo
- Vir: emta.ee, e-residency.gov.ee

### Italija (Regime Forfettario)
- 67% koeficient za programerje (ATECO 62.01.00), 15% davek
- INPS Gestione Separata: 26,23%
- Vir: agenziadelleentrate.gov.it, regime-forfettario.it

### Nemčija (Freiberufler)
- Progresivna formula (ne ravni razredi) po §32a EStG
- GKV ~17,1% + Pflege 4,2% (do kapice 69.750 EUR)
- Vir: bundesfinanzministerium.de

### Singapur
- 13 progresivnih razredov, 0-24%
- MediSave 8% (obvezno za samozaposlene)
- Tečaj: 1 EUR ≈ 1,44 SGD
- Vir: iras.gov.sg, cpf.gov.sg

### UK
- Tečaj: 1 EUR ≈ 0,85 GBP
- Personal Allowance taper nad 100k GBP
- Vir: gov.uk/income-tax-rates

### ZDA (Kalifornija / Wyoming)
- Tečaj: 1 EUR ≈ 1,08 USD
- SE tax 15,3% (na 92,35% dobička)
- Vir: irs.gov, ftb.ca.gov

## Zdravstveno zavarovanje
Države kjer ZZ NI vključeno v prispevke in ga je treba plačati posebej:
- **Dubaj**: ~300 EUR/mesec (obvezno za vizum)
- **Gruzija**: ~100 EUR/mesec (javno ne velja za expate)
- **Singapur**: ~350 EUR/mesec (MediSave samo hospitalizacija)
- **ZDA (CA)**: ~550 EUR/mesec (ACA marketplace)
- **ZDA (WY)**: ~500 EUR/mesec (ACA marketplace)
- **Irska**: ~175 EUR/mesec (PRSI ne pokrije GP obiskov)

Aplikacija ima checkbox za vključitev teh stroškov v primerjavo.

## Opombe za razvijalce
- Vsi izračuni so poenostavljeni modeli za informativne namene
- Davčni parametri se spreminjajo letno - preveriti pred novim letom
- Tečaji valut so fiksirani (EUR/GBP, EUR/USD, EUR/SGD) - v produkciji bi bilo bolje uporabiti API
- Za dodajanje nove države: dodaj objekt v array `COUNTRIES` z `calculate()` funkcijo ki vrne `{prispevki, dohodnina, neto, steps}`
