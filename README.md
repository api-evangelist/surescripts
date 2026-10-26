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
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
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

Surescripts is a **network operator first and an API provider second** — but as of 2026 it is genuinely both. Updated 2026-08-15:

- **There IS a developer portal now.** Surescripts launched **[docs.surescripts.com](https://docs.surescripts.com)** — its Developer Portal — with an initial release dated **2026-08-06**. It publishes companion guides for E-Prescribing, Eligibility, Formulary, Real-Time Prescription Benefit, Medication History (ambulatory, pharmacies, claims suppliers, populations), Care Coordination, Directory, Connectivity and Record Locator & Exchange. Several sections (Connectivity & Authentication, Network Operations, Error Guidance, Directory, Batch Eligibility, On-Demand Formulary) sit behind a **magic-link login**; the rest is public and machine-readable as markdown at `<page>.md`.
- **Two HTTP APIs are publicly documented.** The **Medication History for Populations API** is HL7 **FHIR R4** — `GET /ext/v1/Communication` returning a Bundle of Patient, Organization, Practitioner, MedicationRequest, MedicationDispense, Medication, Condition and Communication resources, with `_lastUpdated`, `_include`, `_revinclude`, `_page_token` and `_count`. The **Formulary Download API** is four REST endpoints — `/formulary/pbms`, `/formulary/listTypes`, `/formulary/lists`, and a file endpoint — serving NCPDP Formulary & Benefit 3.0 and v60 lists.
- **Still no OpenAPI, no self-serve sign-up, no published pricing.** Nothing parses as OpenAPI/Swagger at any probed path on `surescripts.com`, `www.surescripts.com` or `docs.surescripts.com` (probed 2026-08-15). There is no free API key and no public sandbox account.
- **Authentication is mutual TLS, not OAuth.** Every documented surface requires a **Surescripts-issued client certificate** plus a Participant ID header (`x-participant-id` on Formulary Download; `X-SENDER-UID` + `X-SENDER-UID-QUALIFIER` on the FHIR API). Surescripts runs its own Certificate Authority — a live probe of `care-coordination.surescripts.net` returns a certificate issued by *Surescripts Issuing Certification Authority* under *Surescripts Root Certification Authority*, and resets anonymous connections before any HTTP response.
- **Access is certification-gated.** To connect directly you must become a Surescripts-certified participant — conformance testing against current NCPDP standards, contract approval by the **Surescripts Certification Review Board**, identity proofing, and a DEA third-party audit for EPCS / controlled substances.
- **Most integrators go through middleware.** The practical path for most software vendors is to integrate through a Surescripts-certified EHR, pharmacy system, or middleware/clearinghouse partner that already holds certification, rather than certifying directly.
- **Standards, not a proprietary REST API.** Surescripts transactions ride on published industry standards: **NCPDP SCRIPT 2023011** (NewRx, RxRenewal, RxChange, RxTransfer, RxFill, CancelRx, NewRxRequest, and the ePA transaction set), **NCPDP RTPB v13**, NCPDP Formulary & Benefit 3.0/v60, **X12** 270/271 (eligibility) and 278 (prior authorization), **HL7 FHIR R4**, and the **Direct Standard** for secure clinical messaging.

The two documented HTTP APIs carry real `baseURL` values sourced from the provider's own guides and examples. The remaining entries below are still **honestly modeled** from Surescripts' published solution descriptions and the underlying NCPDP/X12 standards, marked `endpointsModeled: true`. No OpenAPI, plans or FinOps artifacts are asserted, because Surescripts publishes none.

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
