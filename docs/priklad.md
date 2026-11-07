# Ukázkový výpočet podsítě krok za krokem

**Zadaný vstup:** `192.168.1.10/24`

## 1. Převod IP adresy do binárního tvaru
Každý oktet (číslo oddělené tečkou) převedeme na 8bitové binární číslo:
* `192` = `11000000`
* `168` = `10101000`
* `1`   = `00000001`
* `10`  = `00001010`
* **IP binárně:** `11000000.10101000.00000001.00001010`

## 2. Určení masky podsítě z prefixu /24
Prefix `/24` znamená, že prvních 24 bitů zleva jsou jedničky (síťová část) a zbylých $32 - 24 = 8$ bitů jsou nuly (hostitelská část):
* **Maska binárně:** `11111111.11111111.11111111.00000000`
* **Maska dekadicky:** `255.255.255.0`
* **Wildcard maska (inverzní):** `0.0.0.255` (`00000000.00000000.00000000.11111111`)

## 3. Výpočet adresy sítě (Network Address)
Provedeme logický součin (bitový `AND`) mezi IP adresou a maskou (vynulujeme hostitelskou část):
* `11000000.10101000.00000001.00001010` (IP)
* `11111111.11111111.11111111.00000000` (Maska)
* **Výsledek binárně:** `11000000.10101000.00000001.00000000`
* **Adresa sítě dekadicky:** `192.168.1.0`

## 4. Výpočet Broadcast adresy
V adrese sítě nastavíme všechny bity hostitelské části (posledních 8 bitů) na `1`:
* **Výsledek binárně:** `11000000.10101000.00000001.11111111`
* **Broadcast dekadicky:** `192.168.1.255`

## 5. Rozsah hostů a počet použitelných adres
* **První použitelný host** (Adresa sítě + 1): `192.168.1.1`
* **Poslední použitelný host** (Broadcast - 1): `192.168.1.254`
* **Počet použitelných hostů:** $2^{(32 - 24)} - 2 = 2^8 - 2 = 256 - 2 = 254$