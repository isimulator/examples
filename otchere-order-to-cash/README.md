# OTCHERE Order-to-Cash / Fulfillment: Golden Path

**Version:** 0.1.0
**Status:** Reference model
**Authority:** ISIM-CR-01 section 19; ISIM-CR-02 section 22

---

## What this is

The canonical architectural acceptance example for iSimulator: an Order-to-Cash operation modeled entirely from Enterprise Simulation Primitives (ISIM-CR-02 R01), declared in the engine-neutral simulation specification (R03), targeting the `discrete-event` execution capability (R05) with no engine named anywhere in the model.

## The operation

```
Order -> Validation -> Credit Check -> Inventory Allocation -> Fulfillment -> Shipment -> Invoicing -> Payment
```

| Stage | Duration | Resource | Capacity | Failure |
|-------|----------|----------|----------|---------|
| Order Validation | 3 min (triangular) | Validation Agent | 12 | 1% |
| Credit Check | 5 min (triangular) | Credit Analyst | 15 | 2% |
| Inventory Allocation | 2 min | Allocation System | 50 | 0.5% |
| Fulfillment | 6 min (triangular) | Fulfillment Worker | 15 | 1% |
| Shipment | 4 min | Carrier | 20 | 2% |
| Invoicing | 2 min | Billing System | 50 | 0.5% |
| Payment | 1 min | Payment Gateway | 100 | 0.3% |

Arrival: 100 orders/hour (Poisson). Horizon: 30 days. Metrics: throughput, cycle time, backlog, SLA, utilization, cost.

## Scenarios

| Scenario | Change |
|----------|--------|
| baseline | none |
| demand-plus-20 | order volume control 100 -> 120/hour (arrival rate binding) |
| capacity-plus-5 | fulfillment workers 15 -> 20 |

## Controls (UI dials map here)

Order Volume (10-300/hour; bound to the arrival rate), Fulfillment Capacity (1-40 workers), Automation (0-100%).

Calibration note (ISIM-CR-03): capacities were provisioned during the first executable replay so the operation is stable at the declared 100 orders/hour demand with headroom for the +20% scenario. The order-volume control binds to `model.arrivals[order-arrival].rate.value`; the schema does not yet support parameter indirection for arrival rates (recorded as a gap for a future CR).

## Acceptance (ISIM-CR-02 section 22)

A solution engineer composes this model from primitives, runs it, changes fulfillment capacity, re-runs, and compares baseline vs scenario: without knowing which engine executed it. Execution arrives with ISIM-CR-03 (Reference Engine Integration).
