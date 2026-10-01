# Firmware Senzorvzduchu pro stavebnici LaskaKit SEN55

Upravený firmware FijnStofGroep Leusden (airRohr) pro stavebnici **LaskaKit Senzorvzduchu 8266**
(AirBoard-8266 + Sensirion SEN55 + BME280). Změny proti originálu jsou v `airrohr-firmware/Versions.md`.

## Soubory
| Soubor | K čemu |
|---|---|
| `latest_cz.bin` | česká verze s výchozím nastavením pro stavebnici (doporučeno) |
| `latest_en.bin` | anglická verze |
| `Beta_latest_cz.bin`, `Beta_latest_en.bin` | tytéž soubory pod starším názvem (kvůli existujícím odkazům) |
| `blank_4MB.bin` | smazání celé flash paměti (smaže i konfiguraci) |
| `FlashESP8266.exe`, `esptool.exe` | nástroje pro nahrání (Windows) |

## Nahrání firmwaru
1. Připojte desku USB kabelem a zjistěte číslo COM portu (Správce zařízení).
2. Spusťte `FlashESP8266.exe`, vyberte COM port, nahrajte `blank_4MB.bin` a potom `latest_cz.bin`.
   Z příkazové řádky totéž: `esptool.exe --port COM9 --baud 460800 erase_flash` a `esptool.exe --port COM9 --baud 460800 write_flash 0x0 latest_cz.bin`.
3. Po restartu deska vysílá Wi-Fi síť `airRohr-XXXXXXXX`, heslo `airrohrcfg`. Připojte se k ní a otevřete http://192.168.4.1.
4. Zadejte svou domácí Wi-Fi a uložte. Deska se restartuje a připojí se; její stránku pak najdete na IP adrese, kterou jí přidělil router.

Pozor: nahrání `blank_4MB.bin` smaže uloženou konfiguraci. Pokud chcete jen aktualizovat firmware a konfiguraci zachovat, nahrajte pouze `latest_cz.bin`.

## Výchozí nastavení české verze
- SEN55 zapnutý, ventilátor běží jen během měření (VOC a NOx indexy zůstávají platné).
- Odesílání na Sensor.Community jako senzor SEN5X (PIN 16); při registraci stanice zvolte Sensirion SEN5X.
- BME280 zapnutý.
- VOC a NOx jsou relativní indexy (Sensirion VOC/NOx Index), zobrazují se jen na stránce stanice, na Sensor.Community se neposílají.

## Odkazy
- Návod k sestavení: https://senzorvzduchu.notion.site/Sestaven-L-skaKIT-Airboard-Senzorvzduchu-SEN55-senzor-kvality-ovzdu-3522b45bc7e080fe8f3adc58e858779b
- Původní firmware: https://github.com/FijnStofGroep/sensors-software-Leusden
- Sensor.Community: https://sensor.community/cs/
