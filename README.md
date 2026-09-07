# Claude Session Viewer

Jednoduchá jednosouborová webová aplikace pro analýzu spotřeby tokenů a nákladů v transkriptech [Claude Code](https://claude.com/claude-code) sessions – včetně subagentů, které session spustila.

Celá aplikace běží **pouze lokálně v prohlížeči** (žádný backend, žádné odesílání dat kamkoliv na server) – soubory se čtou přímo z disku pomocí File API prohlížeče.

## K čemu to je

Claude Code ukládá historii každé konverzace (session) jako `.jsonl` soubor a k ní i přepisy jednotlivých subagentů, které v rámci session vznikly. Tato aplikace tyto soubory načte a zobrazí:

- **Přehled sessions** v dané projektové složce (název, datum, počet subagentů).
- **Dashboard k session** – souhrnné dlaždice (celková cena, velikost kontextového okna, výstupní tokeny, cache čtení/zápis, počet subagentů).
- **Graf ceny podle agenta a nákladové složky** (cache čtení/zápis, vstup, výstup) – skládaný pruhový graf s tooltipem.
- **Tabulku agentů** (hlavní běh + subagenti) s počtem API volání, tokeny a odhadovanou cenou.
- **Detail agenta** – graf růstu kontextového okna v čase, odhad přínosu subagenta (kolik tokenů "ušetřil" hlavnímu běhu) a procházení celé konverzace včetně nástrojových volání, výsledků a "thinking" bloků.

Ceny jsou orientační přepočet podle veřejného ceníku Anthropic API (USD/1M tokenů) – u předplatného Claude Code se tokeny neúčtují přímo, čísla slouží hlavně k porovnání nákladnosti jednotlivých běhů a subagentů.

## Jak to spustit

Není potřeba žádná instalace ani build – stačí otevřít `claude-token-viewer.html` přímo v prohlížeči (dvojklikem, nebo `File > Open`).

> Poznámka: Kvůli výběru celé složky (`webkitdirectory`) funguje nejlépe v prohlížečích založených na Chromiu (Chrome, Edge, Brave...).

### Použití

1. Otevři `claude-token-viewer.html` v prohlížeči.
2. Klikni na **📁 Vybrat složku projektu** a vyber složku konkrétního projektu z `~/.claude/projects/<název-projektu>` (na Windows typicky `C:\Users\<uživatel>\.claude\projects\<název-projektu>`).
3. Aplikace najde všechny hlavní `*.jsonl` soubory (sessions) v této složce a k nim příslušné podsložky `<session>/subagents/` s přepisy subagentů.
4. Klikni na session ze seznamu → zobrazí se dashboard s náklady, grafy a tabulkou agentů.
5. Klikni na řádek agenta v tabulce → zobrazí se detail včetně grafu růstu kontextového okna a celé konverzace.

## Technologie

Čistý HTML/CSS/JavaScript bez závislostí a bez buildovacího kroku – jeden soubor, který si stačí stáhnout a otevřít.

## Screenshot

<!-- Sem prosím vlož screenshot aplikace, např.: -->
<!-- ![Screenshot](screenshot.png) -->
