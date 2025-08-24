# IoT Billing – Demo (Architecture & Flow)

**Goal:** illustrate a simplified daily CDR → rating → monthly invoicing pipeline used in B2B IoT billing.

## Daily File Types (examples)
- GPRS (bytes), VOICE (seconds), SMS (count), SIMDELTA (status), CSPI (mappings)

## Processing (daemons/jobs)
1. **Reader** – filename/columns/dup checks
2. **Validator** – record-level duplicate/format checks
3. **Rating Engine** – maps rate plans via tariff ↔ CSP ↔ customer, writes:
   - `accumulated_usage_data` (rollups)
   - `detailed_usage_data` (per event)
   - rejects → `rejected_events`

## Monthly Invoicing (high level)
- SIM RC, Discounts, Customer RC, One-time, Tier charges
- Invoice PDF/ISD + CSV extracts

## Data Model (sample tables)
- `customer_information`, `sim_information`, `tariff_information`,
  `csp_tariff_mapping`, `accumulated_usage_data`, `detailed_usage_data`

> This repo uses **dummy data** only.
