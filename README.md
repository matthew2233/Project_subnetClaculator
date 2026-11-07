# IPv4 Subnet Calculator

Konzolová aplikace v jazyce Python 3 pro výpočet parametrů IPv4 podsítí (subnetting). Projekt implementuje vlastní algoritmy pro binární převody a síťovou matematiku a obsahuje sadu automatizovaných testů ověřujících správnost výpočtů oproti standardní knihovně `ipaddress`.

## Účel a klíčové funkce programu

Po zadání IPv4 adresy a masky (ve formátu CIDR prefixu `/0` až `/32`, případně dekadické masky `255.255.255.0`) program:
* **Zvaliduje vstupní data:** Zkontroluje správný formát zápisu, rozsah oktetů (`0–255`) a platnost prefixu (`0–32`). Při neplatném vstupu (např. `300.1.1.1/24`, `10.0.0.1/33`, `abc`) program nespadne, ale vypíše srozumitelné upozornění.
* **Převede IP adresu a masku do binárního tvaru** (např. `11000000.10101000.00000001.00001010`).
* **Vypočítá parametry podsítě:**
  * Adresu sítě (Network Address)
  * Masku podsítě (Subnet Mask) a Wildcard masku
  * Broadcast adresu
  * První a poslední použitelnou adresu hosta (First & Last Usable Host)
  * Celkový počet použitelných hostů v síti (včetně korektního ošetření okrajových případů `/0`, `/30`, `/31` a `/32`).

## Struktura projektu

* `main.py` – Hlavní spouštěcí soubor aplikace (rozdělený do modulárních funkcí: `vstup -> výpočty -> výpis`).
* `test_calculator.py` – Testovací skript porovnávající výsledky kalkulačky s vestavěným modulem `ipaddress` na běžných i okrajových případech (`/0`, `/8`, `/16`, `/24`, `/30`, `/31`, `/32`).
* `docs/priklad.md` – Detailní ruční výpočet ukázkové podsítě (`192.168.1.10/24`) krok za krokem.

## Požadavky a spuštění

Projekt vyžaduje nainstalovaný **Python 3.x** a nepoužívá žádné externí závislosti mimo standardní knihovnu.

1. Naklonování repozitáře:
   ```bash
   git clone <URL_REPOZITARE>
   cd <NAZEV_SLOZKY>
