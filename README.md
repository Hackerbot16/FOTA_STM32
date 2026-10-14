# OTA / FOTA Firmware Update

Cellular over-the-air (FOTA) firmware update for the Kriotek VTS tracker.

- **MCU:** STM32G0B1CETx
- **Modem:** Quectel EC200U (AT commands over UART)
- **IDE:** STM32CubeIDE + STM32CubeMX

## Repository layout

| Folder | Purpose |
|---|---|
| `fota_bootloader/` | Segment 1: FOTA application / bootloader |
| `app1/` | Segment 2: application slot 1 |
| `app2/` | Segment 3: application slot 2 |
| `default_config/` | Segment 4: default configuration |
| `docs/` | Technical documentation |

## Flash memory map

| Segment | Contents | Start address | Size |
|---|---|---|---|
| 1 | FOTA app | TODO | TODO |
| 2 | APP1 | TODO | TODO |
| 3 | APP2 | TODO | TODO |
| 4 | Default config | TODO | TODO |

## Update flow

TODO: describe the round-robin update flow (download via modem, write to the next slot, verify, switch).

## Build

1. Open each segment folder in STM32CubeIDE (`File > Open Projects from File System`).
2. If `Drivers/` is not committed, open the `.ioc` and click *Generate Code*.
3. Copy `config.example.h` to `config.h` and fill in your server URL, APN, etc. (`config.h` is git-ignored).
4. Build and flash each segment. Each uses its own linker script flash origin and `VECT_TAB_OFFSET`.

## Notes

- Never commit credentials, tokens or compiled binaries. Use GitHub Releases for `.bin` files.
