# Orders Guide

Deze guide legt uit hoe je orders kunt aanmaken en bestanden kunt uploaden.

## Order Types & Prijzen

| Type | Prijs | Beschrijving |
|------|-------|--------------|
| transcriptie | €5 | Volledige transcriptie van de audio |
| korte_notulen | €10 | Beknopte samenvatting met hoofdpunten |
| middel_notulen | €20 | Gebalanceerde notulen met details |
| lange_notulen | €25 | Uitgebreide notulen met alle details |

## Order Aanmaken

1. **Order Request**
```bash
curl -X POST https://api.snelnotuleren.nl/api/v1/create-order \
  -H "Authorization: Bearer your_token" \
  -H "Content-Type: application/json" \
  -d '{
    "fileName": "vergadering.mp3",
    "email": "contact@bedrijf.nl",
    "context": "Bestuursvergadering",
    "reportType": "transcriptie",
    "smart_detection": true,
    "speaker_diarization": true,
    "speaker_count": 4
  }'
```

2. **Response**
```json
{
  "orderId": "ord_123abc",
  "uploadUrl": "https://storage.googleapis.com/...",
  "status": "success",
  "paymentRequired": false
}
```

3. **Bestand Uploaden**
```bash
curl -X PUT "upload_url_from_response" \
  --upload-file vergadering.mp3 \
  -H "Content-Type: application/octet-stream"
```

## Optionele Parameters

- `smart_detection`: Automatische agendapunt detectie
- `speaker_diarization`: Sprekerherkenning
- `speaker_count`: Aantal verwachte sprekers
- `delayedDelivery`: Vertraagde levering