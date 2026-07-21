# Wake-on-LAN

## Cel

Zdalne wybudzanie hostów przez LAN. Działanie wymaga jednocześnie poprawnej konfiguracji BIOS/UEFI, karty sieciowej i systemu.

## AI-node

Interfejs:

```bash
ip -br link
sudo ethtool enp1s0 | grep -i wake-on
```

Oczekiwane:

```text
Supports Wake-on: ...g
Wake-on: g
```

Jeżeli po restarcie widnieje `Wake-on: d`, ustaw:

```bash
sudo ethtool -s enp1s0 wol g
```

Następnie utrwal ustawienie w konfiguracji systemd-networkd lub jednostce systemd i sprawdź je po restarcie.

## HomeLab

Adres MAC interfejsu Ethernet:

```text
18:60:24:94:81:ea
```

Konfiguracja systemowa została wykonana, ale wybudzenie po pełnym wyłączeniu nadal wymaga weryfikacji ustawień BIOS/UEFI.

## Wysłanie pakietu z macOS

```bash
brew install wakeonlan
wakeonlan ADRES_MAC
```

Pakiet należy wysłać z urządzenia w tej samej sieci LAN. Tailscale sam w sobie nie przekazuje broadcastu WoL; do wybudzania spoza domu potrzebny jest stale działający host pośredniczący w LAN.

## Test

1. zapisz adres MAC,
2. wyłącz host poleceniem `sudo poweroff`,
3. sprawdź, czy diody interfejsu Ethernet pozostają aktywne,
4. wyślij magic packet,
5. sprawdź dostępność przez `ping` i SSH.

Nie uznawaj konfiguracji za zakończoną, dopóki test nie powiedzie się po pełnym wyłączeniu i ponownym uruchomieniu.