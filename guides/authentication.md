# Authenticatie Guide

Deze guide legt uit hoe je de Snelnotuleren API kunt authenticeren.

## Client Credentials

Om de API te gebruiken heb je client credentials nodig:
- Client ID
- Client Secret

Deze kun je verkrijgen via het [dashboard](https://dashboard.snelnotuleren.nl).

## Token Ophalen

Gebruik je credentials om een access token op te halen:

```bash
curl -X POST https://api.snelnotuleren.nl/api/v1/auth/token \
  -H "X-Client-ID: your_client_id" \
  -H "X-Client-Secret: your_client_secret"
```

De response bevat je access token:
```json
{
  "access_token": "eyJ0eXAi...",
  "expires_in": 3600,
  "token_type": "Bearer"
}
```

## Token Gebruiken

Gebruik het token in de Authorization header:
```bash
curl -X POST https://api.snelnotuleren.nl/api/v1/create-order \
  -H "Authorization: Bearer eyJ0eXAi..." \
  -H "Content-Type: application/json" \
  -d '{
    "fileName": "vergadering.mp3",
    "email": "contact@bedrijf.nl",
    "context": "Maandelijkse vergadering",
    "reportType": "transcriptie"
  }'
```

## Token Vernieuwing

Tokens verlopen na 1 uur. Haal een nieuw token op als je een 401 response krijgt.