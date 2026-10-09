<!-- TEMPLATE: Hand-written API endpoint reference. Prefer generating reference from OpenAPI; use this when that's not possible, or as a guide page around a generated reference. Copy to api/reference/<resource>.md. Delete this comment. -->

# <Resource name>

<One sentence: what this resource represents.>

---

## <Verb phrase, e.g. "Create a refund">

`<METHOD> /<version>/<path>`

<One or two sentences: what it does, important side effects.>

**Auth:** `<Bearer token>` · **Scopes:** `<scope:write>` · **Idempotent:** <yes, via `Idempotency-Key` header / no> · **Rate limit:** <default / N per minute>

### Path parameters

| Name | Type | Description |
|---|---|---|
| `<id>` | string | <description> |

### Query parameters

| Name | Type | Required | Default | Description |
|---|---|---|---|---|
| `<param>` | integer | | `<20>` | <description, constraints> |

### Request body

| Field | Type | Required | Description |
|---|---|---|---|
| `<field>` | string | ✅ | <description, format, constraints> |
| `<field>` | integer | | <description> |

### Example request

```bash
curl -X <METHOD> https://api.example.com/<version>/<path> \
  -H "Authorization: Bearer <token>" \
  -H "Content-Type: application/json" \
  -d '{
    "<field>": "<value>"
  }'
```

### Example response `<201 Created>`

```json
{
  "id": "<id>",
  "<field>": "<value>",
  "createdAt": "2026-10-09T12:00:00Z"
}
```

### Errors

| HTTP | Code | Meaning | What to do |
|---|---|---|---|
| 400 | `<validation_error>` | <invalid input> | <fix the field named in `error.field`> |
| 404 | `<not_found>` | <resource doesn't exist> | <check the ID> |
| 409 | `<conflict_code>` | <state conflict> | <how to resolve> |

### Side effects

- <Emits `<event.name>` webhook>
- <Sends email to customer>

### Business rules

- [<BR-ID>](<path>): <summary>

---

## <Next operation>

...
