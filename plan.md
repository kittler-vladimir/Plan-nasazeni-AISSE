# Plán nasazení – migrace C227 na verzi 9 (AISSE)

---

## 1. Předmigrační přípravné práce na frontend prostředí

**Pracnost celkem: 3 dny 2 hodiny**

| Úkol | Doba trvání | Tým | Poznámka | Stav | Start | Konec |
| --- | --- | --- | --- | --- | --- | --- |
| Instalace frontend části do Apache 2.4 (servery sezdmz a semdmz) | 1 den | Tým A | Prováděno za běhu C227 v8, není finální verze v9, posuny termínů, nesplněn termín | Čekání | 05.06.2026 | 12.06.2026 |
| Konfigurace Apache (servery sezdmz a semdmz) – nahrání rozcestníku | 1 den | Tým A | Prováděno za běhu C227 v8, není finální verze v9, posuny termínů, nesplněn termín | Čekání | 05.06.2026 | 12.06.2026 |
| Nahrání Java aplikační části C227 | 1 den | Tým A | Prováděno za běhu C227 v8, není finální verze v9, posuny termínů, nesplněn termín | Čekání | 05.06.2026 | 12.06.2026 |
| Rekonfigurace virtuální služby na F5 LB (přístup z internetu a z KIVS) | 1 hodina | Tým A | Prováděno za běhu C227 v8, není finální verze v9, posuny termínů, nesplněn termín | Čekání | 05.06.2026 | 12.06.2026 |
| Vytvoření zálohy frontend app části (Veritas NetBackup) | 1 hodina | Tým A | Prováděno za běhu C227 v8, není finální verze v9, posuny termínů, nesplněn termín | Čekání | 05.06.2026 | 12.06.2026 |

---

## 2. Předmigrační přípravné práce na backend prostředí

**Pracnost celkem: 7 dnů a 3 hodiny**

| Úkol | Doba trvání | Tým | Poznámka | Stav | Start | Konec |
| --- | --- | --- | --- | --- | --- | --- |
| Instalace backend části do Glassfish 5 | 2 dny | Tým A | Prováděno za běhu C227 v8, není finální verze, posuny termínů, nesplněn termín | Čekání | 05.06.2026 | 12.06.2026 |
| Vytvoření nových domén C227 (servery semadm a sezadm) | 3 dny | Tým A | Prováděno za běhu C227 v8, není finální verze, posuny termínů, nesplněn termín | Čekání | 05.06.2026 | 12.06.2026 |
| Konfigurace nových domén C227 (servery semadm a sezadm) | 2 dny | Tým A | Prováděno za běhu C227 v8, není finální verze, posuny termínů, nesplněn termín | Čekání | 05.06.2026 | 12.06.2026 |
| Nahrání Java aplikační části C227 (WAR soubory) | 1 hodina | Tým A | Prováděno za běhu C227 v8, není finální verze, posuny termínů, nesplněn termín | Čekání | 05.06.2026 | 12.06.2026 |
| Vytvoření zálohy backend app prostředí pomocí nástrojů Glassfish | 2 hodiny | Tým A | Prováděno za běhu C227 v8, není finální verze, posuny termínů, nesplněn termín | Čekání | 05.06.2026 | 12.06.2026 |

---

## 3. Předmigrační přípravné práce na databázovém prostředí

**Pracnost celkem: 7 hodin**

| Úkol | Doba trvání | Tým | Poznámka | Stav | Start | Konec |
| --- | --- | --- | --- | --- | --- | --- |
| Vytvoření zálohy Informix instancí CRO, CVDOP a CVDCD (Veritas NetBackup) | 3 hod | Tým A | Prováděno za běhu aplikace C227 v8 | Čekání | 03.07.2026 | – |
| Nahrání migračních scriptů od dodavatele pro úpravu databází | 3 hod | Tým B | Prováděno za běhu aplikace C227 v8 | Čekání | 03.07.2026 | – |
| Přepnutí dotazování PČR na záložní prostředí semdbs122 (Bedrunka procedury) | 1 hodina | Tým B | Prováděno za běhu aplikace C227 v8 | Čekání | – | – |

---

## Cutover plán

**Pracnost celkem: 18:50 hod — ČAS T = 9:00, 4. 7. 2026**

### 4a. Migrace – Frontend aplikační část

| Úkol | Doba trvání | Tým | Poznámka | Stav | Čas začátku | Čas konce |
| --- | --- | --- | --- | --- | --- | --- |
| Stopnutí Apache 2.2 (servery sezdmz a semdmz) | 10 min | Tým A | Prováděno paralelně | Čekání | 9:00 | – |
| Rekonfigurace virtuálních služeb na F5 LB (rozdělení memberů v poolu frontend Internet a KIVS) | 30 min | Tým A | Prováděno paralelně | Čekání | – | – |
| Start Apache 2.4 (sezdmz a semdmz) s novou verzí rozcestníků a Java aplikací v9 | 20 min | Tým A | Prováděno paralelně | Čekání | – | – |
| Kontrola funkčnosti odkazů v DNS (aisse.mvcr.cms2.cz a aisse.mv.gov.cz) | 20 min | Tým A | Prováděno paralelně | Čekání | – | – |
| Stopnutí Apache 2.4 (servery sezdmz a semdmz) | 10 min | Tým A | Prováděno paralelně | Čekání | – | 9:30 |
| Vyhodnocení GO/NO GO | 10 min | Tým A | – | Čekání | 9:30 | 9:40 |

### 4b. Migrace – Backend aplikační část

| Úkol | Doba trvání | Tým | Dodavatel | Poznámka | Stav | Čas začátku | Čas konce |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Stopnutí ostatních aplikací a Glassfish domén pracovníky MV ČR (AISSEZR, eOPWS, ePasyWS, policie, atd.) | 10 min | Tým B | – | Prováděno paralelně | Čekání | 9:40 | – |
| Stopnutí nově vytvořených domén C227 v9 | 15 min | Tým A | – | Prováděno paralelně | Čekání | – | – |
| Kontrola konfigurace nově vytvořených domén C227 v9 (nastavení portů, certifikátů) | 10 min | Tým A | – | Prováděno paralelně | – | – | – |
| Nastavení komunikačních bran pro EO, EOP a ECD na relační model v9 | 30 min | Tým A | – | Prováděno paralelně | – | – | – |
| Nastavení ostatních aplikací a Glassfish domén MV ČR na relační model v9 | – | Tým B | ARICOMA | Prováděno paralelně | – | – | 10:10 |

### 4c. Migrace – Databázová část

| Úkol | Doba trvání | Tým | Dodavatel | Stav | Čas začátku | Čas konce |
| --- | --- | --- | --- | --- | --- | --- |
| Freeze Informix instancí CVS a ZVS v clusteru | 20 min | Tým A | – | Čekání | 10:10 | – |
| Start migračních SQL scriptů na změnu databází na verzi 9 | 2 hod | Tým B + C | d-PROG | Čekání | – | – |
| Konec migračních SQL scriptů, kontrola logů | 30 min | Tým B | d-PROG | Čekání | – | – |
| Vyhodnocení GO/NO GO | 20 min | Tým B | d-PROG | Čekání | – | – |
| Unfreeze Informix instancí CVS a ZVS v clusteru | 20 min | Tým A | – | Čekání | – | 13:40 |

> ✅ **Vyhodnocení databázová část: GO** (migrace DB proběhla úspěšně)

### 4d. Navazující kroky po úspěšné migraci databáze

| Úkol | Doba trvání | Tým | Dodavatel | Poznámka | Stav | Čas začátku | Čas konce |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Vytvoření zálohy Informix instancí CRO, CVDOP a CVDCD (Veritas NetBackup) | 3 hod | Tým A | – | Automaticky, pravděpodobně jen záloha CRO (ostatní IFX instance se nemění) | Čekání | 13:40 | – |
| Start domén C227 v9 (servery semadm a sezadm) | 30 min | Tým A | – | – | Čekání | – | – |
| Start komunikačních bran pro EO, EOP a ECD | 1 hod | Tým A | – | – | Čekání | – | – |
| Start všech ostatních domén a aplikací MV ČR (AISSEZR, eOPWS, ePasyWS, policie, atd.) | 1 hod | Tým B | – | – | Čekání | – | – |
| Start Apache 2.4 (sezdmz a semdmz) s novou verzí rozcestníků a Java aplikací v9 | 20 min | Tým A | – | – | Čekání | – | – |
| Kontrola funkčnosti odkazů v DNS (aisse.mvcr.cms2.cz a aisse.mv.gov.cz) | 10 min | Tým A+B | – | – | Čekání | – | – |
| Kontrola funkčnosti aplikace verze C227 v9 | 1 hod | Tým A+B+C | ARICOMA | Provádí Hotline | Čekání | – | – |
| Kontrola funkčnosti komunikačních bran EO, EOP a ECD | 1 hod | Tým A+B+C | ARICOMA | Provádí Gračko, Mistrík, Schuster, Kittler a Andreáš. Tým A nemá přístup k datům. | Čekání | – | – |
| Kontrola funkčnosti všech ostatních domén a aplikací MV ČR | 1 hod | Tým B+C | ARICOMA | – | Čekání | – | – |
| Vyhodnocení migrace prostředí C227 na verzi 9 GO/NO GO | 30 min | Tým A+B+C | ARICOMA | – | Čekání | – | – |
| Vyhodnoceno GO | 0 min | Tým A+B+C | ARICOMA | – | Čekání | – | – |
| Zaslání SMS vedení o ukončení migrace | 10 min | Tým A+B | – | – | – | – | 22:10 |

---

## 5. Závěr / Administrativa

**Pracnost celkem: 1 hodina**

| Úkol | Doba trvání | Tým | Stav |
| --- | --- | --- | --- |
| Zápis ZMĚNY do knihy serverů | 1 hodina | Tým A | Čekání |

---

## 7. Testování

### 7.1 Příprava testování

| Úkol | Tým | Stav | Datum |
| --- | --- | --- | --- |
| Uvedení mobilního telefonu pro WhatsApp skupinu | – | Čekání | 03.07.2026 |

### 7.2 AISEO

| Úkol | Tým | Stav | Datum | Čas |
| --- | --- | --- | --- | --- |
| TS EO01 Statistika stavu revizí – Praha 4, Brno za 6. měsíc | Tým C | Čekání | – | – |
| TS EO02 Statistiky od-do – Plzeň, Brno za 6. měsíc | Tým C | Čekání | – | – |
| Kontrola zápisu v archiv_os, osoba_vl, eo_svazek, op_inter_send | – | – | 07.07.2026 | 6:45 |

### 7.3 AIS EOP

| Úkol | Tým | Stav | Datum | Čas |
| --- | --- | --- | --- | --- |
| TS OP01 Statistika vydaných OP za období podle důvodu – za 6. měsíc pro vybrané ORP | Tým C | Čekání | – | – |
| Kontrola zápisu v archiv_op, archiv_op2 | – | – | – | – |

### 7.4 AIS ECD

| Úkol | Tým | Stav | Datum | Čas |
| --- | --- | --- | --- | --- |
| TS CD01.2 Statistika CD podle datumu zavedení do evidence – za 6. měsíc pro vybrané ORP | Tým C | Čekání | – | – |
| Kontrola zápisu v archiv_cd1, archiv_cd2 | – | – | – | – |
| TS CD03 Skartační protokol za období – za 6. měsíc pro vybrané ORP | Tým C | Čekání | – | – |

### 7.5 C227 a provozní monitoring

| Úkol | Tým | Stav | Datum | Čas |
| --- | --- | --- | --- | --- |
| C227 – rozšířené vyhledávání, dotaz na osobu, doklady | HotLine | Čekání | – | – |
| Kontrola aplikačních LOGs – C227, AISSEZR, AISV | Tým B | Čekání | – | – |
| Monitoring provozní zátěže – četnost připojených uživatelů, paměť, zámky, transakční logs | Tým B | Čekání | – | – |
