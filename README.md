# Snelnotuleren API Documentation

Welkom bij de Snelnotuleren API documentatie. Deze API stelt je in staat om automatische notulen te integreren in je eigen applicatie.

## Authenticatie

De API gebruikt een combinatie van client credentials en Bearer tokens voor authenticatie:

1. Vraag client credentials aan via het dashboard
2. Gebruik deze credentials om een token op te vragen
3. Gebruik het token voor API requests

```bash
# Token ophalen
curl -X POST https://api.snelnotuleren.nl/api/v1/auth/token \
  -H "X-Client-ID: your_client_id" \
  -H "X-Client-Secret: your_client_secret"
```

## Quick Start

```python
from snelnotuleren import SnelNotulerenClient

client = SnelNotulerenClient(
    client_id='your_client_id',
    client_secret='your_client_secret'
)

order_id = client.create_order(
    file_path='vergadering.mp3',
    email='contact@bedrijf.nl',
    context='Maandelijkse vergadering'
)
```

## Endpoints

### POST /api/v1/auth/token
Verkrijg een access token met je client credentials.

### POST /api/v1/create-order
Maak een nieuwe order aan voor het verwerken van een audio bestand.

## Rapport Types & Prijzen

- `transcriptie` (€5) - Volledige transcriptie
- `korte_notulen` (€10) - Beknopte notulen
- `middel_notulen` (€20) - Gebalanceerde notulen
- `lange_notulen` (€25) - Uitgebreide notulen

## SDK's

- [Python SDK](https://github.com/snelnotuleren/python-sdk)

## Support

Voor support, email naar support@snelnotuleren.nl