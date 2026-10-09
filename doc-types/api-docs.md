# API Docs

> **What:** How to document APIs (REST, GraphQL, gRPC, events/webhooks) for internal and external consumers.
> **Read when:** you expose an API to anyone other than the code next to it, including other teams and your own frontend.

## TL;DR

- API docs have **two parts**: **reference** (every endpoint, field and error, ideally *generated* from a spec) and **guides** (quick start, auth, common tasks, written by hand).
- Use a **machine-readable spec** as the single source of truth: OpenAPI (REST), SDL (GraphQL), `.proto` (gRPC), AsyncAPI (events).
- Every endpoint needs **a real request and response example**.
- Document **errors, auth, rate limits, pagination, versioning and deprecation** once, centrally.
- **External** API docs usually deserve their own site or portal, separate from internal docs.

---

## The two halves of API docs

| | Reference | Guides |
|---|---|---|
| Question answered | "What exactly does `POST /refunds` accept?" | "How do I issue a refund?" |
| Source | Generated from spec (OpenAPI, SDL, proto) | Handwritten Markdown |
| Organized by | Resource / endpoint / type | Task / use case |
| Completeness | 100%, every field | Common paths only |
| Diátaxis type | Reference | Tutorial + how-to + explanation |

You need both. Reference alone is a dictionary with no grammar. Guides alone leave edge cases undocumented.

---

## Recommended API doc set

```
api/
├── README.md                 overview: what the API does, base URLs, versions, links
├── getting-started.md        first successful call in 5 minutes
├── authentication.md         how to get and use credentials, scopes
├── concepts/                 explanation pages
│   ├── pagination.md
│   ├── idempotency.md
│   ├── errors.md             error format + full error code catalog
│   ├── rate-limits.md
│   └── versioning.md         version policy, deprecation, sunset
├── guides/                   task-oriented how-tos
│   ├── create-an-order.md
│   └── handle-webhooks.md
├── reference/                generated (or a link to the rendered spec)
│   └── openapi.yaml          the source of truth
├── webhooks.md               events, payloads, retries, signature verification
├── sdks.md                   client libraries + examples
└── changelog.md              API-specific changes, breaking changes highlighted
```

---

## Spec-first: OpenAPI

Keep the spec in the repo, review it in PRs and generate the reference from it.

```yaml
openapi: 3.1.0
info:
  title: Payments API
  version: 2.3.0
paths:
  /v2/refunds:
    post:
      summary: Create a refund
      description: Refunds all or part of a captured payment. Refunds over €500 require approval.
      operationId: createRefund
      tags: [Refunds]
      requestBody:
        required: true
        content:
          application/json:
            schema: { $ref: '#/components/schemas/RefundRequest' }
            example: { paymentId: "pay_123", amountCents: 1500, reason: "damaged_item" }
      responses:
        '201': { description: Refund created }
        '409': { description: Payment already fully refunded }
```

| Approach | How | Best when |
|---|---|---|
| **Spec-first (design-first)** | Write the spec, review it, then implement and validate code against the spec | Public APIs, multiple consumers, contract testing |
| **Code-first** | Annotations/attributes in code generate the spec | Internal APIs, fast iteration, one consumer |

Either way, **commit the resulting spec** and render it with a tool such as Redoc, Swagger UI, Scalar or Stoplight Elements.

### Spec formats by API style

| API style | Spec format | Rendered with (examples) |
|---|---|---|
| REST / HTTP | OpenAPI 3.x | Redoc, Swagger UI, Scalar |
| GraphQL | Schema SDL + descriptions | GraphiQL, SpectaQL, GraphQL Voyager |
| gRPC | `.proto` with comments | protoc-gen-doc, Buf Schema Registry |
| Events / messaging | AsyncAPI | AsyncAPI Studio / generator |
| Webhooks | OpenAPI 3.1 `webhooks` or AsyncAPI | as above |

---

## What every endpoint page must include

| Element | Example |
|---|---|
| Method + path | `POST /v2/refunds` |
| One-sentence purpose | "Refunds all or part of a captured payment." |
| Auth & required scopes | `Bearer token`, scope `refunds:write` |
| Path / query / header params | Table: name, type, required, description, constraints |
| Request body schema | Fields, types, required, validation rules |
| **Request example** | Full, copy-pasteable `curl` (+ SDK snippets) |
| **Response example(s)** | Success + the most common errors |
| Status / error codes | Table of codes and what to do about each |
| Side effects | "Sends `refund.created` webhook", "Emails the customer" |
| Idempotency | Header support, retry safety |
| Rate limits | If different from default |
| Business rules | Link to the canonical rule ([business-requirements](business-requirements.md#business-rules-catalog)) |

Template: [templates/api-endpoint-template.md](../templates/api-endpoint-template.md)

---

## Errors

Document the error **format** once and list **every code**:

```json
{
  "error": {
    "code": "refund_exceeds_payment",
    "message": "Refund amount 2000 exceeds remaining refundable amount 1500.",
    "requestId": "req_8f3a..."
  }
}
```

| Code | HTTP | Meaning | What the client should do |
|---|---|---|---|
| `refund_exceeds_payment` | 409 | Amount too large | Lower the amount; fetch payment to see the remaining balance |
| `approval_required` | 202 | Over €500 | Poll refund status or wait for `refund.approved` webhook |

The last column is the one most often missing, and the one consumers need most.

---

## Versioning and deprecation

Document your policy explicitly in `concepts/versioning.md`:

- **How** versions are expressed: URL (`/v2/`), header, or date-based (`2026-10-01`).
- **What counts as breaking**: removed fields, new required params, changed types, changed semantics.
- **Deprecation process**: announce → mark deprecated in spec (`deprecated: true`) → `Deprecation` / `Sunset` headers → remove after N months.
- **Where changes are announced**: API changelog, email, status page.

For multiple live major versions, see [by-version model](../organizing/models/by-version.md).

---

## Event-driven APIs

For Kafka/RabbitMQ topics, webhooks and domain events, document:

| Item | Detail |
|---|---|
| Event name & version | `order.paid.v1` |
| Producer / consumers | Who publishes, who subscribes |
| Channel / topic | `orders.events` |
| Payload schema | AsyncAPI / JSON Schema / Avro |
| Example payload | Full JSON |
| Delivery guarantees | at-least-once, ordering, retries, DLQ |
| When emitted | The exact business trigger |

An **event catalog** (one page or generated site listing every event) is the API reference of event-driven systems.

---

## Internal vs external API docs

| Internal API | External / public API |
|---|---|
| Reference + short README is often enough | Full portal: quick start, guides, SDKs, changelog, status |
| Can live co-located with the service | Separate site or developer portal |
| Can mention internal services | No internal hostnames, architecture or secrets |
| Engineers review | Engineers, technical writer and product review |

See [internal-vs-public](../organizing/internal-vs-public.md).

---

## API doc quality checklist

- [ ] Spec is in the repo and validated in CI (such as `spectral lint`)
- [ ] Every operation has summary, description, and request + response examples
- [ ] Every error code is listed with a "what to do" column
- [ ] Auth guide gets a newcomer to a first successful call in ≤5 minutes
- [ ] Pagination, rate limits, idempotency documented once and linked
- [ ] Breaking changes are flagged in the API changelog
- [ ] Examples are tested (generated from tests, or run in CI)

---

**Related:** [developer-docs](developer-docs.md) · [business-requirements](business-requirements.md) · [page-patterns: reference](../writing/page-patterns.md#reference-page)
**Up:** [Doc types](README.md)
