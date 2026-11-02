# Changelog

All notable changes to this repository are documented here. Format follows Keep a Changelog; versioning is semantic.

## [0.1.1] - 2026-09-02

### Changed
- ISIM-CR-03 golden path calibration: resource capacities provisioned for stability at the declared demand (Validation Agent 12, Credit Analyst 15, Fulfillment Worker 15); order-volume control bound to the arrival rate; scenarios updated accordingly. Surfaced by the first executable replay.

## [0.1.0] - 2026-08-31

### Added
- Initial repository seed for the iSimulator organization.

## [0.2.0] - 2026-08-31

### Added
- otchere-order-to-cash/: golden-path model (simulation.json) with 8-stage process, 7 resources, 3 controls, 6 metrics, 3 scenarios; validated against itwin-sim-0.1.0 schema.
