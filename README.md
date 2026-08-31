# iSimulator: examples

Worked examples of Organization iTwins.

**Version:** 0.1.0
**Status:** Draft
**Last Updated:** 2026-08-31

---

## Scope

Concrete, inspectable Organization iTwin examples usable by digital architects and domain experts. Each example states its iTwin model, scenario configuration, and expected simulation observations.

## Status

## Golden Path (ISIM-CR-01 section 19)

**OTCHERE Order-to-Cash / Fulfillment** is the canonical architectural acceptance example: Order -> Validation -> Credit -> Inventory -> Fulfillment -> Shipment -> Invoice -> Payment. Each stage carries Resource, Capacity, Processing Time, Queue, Policy, Rule, Failure Rate, SLA, Cost. Acceptance progression: Observe, Manipulate, Simulate, Compare, Explain, Forecast, Optimize, Report. Every subsequent CR must progressively satisfy this golden path.


v0.1.0 seed. Structure and content evolve via versioned changes; see [isimulator/openspec](https://github.com/isimulator/openspec) for requirements and [isimulator/docs](https://github.com/isimulator/docs) for design context.
