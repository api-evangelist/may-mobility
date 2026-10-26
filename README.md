# May Mobility

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

May Mobility is an American autonomous vehicle technology company headquartered in Ann Arbor, Michigan, founded in 2017 by Edwin Olson, Alisyn Malek and Steve Vozar. It develops and operates self-driving shuttle, microtransit and robotaxi services with cities, transit agencies, commercial sites and ride-hail networks including Uber, Lyft and Grab, using a proprietary Multi-Policy Decision Making (MPDM) autonomy stack.

- Website: https://maymobility.com/
- Developer documentation: https://docs.maymobility.com/
- NOC / network documentation: https://net.maymobility.com/ (AS398351)

## API surface

May Mobility publishes a **Fleet API** for fleet partners, in two parts:

- **Fleet Realtime API** — WebSocket streaming, in telemetry mode (15 documented per-vehicle topics as JSON) and video mode (exterior cameras as serialized protobuf).
- **Fleet Batch (REST) API** — historical telemetry between two timestamps, plus LiDAR ROSBAG exports, vehicle shift timings and last-active status.

Both are authenticated with AWS Cognito OAuth 2.0 client-credentials tokens. **Access is not self-service** — accounts, scopes and the connection domain itself are provisioned by contacting the May Mobility Fleet API team.

## Contract discovery result

May Mobility publishes **no machine-readable API contract**. Probed across `maymobility.com`, `docs.maymobility.com` and `net.maymobility.com`: no OpenAPI/Swagger, no AsyncAPI, no GraphQL, no JSON Schema, no MCP server, no A2A agent card. The artifacts in this repo are derived from the provider's own published documentation and from live probes, with every claim evidenced.

## Notable findings

- Infrastructure security is well ahead of the API description: DNSSEC, CAA, DMARC `p=reject`, HSTS, TLS 1.3, an in-house PKI with published Root/Intermediate CAs, a public AS with an open peering policy, and a real responsible-disclosure program with safe harbour.
- The disclosure policy carries a safety-critical carve-out: **May Mobility shuttles are explicitly out of scope for security research.**
- All three hosts publish Cloudflare Content Signals (`search=yes, ai-train=no, use=reference`) with an EU DSM Article 4 rights reservation and Disallow directives for nine named AI crawlers.
- Twelve documented failure conditions, none with a published status code or error shape.
- The advertised status page (`status.net.maymobility.com`) fails its TLS handshake.
- The security.txt is past its own `Expires` date.
