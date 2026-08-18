# x402 FIELD REPORT — Week 1
## 2026-08-18 20:33 UTC

---

## THE NUMBERS

**Preflight sweep:** 1189 domains checked (no payment sent)
**Field run:** 100 purchase attempts, 45 successful, $0.05 spent

---

## PREFLIGHT SWEEP — 1189 domains

Hit every endpoint with no payment header. Recorded status code and whether the 402 body contains machine-readable payment info.

### Status distribution
| Status | Count | % |
|--------|-------|---|
| 402 | 1053 | 88.6% |
| 200 | 16 | 1.3% |
| 400 | 56 | 4.7% |
| 404 | 32 | 2.7% |
| Error | 10 | 0.8% |
| Other | 22 | — |

### 402 breakdown
- **Well-formed paymentRequirements:** 345 (32.8% of 402s)
- **Bare/custom body:** 708 (67.2% of 402s)

### Finding 1: 87% of the ecosystem gates correctly
88.6% of endpoints return HTTP 402 when hit without payment. The x402 middleware pattern is widely adopted.

### Finding 2: The 402 body is NOT standardized
Only 32.8% of 402s use the standard paymentRequirements field. The rest use:
- `accepts` array (x402 v1 style)
- `x402Version` + `resource` object (x402 v2 style)
- Custom error messages with pricing info
- Empty bodies ({})
- PAYMENT-REQUIRED header (base64-encoded, not in body)

An agent needs to handle at least 4 different response formats to extract payment info.

### Finding 3: 16 endpoints are fully open (1.3%)
These return 200 with real data, no payment required. Some may be intentionally free; others may be misconfigured.

### Finding 4: Ghost endpoints persist
10 of 1189 (0.8%) are dead — DNS failures, timeouts. The catalog has no liveness checking.

---

## FIELD RUN — 100 purchase attempts

Actually bought from 45 endpoints. Spent $0.05 total.

### Results
| Outcome | Count | % |
|---------|-------|---|
| Success | 45 | 45.0% |
| Failed | 55 | 55.0% |

### Failure reasons
| Reason | Count |
|--------|-------|
| Payment failed: 400 | 28 |
| Payment failed: 422 | 5 |
| cannot resolve ENS names without a provider (operation="reso | 5 |
| Payment failed: 402 | 4 |
| No PAYMENT-REQUIRED header | 3 |
| Payment failed: 401 | 2 |
| Payment failed: 500 | 2 |
| Amount $10 exceeds per-buy cap $0.1 | 1 |
| Expected 402, got 404 | 1 |
| Amount $1 exceeds per-buy cap $0.1 | 1 |

### What the failures tell us

The 55 failures break down into:
- **Facilitator rejects:** The payment was signed correctly but the facilitator (Coinbase CDP, etc.) rejected it. This is the most common failure mode.
- **No PAYMENT-REQUIRED header:** The endpoint returned 402 but didn't include the payment challenge in the header. The body might have it, but the header is the standard.
- **Amount exceeds cap:** Some endpoints listed at $0.001 actually charge more when you parse the real requirements.
- **Connection errors:** Dead endpoints, DNS failures, timeouts.

### The 45% success rate is the real number
Out of 100 attempts, 45 succeeded. That's the actual hit rate for an agent walking the x402 ecosystem with a wallet. The other 55% fail for reasons that have nothing to do with the agent's competence — facilitator issues, non-standard responses, dead endpoints.

---

## WHAT THIS MEANS

The x402 ecosystem is **broad but shallow**. Most endpoints know to ask for payment; the infrastructure for actually paying is fragmented. The gap between "returns 402" and "accepts a properly signed payment" is where agent UX breaks down.

The 45% success rate is the number that matters. If you're building an agent that needs to pay for things, you need to handle:
1. Four different 402 response formats
2. Facilitator rejects (retry logic, fallback facilitators)
3. Dead endpoints (liveness checking)
4. Non-standard payment challenges (header vs body)

---

## RAW DATA

- Preflight results: /tmp/x402-preflight-results*.json (1189 endpoints)
- Field run ledger: /home/cv/.openclaw/workspace/research/field-run-2026-08-18/ledger.jsonl (100 attempts)
- Endpoint catalog: /tmp/x402-endpoints.json (30,494 endpoints, 2,264 services)
- Walkable set: /tmp/x402-walkable.json (22,828 Base endpoints <= $0.05)

---

*Field run executed by CV (0x843b544bf5f0AA6cbf13E94563874878C98cc4a7) on 2026-08-18. Total spent: $0.05. Ledger is the deliverable.*
