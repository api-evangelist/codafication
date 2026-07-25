# Codafication (codafication)

Codafication is a Brisbane, Australia insurtech founded in 2015 by Daniel Sandaver and Drew Butler out of a property claims and repair construction business, building software for the general insurance claims supply chain rather than for underwriting or policy administration. Its three products are Crunchwork, a cloud claims and project management platform that acts as a control tower across insurers, assessors, builders, restorers and trades; Virtual Assist, a real-time video streaming and virtual assessment tool used for remote triage of property claims; and Unity Cloud, a GraphQL data and integration layer marketed as a way to retrieve and normalise data across fragmented legacy insurance systems. Named Australian customers and partners include Insurance Australia Group (IAG, announced December 2025 for its property claims supply chain), Suncorp, Urban Utilities and the Australian Building and Construction Group, alongside a Guidewire partner relationship and SOC 2 Type II certification attained in January 2026.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/codafication/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/codafication/refs/heads/main/apis.yml)

## Tags

- Insurance
- Australia
- Insurtech
- Claims
- Claims Management
- Property and Casualty
- FNOL
- Supply Chain
- GraphQL
- Partner Gated

## Timestamps

- **Created:** 2026-07-25
- **Modified:** 2026-07-25

## APIs

None. Codafication publishes no public, self-serve API.

No `developer.`, `developers.`, `docs.` or `api.` subdomain resolves for `codafication.com`, and no API reference, OpenAPI definition, Postman collection, webhook catalog or authentication documentation could be found at any reachable first-party location. Certificate transparency lists exactly seven hosts under the domain — `blog`, `crunchwork`, `go`, `helm`, `help`, `scim`, `unitycloud` — and none of them is a developer or documentation host.

The only integration surface documented publicly is Crunchwork **consuming** third-party APIs on a per-customer, Codafication-configured basis: a Crunchwork-to-NetSuite sync, a one-way Crunchwork-to-Xero integration, the ENData Scope API for publishing quotes and variations, and Opus document submission. Unity Cloud is described in Codafication's own engineering posts as a GraphQL layer over insurance systems, but no public or introspectable GraphQL endpoint exists.

**ACORD posture:** no ACORD reference found. Searches of the knowledge base and the full blog corpus for ACORD, AL3, ACORD XML and NGDS returned zero matches; interchange runs instead through Australian claims-scoping and finance systems.

Australia has the legal machinery for open insurance and no live obligation — the Consumer Data Right was designated to extend to general insurance and then deferred — so nothing forces this platform to expose a public API, and it does not. See [review.yml](review.yml) for the full probe log, HTTP statuses and provenance.

## Links

- **Website:** [https://codafication.com/](https://codafication.com/)
- **Blog:** [https://blog.codafication.com/](https://blog.codafication.com/)
- **Blog RSS:** [https://blog.codafication.com/rss.xml](https://blog.codafication.com/rss.xml)
- **Knowledge Base:** [https://support.codafication.com/en/](https://support.codafication.com/en/)
- **GitHub:** [https://github.com/Codafication](https://github.com/Codafication)
- **LinkedIn:** [https://www.linkedin.com/company/codafication/](https://www.linkedin.com/company/codafication/)

## Maintainers

- Kin Lane — kin@apievangelist.com
