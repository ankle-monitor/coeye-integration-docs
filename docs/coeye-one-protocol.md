
```markdown
# CO-EYE ONE — Device Communication Protocol

## Overview

The CO-EYE ONE GPS ankle monitor communicates with the monitoring server
using a binary protocol over TCP/IP.

## Connection Modes

| Mode | Transport | Typical Battery Life | Use Case |
|---|---|---|---|
| LTE Standalone | LTE-M / NB-IoT direct | 7 days | Outdoor, independent tracking |
| WiFi-Directed | WiFi to server via repeater | 20 days | Indoor, cellular dead zones |
| BLE-Connected | BLE to smartphone/HouseStation | 180 days | Home, office, low-power mode |

The device automatically switches between modes based on environment
(no manual intervention required).

## Frame Structure

    [STX 2B] [Length 2B] [MsgType 1B] [Payload NB] [CRC16 2B] [ETX 2B]

- STX: Start marker (0xAA55)
- Length: Total frame length including header
- MsgType: Message type identifier
- CRC16: CCITT CRC-16 over Length + MsgType + Payload
- ETX: End marker (0x55AA)

## Position Report Fields

| Field | Bytes | Description |
|---|---|---|
| Timestamp | 4 | Unix epoch (UTC) |
| Latitude | 4 | IEEE 754 float, degrees |
| Longitude | 4 | IEEE 754 float, degrees |
| Altitude | 2 | Meters above sea level |
| Speed | 2 | km/h × 10 |
| Heading | 2 | Degrees × 10 |
| HDOP | 1 | Horizontal dilution × 10 |
| Satellites | 1 | Number of satellites used |
| Battery | 1 | Percentage (0-100) |
| Signal | 1 | Cellular signal strength (0-31) |

## Security

- TLS 1.2+ with mutual certificate authentication
- AES-128/256 payload encryption
- Anti-replay protection via sequence numbers
- Anti-spoofing: GNSS carrier-to-noise ratio monitoring

For protocol integration licensing, contact support@rfidcn.com.
```
