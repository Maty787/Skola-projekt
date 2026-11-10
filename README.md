# NetProbe

Malé přenosné zařízení na Raspberry Pi 5, které zmapuje bezdrátové a síťové zařízení v okolí a řekne, co o nich zjistilo: kamery, IoT krabičky, Wi-Fi sítě a to, co se k nim ještě hodí.

Inspirací je HackRF. Jeden kompaktní nástroj, který si vezmete s sebou, místo hromady programů a adaptérů. NetProbe ale není SDR a nesnaží se jím být. Je zaměřený na audit a výsledkem není surový výstup, ale srozumitelný report.

Používejte ho jen na sítích a zařízeních, která vlastníte, nebo k nimž máte písemné svolení.

## Stav

Projekt je ve fázi návrhu. Hotový je Project Charter a kostra repozitáře, první funkční verze (MVP) je plánovaná na duben. Dokud neexistuje první release, README popisuje záměr, ne hotový produkt.

## Co má MVP umět

1. Najít zařízení v dosahu a rozpoznat, jestli jde o kameru, IoT zařízení, nebo něco jiného.
2. Zjistit otevřené porty a běžící služby.
3. Ukázat výsledky ve webovém rozhraní a uložit je jako report.

Před každým skenem rozhraní vyžaduje potvrzení, že uživatel má k cíli oprávnění. Přeskočit se to nedá.

## Co umět nebude

Cloud, více uživatelů, mobilní aplikaci ani žádné aktivní útoky na nalezená zařízení. NetProbe zjišťuje a hlásí, nic nenarušuje.

## Jak to funguje

Raspberry Pi se připojí k síti a přes prohlížeč (`netprobe.local`) se ovládá webové rozhraní. To posílá požadavek na backend ve FastAPI, který spustí sken pomocí nmap, výstup zpracuje a uloží do SQLite. Z uložených nálezů se potom generuje report.

Vlastní skener nepíšu. Skládám ověřené nástroje a snažím se, aby jádro zůstalo malé.

Moduly pro další typy zařízení jsou v návrhu počítané jako samostatné části. Konkrétní hardware pro rádiovou část (Wi-Fi adaptér a další) zatím není vybraný.

## Technologie

Python, FastAPI, SQLite, nmap, HTML + Tailwind, Raspberry Pi 5.

## Struktura repozitáře

```
backend/     API a spouštění skenů
frontend/    webové rozhraní
docs/        Project Charter a další dokumentace
```

## Instalace

Zatím není co instalovat. Postup doplním s první funkční verzí.

## Plán

Do dubna čtyři měsíční milníky. Pokud se bude časově škrtat, pořadí priorit je: discovery, sken, report. Webové rozhraní by pak bylo minimální.

## Licence

MIT, viz [LICENSE](LICENSE).

## Autor

Matyáš Vojtíšek
