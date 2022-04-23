---
layout: postc
title:  "Nesrovnalosti v datových sadách"
date:   2021-11-18 10:35:00 +0100
tags: covid cs
---

Ministerstvo každý den publikuje [datové sady](https://onemocneni-aktualne.mzcr.cz/api/v2/covid-19) týkající se covidu a já je každou hodinu [zazálohuju](https://gitlab.com/martin.majlis/covid-19-data), protože příliš nevěřím tomu, že je ČR schopna s daty nějak pracovat.

Už loni jsem si všimnul, že v `osoby.csv` jsou nesrovnalosti, tak jsem jim napsal e-mail, aby se na to podívali. Jejich reakce byla, že mám používat verzi 2 místo verze 1, i když ty soubory byly identické. Článek o [reinfekcích](https://www.seznamzpravy.cz/clanek/preziti-covidu-chrani-ale-mene-nez-se-zdalo-reinfekci-je-radove-vice-180447) mne přiměl se na aktuální situaci podívat.

## Nesrovnalosti

Když se podívám na dnešní data (2021-11-18):

### ockovani-distribuce.csv ###

* [ockovani-distribuce.csv](https://gitlab.com/martin.majlis/covid-19-data/-/commit/8f2f21f713f9fbfe3425a38048d9ab3391853b58)
* Některé řádky jsou zduplikované, některé duplikace mizí, některé unikátní řádky mizí
* Problematické záznamy: 2021-10-06, 2021-10-29, 2021-11-11, ...
* 2x:
  * ```
sort data/backup/onemocneni-aktualne.mzcr.cz_covid-19-v2/ockovani-distribuce-sorted.csv | uniq -c | sort -nr
```
  * ```
      2 2021-10-06,262721a0-5551-41d6-bc46-06d5aa9d18a8,"FN Ostrava - Poliklinika",CZ080,"Moravskoslezský kraj",78823faf-6770-4848-9579-4f96feef42e4,"Nemocnice AGEL Nový Jičín a.s.",CZ080,"Moravskoslezský kraj",Comirnaty,Pfizer,Výdej,30,180,3c190d13-b40c-4f93-b82e-b995480c9847
      2 2021-10-06,262721a0-5551-41d6-bc46-06d5aa9d18a8,"FN Ostrava - Poliklinika",CZ080,"Moravskoslezský kraj",63a56753-7d68-44cb-a025-d605c6c8d307,"Nemocnice s poliklinikou Karviná-Ráj, p.o. - pracoviště Orlová",CZ080,"Moravskoslezský kraj",Spikevax,Moderna,Výdej,1,10,7f4e8d94-38e8-4a28-bbc3-42e6915741bf
      2 2021-10-06,262721a0-5551-41d6-bc46-06d5aa9d18a8,"FN Ostrava - Poliklinika",CZ080,"Moravskoslezský kraj",63a56753-7d68-44cb-a025-d605c6c8d307,"Nemocnice s poliklinikou Karviná-Ráj, p.o. - pracoviště Orlová",CZ080,"Moravskoslezský kraj",Comirnaty,Pfizer,Výdej,15,90,7f4e8d94-38e8-4a28-bbc3-42e6915741bf
      2 2021-10-06,262721a0-5551-41d6-bc46-06d5aa9d18a8,"FN Ostrava - Poliklinika",CZ080,"Moravskoslezský kraj",39036e3e-62e4-4ea3-8a5f-92bbc64acfba,"Zdravotnická záchranná služba MSK, p. o.",CZ080,"Moravskoslezský kraj",Comirnaty,Pfizer,Výdej,2,12,24d9a218-dca3-4ba2-b0b4-d99b55178ee9
      2 2021-10-06,262721a0-5551-41d6-bc46-06d5aa9d18a8,"FN Ostrava - Poliklinika",CZ080,"Moravskoslezský kraj",243d9780-7f89-4218-8db5-e18ceda4778b,"Nemocnice AGEL Podhorská a.s. pracoviště Bruntál",CZ080,"Moravskoslezský kraj",Comirnaty,Pfizer,Výdej,16,96,8af193e3-1404-4b3b-8e46-2097dacdc2b8
      2 2021-10-06,262721a0-5551-41d6-bc46-06d5aa9d18a8,"FN Ostrava - Poliklinika",CZ080,"Moravskoslezský kraj",1f87f33d-96b7-4e48-a6e9-8accc40e2129,"Dopravní zdravotnictví a.s., Poliklinika AGEL Ostrava",CZ080,"Moravskoslezský kraj",Comirnaty,Pfizer,Výdej,2,12,ce10fdc6-160d-40cf-a66b-e79ef57e6286
      1 datum,ockovaci_misto_id,ockovaci_misto_nazev,kraj_nuts_kod,kraj_nazev,cilove_ockovaci_misto_id,cilove_ockovaci_misto_nazev,cilovy_kraj_kod,cilovy_kraj_nazev,ockovaci_latka,vyrobce,akce,pocet_ampulek,pocet_davek,distribuce_id
      1 2021-11-17,c4411674-d3bd-4666-96df-fdedefed8b68,"Nemocnice Jindřichův Hradec - OČKO centrum",CZ031,"Jihočeský kraj",af93d502-871a-4bae-9003-e5793a73520c,"(Bez registrace) Nemocnice Jindřichův Hradec - OČKO centrum",CZ031,"Jihočeský kraj",Comirnaty,Pfizer,Výdej,50,300,21e3ed5b-e3af-41d7-80f3-1edc775c7d70
```

### ockovani-spotreba.csv ###

* [ockovani-spotreba.csv](https://gitlab.com/martin.majlis/covid-19-data/-/commit/a102cd87eee8cf8da934c827447f13afd58c0b00)
* Některé řádky jsou zduplikované, některé duplikace mizí, některé unikátní řádky mizí
* Problematické záznamy: 2021-06-07, 2021-06-24, 2021-07-19, ...

### ockovani.csv ###

* [ockovani.csv](https://gitlab.com/martin.majlis/covid-19-data/-/commit/6d083d6c3aa5e51bc0feabf1c7f981f9f00a0093)
* `git show 6d083d6c3aa5e51bc0feabf1c7f981f9f00a0093` - [diff](/assets/2021-11-18-6d083d6c3aa5e51bc0feabf1c7f981f9f00a0093.html)
* Mění se počty očkovaných v různých dnech a krajích
* Problematické záznamy: 2021-01-05, 2021-01-07, 2021-01-08, ...

### hospitalizace.csv ###

* [hospitalizace.csv](https://gitlab.com/martin.majlis/covid-19-data/-/commit/49986dd182c704f62e02d39815d49210783164d5)
* Mění se počty pacientů v různých stavech
* Problematické záznamy: 2020-10-25, 2020-11-02, 2020-11-13, ...

### mestske-casti.csv ###

* [mestske-casti.csv](https://gitlab.com/martin.majlis/covid-19-data/-/commit/2d200d3b2a9175343c2acd23c03ff56077a61c29)
* `git show 2d200d3b2a9175343c2acd23c03ff56077a61c29` - [diff](/assets/2021-11-18-2d200d3b2a9175343c2acd23c03ff56077a61c29.html)
* Mění se počty nových případů, aktivních případů
* Problematické záznamy: 2020-03-16, a potom velké v množství podle počtů případů
* Stěhující se lidé - 2020-03-16 - člověk se přestehoval z Prahy 8 na Prahu 1
* Poznámka: Tento dataset se týká jenom Prahy. Je tam obdobný dataset týkající se obci - `obce.csv`, ale ten je příliš velký, tak ho ignoruju

### orp.csv ###

* [orp.csv](https://gitlab.com/martin.majlis/covid-19-data/-/commit/34683eaa99017c1967f59bc87404e002315067da)
* `git show 34683eaa99017c1967f59bc87404e002315067da` - [diff](/assets/2021-11-18-34683eaa99017c1967f59bc87404e002315067da.html)
* Mění se počty - 10000 změněných řádků
* Problematické záznamy: 2020-03-28, ...

### kraj-okres-nakazeni-vyleceni-umrti.csv ###

* [kraj-okres-nakazeni-vyleceni-umrti.csv](https://gitlab.com/martin.majlis/covid-19-data/-/commit/a14cfc15cf4efb1405895f4f795cacf5e1000661)
* `git show a14cfc15cf4efb1405895f4f795cacf5e1000661` - [diff](/assets/2021-11-18-a14cfc15cf4efb1405895f4f795cacf5e1000661.html)
* Mění se počty - 24000 změněných řádků
* Problematické záznamy: 2020-04-06, ...
* Stěhující se lidé?

### osoby.csv ###

* [osoby.csv](https://gitlab.com/martin.majlis/covid-19-data/-/commit/dbcc26d11aa5e9b15c0824abced60f88e7f9c54e)
* `git show dbcc26d11aa5e9b15c0824abced60f88e7f9c54e` - [diff](/assets/2021-11-18-dbcc26d11aa5e9b15c0824abced60f88e7f9c54e.html)
* Stěhující se lidé, změny pohlaví, stárnutí o 1 rok
* Problematické záznamy: 2020-04-30, 2020-05-14, ...
  * Stěhování: `-2020-04-30,24,M,CZ031,CZ0316,,,` - `+2020-04-30,24,M,CZ032,CZ0323,,,`
  * Změna pohlaví: `-2020-07-07,46,Z,CZ080,CZ0801,,,` - `+2020-07-07,46,M,CZ080,CZ0801,,,`
  * Stárnutí: `-2021-03-31,26,Z,CZ032,CZ0323,,,` - `+2021-03-31,27,M,CZ032,CZ0323,,,1`

### umrti.csv ###

* [umrti.csv](https://gitlab.com/martin.majlis/covid-19-data/-/commit/bfe7f962f7391c9b7b1baf99c635d33c0bf4814c) - dnešní data vypadají dobře
* data z minulého týdne:
  * Příkazy:

```
git log .//data/backup//onemocneni-aktualne.mzcr.cz_covid-19-v2/umrti.csv
git show 1778f773860b7f5320ddac0685c0251eda0f3481:.//data/backup//onemocneni-aktualne.mzcr.cz_covid-19-v2/umrti.csv | sort > /tmp/umrti-1778f773860b7f5320ddac0685c0251eda0f3481.csv
git show 963a3ce82bb19118a39d5345102be09dc6c89308:.//data/backup//onemocneni-aktualne.mzcr.cz_covid-19-v2/umrti.csv | cut -f 2-99 -d, | sort > /tmp/umrti-963a3ce82bb19118a39d5345102be09dc6c89308.csv

diff --color=always /tmp/umrti-1778f773860b7f5320ddac0685c0251eda0f3481.csv /tmp/umrti-963a3ce82bb19118a39d5345102be09dc6c89308.csv
```
* [diff](/assets/2021-11-18-1778f773860b7f5320ddac0685c0251eda0f3481-963a3ce82bb19118a39d5345102be09dc6c89308.html)
* Problematické záznamy: 2021-01-03, 2021-10-28
* Stěhování, změny věků

### vyleceni.csv ###

* [vyleceni.csv](https://gitlab.com/martin.majlis/covid-19-data/-/commit/0cd1f7b7a351cdf7fb7346f39c7ed3eafd12f316)
* `git show 0cd1f7b7a351cdf7fb7346f39c7ed3eafd12f316` - [diff](/assets/2021-11-18-0cd1f7b7a351cdf7fb7346f39c7ed3eafd12f316.html)
* Problematické záznamy: 2020-04-06, ...
* Podobné jako `kraj-okres-nakazeni-vyleceni-umrti.csv`

### kraj-okres-testy.csv ###

* [kraj-okres-testy.csv](https://gitlab.com/martin.majlis/covid-19-data/-/commit/b30d598063ed1b4c59d6f0fbc2f25e741f3970ff)
* `git show b30d598063ed1b4c59d6f0fbc2f25e741f3970ff` - [diff](/assets/2021-11-18-b30d598063ed1b4c59d6f0fbc2f25e741f3970ff.html)
* Změny počtů
* Problematické záznamy: 2020-11-17, 2020-11-26, ...


## Závěr

* Všechny datasety, na které jsem se podíval, mění data stará několik měsíců (maximum je pro dnešek rok a půl).
* Je podivné, že různé reporty mají první problematický záznam v různých dnech. Čekal bych, že přestěhovaný/znovu infikovaný/mrtvý člověk způsobí problém v jejich předpokladech, takže se datasety změní ve stejný den.
* Pokud by pipeliny pro generování dat testovali, tak by si ta data seřadili, aby se jim snadněji psali testy. Vzhledem k tomu, že ty data jsou pokaždé seřazená jinak, tak jsem očekával, že je netestují, takže tam budou problémy. Nečekal jsem, že problematické budou všechny reporty.


## Poznámky

* Od minulé vlny jsem to neaktualizoval, takže spoustu reportů nezálohuji.
* Kvůli tomu, že ty soubory nejsou setřízené, tak pro rozdílý mezi staršími reporty je potřeba používat postup z `umrti.csv`.
* Vypadá to, že 2021-11-17 přidali do reportů sloupeček id, který je pokaždé jiný.


