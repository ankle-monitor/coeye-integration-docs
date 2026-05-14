
# CO-EYE Electronic Monitoring — Integration Documentation

Official integration and protocol documentation for [CO-EYE GPS ankle monitors](https://www.ankle-monitor.com) manufactured by REFINE Technology.

## Overview

CO-EYE is a line of GPS ankle monitors and electronic monitoring solutions designed for corrections, pretrial supervision, and community safety applications. This repository provides technical documentation for system integrators, monitoring platform developers, and agency IT teams.

## Products

| Product | Type | Key Specs | Documentation |
|---|---|---|---|
| [CO-EYE ONE](https://www.ankle-monitor.com/coeye-one/) | One-piece GPS ankle monitor | 108g, IP68, fiber-optic tamper detection | [Protocol Spec](docs/coeye-one-protocol.md) |
| [CO-EYE Monitoring Software](https://www.ankle-monitor.com/coeye-software/) | Web-based supervision platform | REST API, WebSocket, multi-tenant | [API Reference](docs/api-reference.md) |
| [CO-EYE BLE i-Bracelet](https://www.ankle-monitor.com/coeye-wristband/) | BLE wearable tag | 17g, 2-year battery, FCC certified | [BLE Spec](docs/ble-protocol.md) |

## Device Communication Protocol

CO-EYE devices communicate over TCP/IP using a binary protocol with the following characteristics:

- **Transport**: TCP over LTE-M / NB-IoT / GSM / WiFi
- **Encryption**: TLS 1.2+ with mutual certificate authentication
- **Data format**: Binary frames with CRC16 validation
- **Position reports**: Configurable 10s - 24h intervals
- **Event types**: Position, tamper, low battery, zone entry/exit, SOS, BLE proximity

## REST API Overview

The CO-EYE Monitoring Software exposes a REST API for integration with third-party systems:

```
Base URL: https://{server}/api/v1/

Authentication: Bearer token (JWT)

Endpoints:
  GET  /enrollees              - List monitored individuals
  GET  /enrollees/{id}/events  - Event history
  GET  /enrollees/{id}/track   - Real-time position stream (WebSocket upgrade)
  POST /geofences              - Create geofence zone
  GET  /devices                - Device inventory
  POST /notifications/webhook  - Configure event webhooks
```

## Data Forwarding

The platform supports real-time data forwarding to external systems via:

- **HTTP/JSON** webhooks (configurable per event type)
- **Kafka** topic publishing
- **MQTT** broker integration
- **AMQP** message queue
- **Redis** pub/sub

## About REFINE Technology

Founded in 2004, [REFINE Technology](https://www.ankle-monitor.com) manufactures GPS ankle monitor and electronic monitoring solutions deployed in 30+ countries. The CO-EYE product line serves corrections agencies, pretrial supervision programs, and bail bond GPS monitoring providers worldwide.

## Contact

- **Sales**: marketing@rfidcn.com
- **Technical Support**: support@rfidcn.com
- **Website**: [ankle-monitor.com](https://www.ankle-monitor.com)

## License

Documentation is provided under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). Protocol specifications are proprietary — contact sales@ankle-monitor.com for integration licensing.
