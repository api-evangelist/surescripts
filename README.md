# Surescripts (surescripts)

Surescripts operates the largest health information network in the United States, connecting prescribers, pharmacies, pharmacy benefit managers (PBMs), health plans, and health systems for e-prescribing, medication history, benefit and eligibility verification, electronic prior authorization, and clinical interoperability. In 2025 the network routed billions of e-prescriptions with 99.998% average uptime.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/surescripts/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/surescripts/refs/heads/main/apis.yml)

## Access model — read this first

Surescripts is a **network operator, not a public API provider.** This entry is an honest, gated stub:

- **No self-serve developer portal.** There is no `developer.surescripts.com` you can sign up for, no free API key, and no public OpenAPI or REST reference. You cannot call Surescripts directly and start sending prescriptions.
- **Access is certification-gated.** To connect directly you must become a Surescripts-certified participant — a conformance process against current NCPDP standards (and a DEA third-party audit for EPCS / controlled substances). Industry reporting describes direct certification as a multi-month-to-multi-year, high-cost effort.
- **Most integrators go through middleware.** The practical path for most software vendors is to integrate through a Surescripts-certified EHR, pharmacy system, or middleware/clearinghouse partner that already holds certification, rather than certifying directly.
- **Standards, not a proprietary REST API.** Surescripts transactions ride on published industry standards: **NCPDP SCRIPT** (NewRx, RxRenewal, RxChange, RxTransfer, RxFill, CancelRx, NewRxRequest, and the ePA transaction set), the **NCPDP Real-Time Prescription Benefit (RTPB)** standard, NCPDP formulary and benefit files, **X12** 270/271 (eligibility) and 278 (prior authorization), and the **Direct** protocol for secure clinical messaging.

Because the transaction surface is not publicly documented, the APIs listed below are **honestly modeled** from Surescripts' published solution descriptions and the underlying NCPDP/X12 standards. Each is marked `endpointsModeled: true`; no base URLs, OpenAPI, plans, rate-limit, or FinOps artifacts are asserted because no public, sourced surface exists.

## Tags

- Healthcare
- E-Prescribing
- Health Information Network
- NCPDP SCRIPT
- Medication History
- Prior Authorization
- Interoperability
- Gated

## Timestamps

- **Created:** 2026-07-04
- **Modified:** 2026-07-04

## APIs (modeled)

### Surescripts E-Prescribing

Routes electronic prescriptions between prescribers and pharmacies over the NCPDP SCRIPT standard — NewRx, RxRenewal, RxChange, RxTransfer, RxFill, CancelRx, and NewRxRequest — plus Electronic Prescribing for Controlled Substances (EPCS).

- **Human URL:** [https://surescripts.com/what-we-do/e-prescribing](https://surescripts.com/what-we-do/e-prescribing)

### Surescripts Medication History

Returns a patient's fills and claims-based medication history aggregated across pharmacies and PBMs to support medication reconciliation at the point of care.

- **Human URL:** [https://surescripts.com/what-we-do](https://surescripts.com/what-we-do)

### Surescripts Eligibility and Formulary

Verifies pharmacy benefit eligibility and returns formulary and benefit coverage details, modeled on X12 270/271 exchange and NCPDP formulary and benefit files.

- **Human URL:** [https://surescripts.com/what-we-do](https://surescripts.com/what-we-do)

### Surescripts Real-Time Prescription Benefit

Returns patient-specific, real-time out-of-pocket drug cost, coverage status, and therapeutic alternatives at the point of prescribing, modeled on the NCPDP RTPB standard.

- **Human URL:** [https://surescripts.com/what-we-do](https://surescripts.com/what-we-do)

### Surescripts Electronic Prior Authorization

Automates electronic prior authorization (ePA) between prescribers and payers/PBMs using the NCPDP SCRIPT ePA transaction set.

- **Human URL:** [https://surescripts.com/prior-authorization-portal-resources](https://surescripts.com/prior-authorization-portal-resources)

### Surescripts Clinical Direct Messaging

Secure, HIPAA-compliant clinical message exchange (Direct Secure Messaging) for care coordination, transitions of care, and referrals.

- **Human URL:** [https://surescripts.com/what-we-do](https://surescripts.com/what-we-do)

### Surescripts Record Locator and Exchange

Locates where a patient has clinical records across the network and enables retrieval of relevant clinical documents to inform care.

- **Human URL:** [https://surescripts.com/what-we-do](https://surescripts.com/what-we-do)

## Pricing

Not publicly published. Surescripts uses negotiated, subscription- and transaction-based pricing that varies by service module, organization size, and volume; for routing and eligibility transactions, pharmacies and PBMs pay a per-transaction fee. Direct certification also carries its own cost and time investment. Terms are provided on request through Surescripts sales and partnership channels.

## Common Properties

- [LinkedIn](https://www.linkedin.com/company/surescripts)
- [Website](https://surescripts.com)
- [Documentation](https://surescripts.com/what-we-do)
- [Certifications](https://surescripts.com/why-surescripts/certifications-and-accreditations)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
