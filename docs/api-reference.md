```markdown
# CO-EYE Monitoring Software — REST API Reference

Base URL: `https://{your-server}/api/v1/`

## Authentication

All API requests require a Bearer token (JWT) in the Authorization header:

    Authorization: Bearer {your-jwt-token}

Tokens are issued by the CO-EYE Monitoring Software admin panel.
Token lifetime: 24 hours (configurable).

## Endpoints

### Enrollees (Monitored Individuals)

| Method | Path | Description |
|---|---|---|
| GET | /enrollees | List all enrollees with pagination |
| GET | /enrollees/{id} | Get enrollee details |
| GET | /enrollees/{id}/events | Get event history |
| GET | /enrollees/{id}/positions | Get position history |

### Devices

| Method | Path | Description |
|---|---|---|
| GET | /devices | List all devices |
| GET | /devices/{id} | Get device details and status |
| GET | /devices/{id}/diagnostics | Get device health data |

### Geofences

| Method | Path | Description |
|---|---|---|
| GET | /geofences | List geofence zones |
| POST | /geofences | Create a geofence zone |
| PUT | /geofences/{id} | Update geofence |
| DELETE | /geofences/{id} | Delete geofence |

### Notifications

| Method | Path | Description |
|---|---|---|
| POST | /notifications/webhook | Register webhook endpoint |
| GET | /notifications/webhook | List registered webhooks |

## Event Types

| Event Code | Name | Description |
|---|---|---|
| POS | Position Update | Scheduled GPS position report |
| TAM | Tamper Alert | Fiber-optic strap or case tamper detected |
| LBT | Low Battery | Battery below configured threshold |
| ZIN | Zone Entry | Enrollee entered geofenced area |
| ZOT | Zone Exit | Enrollee exited geofenced area |
| SOS | Emergency | SOS button pressed on device or app |
| BLE | BLE Proximity | BLE beacon proximity change detected |

## Rate Limits

- Standard: 100 requests/minute per API key
- Bulk export: 10 requests/minute

For full API documentation and SDKs, contact support@rfidcn.com.
```
