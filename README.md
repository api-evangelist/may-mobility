# May Mobility

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
