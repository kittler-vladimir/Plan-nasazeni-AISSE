# Plán nasazení – AISSE (C227, migrace na verzi 9)

Tento repozitář obsahuje plán migrace systému **C227** z verze v8 na verzi v9, včetně předmigračních příprav, detailního cutover plánu s časovými značkami, závěrečné administrativy a testování.

## Obsah repozitáře

- `plan.md` – kompletní plán migrace, rozdělený do následujících fází:
  1. **Předmigrační přípravné práce na frontend prostředí** – instalace a konfigurace Apache 2.4, nahrání Java aplikační části, rekonfigurace F5 LB, zálohy (pracnost: 3 dny 2 hodiny).
  2. **Předmigrační přípravné práce na backend prostředí** – instalace Glassfish 5, vytvoření a konfigurace nových domén, nahrání WAR souborů, zálohy (pracnost: 7 dnů a 3 hodiny).
  3. **Předmigrační přípravné práce na databázovém prostředí** – zálohy Informix instancí, nahrání migračních scriptů, přepnutí dotazování PČR (pracnost: 7 hodin).
  4. **Cutover plán (migrace na verzi 9, 4.7.2026, T = 9:00)** – detailní harmonogram dne ostrého přechodu s časovými značkami (9:00–22:10), rozdělený na frontend, backend a databázovou část, včetně bodů GO/NO GO a finálních kontrol funkčnosti (pracnost: 18:50 hod).
  5. **Závěr / Administrativa** – zápis změny do knihy serverů (pracnost: 1 hodina).
  7. **Testování** – testovací scénáře a kontroly po migraci, rozdělené do podsekcí:
     - Příprava (WhatsApp skupina)
     - AISEO (TS EO01, TS EO02, kontrola zápisů – 07.07.2026)
     - AIS EOP (TS OP01, kontrola archiv_op)
     - AIS ECD (TS CD01.2, TS CD03, kontrola archiv_cd)
     - C227 a provozní monitoring (HotLine, aplikační logy, monitoring zátěže)

## Týmy

- **Tým A** – instalace, konfigurace a nasazení frontend a backend části, administrativa
- **Tým B** – databázové úpravy, aplikace pracovníků MV ČR, provozní monitoring
- **Tým C** – testování a vyhodnocení (AISEO, AIS EOP, AIS ECD)
- **HotLine** – testování C227 (rozšířené vyhledávání, dotaz na osobu, doklady)
- **ARICOMA / d-PROG** – externí dodavatelé zajišťující součinnost u vybraných kroků

## Poznámka k prostředí

Předmigrační práce probíhají za běhu produkční aplikace C227 v8. Verze v9 zatím není finální, proto dochází k posunům termínů v souvislosti s řešením nedostatků.

---

## Práce s repozitářem

### Klonování repozitáře

```bash
git clone https://github.com/kittler-vladimir/Plan-nasazeni-AISSE.git
cd Plan-nasazeni-AISSE
```

### Stažení aktuálních změn (pull)

Před každým začátkem práce doporučujeme stáhnout nejnovější verzi z GitHubu:

```bash
git pull origin main
```

Pokud lokální a vzdálená historie nemají společný základ (např. po inicializaci repozitáře s README na GitHubu), použij:

```bash
git pull origin main --allow-unrelated-histories
```

### Odeslání změn (push)

```bash
git add .
git commit -m "Popis provedené změny"
git push origin main
```

Pokud push selže s chybou `non-fast-forward` (vzdálená větev obsahuje commity, které lokálně nemáš), nejprve proveď `git pull origin main` a teprve poté `git push`.

### Práce s Issues

Issues slouží k evidenci úkolů, chyb a návrhů souvisejících s migrací.

**Vytvoření nového issue (web):**
1. Záložka **Issues** → **New issue**
2. Vyplň název a popis úkolu/problému
3. Nastav přiřazenou osobu (Assignee), štítek (Label) a případně milník (Milestone)

**Vytvoření issue přes GitHub CLI:**
```bash
gh issue create --title "Název úkolu" --body "Popis úkolu" --label bug
```

**Propojení commitu/PR s issue:**
V commit message nebo popisu pull requestu napiš:
```
Fixes #číslo_issue
```
Po sloučení do `main` větve se issue automaticky uzavře.

**Užitečné odkazy v textu:**
- `#12` – odkaz na issue/PR číslo 12
- `@uzivatel` – upozornění konkrétního uživatele v komentáři
- `- [ ] úkol` – checklist v popisu issue (GitHub zobrazí progres, např. 2/5 hotovo)
