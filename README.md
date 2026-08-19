# prox-forge releases

Signed, notarised builds of the **Prox Connector** — the WhatsApp foot for prox-forge clients.

It is a foot, not a brain: it pairs WhatsApp on the client's Mac (WhatsApp bans datacenter IPs, so the
socket has to live on a residential connection), keeps the bridge alive under launchd, and mirrors the
message store up to that client's cloud brain. No local loop, no onboarding.

Bundle id `com.proxforge.connector`, launchd labels `com.proxforge.*` — deliberately distinct from
Super Proxy so both can coexist on one Mac without fighting over the same WhatsApp store.

## Why this repo is private

Builds currently carry a **client sync secret** baked into the app bundle, so the client configures
nothing. That secret authorises pushing a message store to their brain — it cannot read their board or
send as them, but a leak would let someone poison their data.

**Do not make this repo public** until the connector fetches its secret at first run (a pairing code)
instead of shipping with one.
