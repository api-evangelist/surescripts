# Surescripts (surescripts)

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

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
