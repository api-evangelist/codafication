# Codafication (codafication)

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

Codafication is a Brisbane, Australia insurtech founded in 2015 by Daniel Sandaver and Drew Butler out of a property claims and repair construction business, building software for the general insurance claims supply chain rather than for underwriting or policy administration. Its three products are Crunchwork, a cloud claims and project management platform that acts as a control tower across insurers, assessors, builders, restorers and trades; Virtual Assist, a real-time video streaming and virtual assessment tool used for remote triage of property claims; and Unity Cloud, the GraphQL data, extension and integration platform the other two are built on. Named Australian customers and partners include Insurance Australia Group (IAG, announced December 2025 for its property claims supply chain), Suncorp, Urban Utilities and the Australian Building and Construction Group, alongside a Guidewire partner relationship and SOC 2 Type II certification attained in January 2026.

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
- Webhooks
- SDK
- Extensions
- Multi Tenant
- Partner Gated

## Timestamps

- **Created:** 2026-07-25
- **Modified:** 2026-07-25

## APIs

### Unity Platform API — [docs.unitycloud.io](https://docs.unitycloud.io/)

Codafication does publish a public API reference — on a **second registrable domain**, which is why an earlier pass that enumerated only `%.codafication.com` concluded it did not. [https://docs.unitycloud.io/](https://docs.unitycloud.io/) is the complete Unity Platform SDK reference, reachable anonymously.

- **GraphQL** is the primary surface: one collated endpoint, where the schemas of every installed extension are merged centrally on the fly, with auto-generated strongly typed `where` clauses, RBAC and multi-tenancy applied by default. Two client generations are documented — `client` (older) and `clientV2` (new extensions).
- **REST** exists as an extension-scoped projection on the same gateway: `https://<CloudDomain>/graphql/v2/<extensionName>/<endpoint>` (private, authorization header required) and `.../graphql/v2/public/<extensionName>/<endpoint>` (public, no Unity authorization).
- **Webhooks** subscribe to Unity *mutations* and deliver the result of a **caller-supplied GraphQL query** as the payload — not a fixed id-only body — which removes the follow-up read a conventional webhook forces. **Logic hooks** (`beforeHook`/`afterHook`) run in-process against a named mutation; a before hook can block or fail it, an after hook cannot roll it back.
- **Auth** is Auth0-backed (SAML 2.0 / Active Directory connections) for users, Unity API tokens from the in-product Developer Portal for platform calls, and a pre-shared `authenticationSecret` per extension.
- **SDKs** are `@teamcodafication/unity-portal-sdk` (React frontend) and `@teamcodafication/unity-sdk` (Node.js backend, built on graphql-yoga over express) — both documented, both 404 on the public npm registry.

No `baseURL` is recorded in `apis.yml` on purpose: the host is the customer's own tenant Cloud domain, not a shared production host, and none was fabricated.

**What is still missing** (re-verified this round against every host): no OpenAPI, Swagger or AsyncAPI document anywhere first-party; no anonymously introspectable GraphQL endpoint — `/graphql` POSTs return the site bot challenge, not a GraphQL response; no public event catalog (it lives in the in-product Developer Portal); no Postman collection; no public registry distribution of the SDKs; no self-serve signup; no status page (`codafication.statuspage.io` is unclaimed and redirects to statuspage.io); no SLA, deprecation policy, roadmap or developer changelog; no named OAuth scopes, error-code registry, rate-limit documentation or idempotency contract. The reference itself carries a `Last-Modified` of 2022-03-24.

The other public integration surface is Crunchwork **consuming** third-party APIs on a per-customer, Codafication-configured basis: a Crunchwork-to-NetSuite sync, a one-way Crunchwork-to-Xero integration, the ENData Scope API for publishing quotes and variations, and Opus document submission.

**ACORD posture:** no ACORD reference found. Searches of the knowledge base and the full blog corpus for ACORD, AL3, ACORD XML and NGDS returned zero matches; interchange runs instead through Australian claims-scoping and finance systems.

Australia has the legal machinery for open insurance and no live obligation — the Consumer Data Right was designated to extend to general insurance and then deferred — so nothing forces this platform to open further than it already has. See [review.yml](review.yml) for the full probe log, HTTP statuses and provenance.

## Artifacts

- [authentication/codafication-authentication.yml](authentication/codafication-authentication.yml) — Auth0, Unity tokens, extension secrets, RBAC
- [conventions/codafication-conventions.yml](conventions/codafication-conventions.yml) — GraphQL/REST semantics, filtering, error envelope, versioning
- [asyncapi/codafication-unity-webhooks.yml](asyncapi/codafication-unity-webhooks.yml) — webhook and logic-hook surface
- [data-model/codafication-data-model.yml](data-model/codafication-data-model.yml) — UnityUser, Tenant, roles, permissions, extensions
- [packages/codafication-packages.yml](packages/codafication-packages.yml) — the two SDKs plus the one public npm package
- [cli/codafication-cli.yml](cli/codafication-cli.yml) — Create Extension CLI and setup scripts
- [components/codafication-components.yml](components/codafication-components.yml) — UnitySDK wrapper, UnityBar, Device Controller
- [sandbox/codafication-sandbox.yml](sandbox/codafication-sandbox.yml) — Minikube local development environment
- [conformance/codafication-conformance.yml](conformance/codafication-conformance.yml) — standards posture, SOC 2 Type II, APRA CPS 234
- [lifecycle/codafication-lifecycle.yml](lifecycle/codafication-lifecycle.yml) — versioning, and the absences (no status page, SLA, deprecation policy)
- [well-known/codafication-well-known.yml](well-known/codafication-well-known.yml) — `/.well-known/` probe index (zero first-party documents)
- [security/codafication-domain-security.yml](security/codafication-domain-security.yml) — TLS/HSTS/DNSSEC/CAA/SPF/DMARC probe
- [llms/codafication-llms.txt](llms/codafication-llms.txt) — generated llms.txt

## Links

- **Website:** [https://codafication.com/](https://codafication.com/)
- **API Reference:** [https://docs.unitycloud.io/](https://docs.unitycloud.io/)
- **Getting Started:** [https://docs.unitycloud.io/#prerequisites-setup](https://docs.unitycloud.io/#prerequisites-setup)
- **Blog:** [https://blog.codafication.com/](https://blog.codafication.com/)
- **Blog RSS:** [https://blog.codafication.com/rss.xml](https://blog.codafication.com/rss.xml)
- **Knowledge Base:** [https://support.codafication.com/en/](https://support.codafication.com/en/)
- **Contact:** [https://codafication.com/get-in-touch/](https://codafication.com/get-in-touch/)
- **Terms:** [https://codafication.com/terms-and-conditions/](https://codafication.com/terms-and-conditions/)
- **Privacy:** [https://codafication.com/privacy](https://codafication.com/privacy)
- **GitHub:** [https://github.com/Codafication](https://github.com/Codafication)
- **LinkedIn:** [https://www.linkedin.com/company/codafication/](https://www.linkedin.com/company/codafication/)

## Maintainers

- Kin Lane — kin@apievangelist.com
