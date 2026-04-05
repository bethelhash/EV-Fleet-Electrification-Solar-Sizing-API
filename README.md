# EV Fleet Electrification & Solar Sizing API

[![RapidAPI](https://img.shields.io/badge/RapidAPI-FF0000?style=for-the-badge&logo=rapidapi&logoColor=white)](https://rapidapi.com/bethelnedi/api/ev-fleet-electrification-solar-sizing-api)
[![Live Docs](https://img.shields.io/badge/Live%20Docs-Hugging%20Face-4285F4?style=for-the-badge&logo=huggingface&logoColor=white)](https://amfumu-ev-fleet-api.hf.space/docs)
[![License](https://img.shields.io/badge/License-MIT-yellow.svg?style=for-the-badge)](LICENSE)
[![Data Sources](https://img.shields.io/badge/Data%20Sources-2024--2025-blue?style=for-the-badge)](https://rapidapi.com/bethelnedi/api/ev-fleet-electrification-solar-sizing-api)

**The only API that models commercial fleet electrification end-to-end**

Most fleet tools give you a vehicle range estimate and nothing else. This API delivers the **complete infrastructure picture** — charging load, peak demand, utility demand charges, EVSE costs, vehicle & charger incentives, managed charging savings, on-site solar sizing to offset the entire fleet load, and 10-year financials — with **every single number traceable** to a named regulatory or research source.

---

### What problem it solves (pain point)
Energy consultants, fleet managers, and sustainability teams waste weeks (and often $50,000+) building custom spreadsheets just to understand the full picture of electrifying a commercial fleet. This API eliminates that pain by returning ready-to-use, investment-grade data in one call.

### The methodology (cite the source)
Every calculation is built on peer-reviewed, official sources (no black-box AI):
- NREL EVI-Pro 2023 + DOE AFDC 2024 (charging load)
- SAE J1772:2023 + NREL EVI-Pro 2023 (peak demand & chargers)
- OpenEI Utility Rate Database 2024 (demand charges)
- NREL/TP-7A40-87610 + BloombergNEF 2024 (EVSE costs)
- IRA 2022 §30C, §45W, §48E + IRS Notices 2023-29/2023-38 (incentives)
- PVWatts V8 + NASA POWER MERRA-2 + NREL/TP-6A20-62641 (solar sizing & production)

Full transparency: `/reference/methodology` returns every equation and source document.

### What you get back (specific outputs)
A single `/fleet/full` call returns **7 complete data sections** plus a full citation register:

| Output | Methodology (simplified) | Primary Sources |
|--------|--------------------------|-----------------|
| Annual fleet charging load (kWh) | `daily_miles ÷ EPA efficiency ÷ charging_eff × fleet × 365` | NREL EVI-Pro 2023; DOE AFDC 2024 |
| Fleet peak demand added (kW) | `simultaneous_vehicles × charger_power_kw` | SAE J1772:2023; NREL EVI-Pro 2023 |
| Annual demand charge increase ($) | `peak_kw × rate_usd/kW/mo × 12` | OpenEI Utility Rate Database 2024 |
| EVSE hardware + install cost | Per-charger benchmarks by type | NREL/TP-7A40-87610; BloombergNEF 2024 |
| EVSE tax credit (§30C) | 6% base; 30% in qualifying census tracts | IRA 2022 §30C; IRS Notice 2023-29 |
| Vehicle purchase credit (§45W) | $7,500 light duty; $40,000 heavy duty | IRA 2022 §45W |
| Solar system size to offset fleet | PVWatts V8 capacity factor model | NASA POWER MERRA-2; NREL/TP-6A20-62641 |
| Solar capital cost + ITC (§48E) | $1.65/W + 30% base + up to 20% adders | Ramasamy et al. 2023; IRA 2022 §48E |

**Additional outputs**: managed charging savings model, 10-year cash-flow summary, Scope 1 emission reductions, and complete citation register.

### Who it's for (target audience)
- Fleet managers planning EV transitions for **10–500 vehicles**
- Energy consultants building business cases for fleet electrification
- ESCOs sizing on-site solar + BESS alongside fleet charging
- Sustainability teams calculating Scope 1 emission reductions
- Developers building fleet management, energy, or decarbonization applications

### Call to action
**Start modeling complete fleet electrification in one API call** → [Subscribe on RapidAPI](https://rapidapi.com/bethelnedi/api/ev-fleet-electrification-solar-sizing-api)

Free tier available for testing. Pro & Enterprise plans unlock unlimited calls + priority support.

---

## Multi-Jurisdiction Coverage
- **United States**: All 50 states with individual demand charge rates from OpenEI. Federal incentives §30C (EVSE), §45W (vehicles), §48E (solar).
- **United Kingdom**: Workplace Charging Scheme (75% of socket cost up to £350/socket). Enhanced Capital Allowances — 100% first-year depreciation on zero-emission vehicles.
- **Australia**: ARENA/CEFC fleet electrification grants (~50% of eligible EVSE costs). FBT exemption for EVs. LZEV state rebates.
- **India**: FAME II commercial vehicle subsidy (₹10,000–₹50,000/kWh by category).
- **South Africa & Singapore**: Demand charge equivalents and applicable local incentives.

---

## EPA-Validated Vehicle Database
| Vehicle                        | Category          | Efficiency (mi/kWh) | §45W Credit |
|--------------------------------|-------------------|---------------------|-------------|
| Ford E-Transit Cargo           | Light duty van    | 2.0                 | $7,500      |
| Ford E-Transit 350 HD          | Medium duty van   | 1.6                 | $40,000     |
| Ford F-150 Lightning Fleet     | Light duty pickup | 2.3                 | $7,500      |
| Rivian R1T Fleet               | Light duty pickup | 2.3                 | $7,500      |
| Workhorse C-1000               | Medium duty van   | 1.25                | $40,000     |
| Lightning eMotors ZEV3         | Medium duty truck | 1.25                | $40,000     |
| Freightliner eCascadia         | Class 8 heavy duty| 0.5                 | $40,000     |
| Lion8 Electric Truck           | Class 8 heavy duty| 0.52                | $40,000     |
| Custom                         | User-defined      | User input          | User input  |

*Source: EPA fueleconomy.gov (2024); manufacturer fleet catalogues*

## Supported Charger Types (SAE J1772:2023)
- Level 1 (1.4 kW)
- Level 2 Standard (7.2 kW)
- Level 2 High (11.5 kW)
- Level 2 Max (19.2 kW)
- DCFC 50 kW / 150 kW / 350 kW
- MCS 500 kW (heavy duty)

---

## Pricing Plans (RapidAPI)
| Plan          | Price       | Rate Limit           | Monthly Quota | Endpoints Allowed          | Support                     |
|---------------|-------------|----------------------|---------------|----------------------------|-----------------------------|
| **Free**      | $0/month    | 5 requests/min       | 50/month      | /fleet/quick + reference   | Community                   |
| **Pro**       | $79/month   | 1,000 requests/hour  | Unlimited     | All                        | Standard                    |
| **Enterprise**| $249/month  | Unlimited            | Unlimited     | All + priority             | Dedicated (support@solartruth.app) |

---

## Endpoint Reference

**Live Interactive Docs:** [https://amfumu-ev-fleet-api.hf.space/docs](https://amfumu-ev-fleet-api.hf.space/docs)

### POST `/fleet/quick` (Free tier)
Quick feasibility estimate. No site data needed.

### POST `/fleet/full` (Pro & Enterprise)
Complete end-to-end analysis including solar sizing.

### Reference Endpoints (all tiers)
- `GET /reference/vehicles`
- `GET /reference/chargers`
- `GET /reference/demand-rates`
- `GET /reference/climate-zones`
- `GET /reference/incentives`
- `GET /reference/methodology`

---

**Data Integrity & Transparency**  
Every output value is 100% traceable. No black-box calculations.

**Ready to integrate?**  
Star this repo → Subscribe on RapidAPI → Start building bulletproof fleet electrification proposals today.

Questions or Enterprise onboarding? Email **support@solartruth.app**

*Last updated: April 2026 • Data sources current through 2024–2025 publications*
