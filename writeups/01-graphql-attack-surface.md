# GraphQL Attack Surface: What I Learned From the PortSwigger Labs

*Draft — target 600–900 words. Concepts and fixes, not lab solutions.*

## Why GraphQL changes the security picture
<!-- 3–4 sentences: single endpoint, client-shaped queries, schema introspection, authz at field/resolver level instead of per-route. -->

## 1. Finding the endpoint
<!-- Common paths, "Query not present"-style hints, universal queries. -->

## 2. Introspection and schema discovery
<!-- What it exposes, why it's risky in production, what to do when it's disabled (suggestion leakage). -->

## 3. Access control at the resolver level
<!-- Private fields/objects reachable by ID; accidental field exposure. Where authz checks belong. -->

## 4. Abusing aliases and batching
<!-- Rate-limit/brute-force protections counting requests, not operations. -->

## 5. CSRF over GraphQL
<!-- Content-type handling, GET/form-encoded queries, SameSite and token defenses. -->

## Defender checklist
- [ ] Disable introspection in production (and field suggestions)
- [ ] Enforce authorization in every resolver, not just at the edge
- [ ] Limit query depth, complexity, aliases and batch size
- [ ] Require JSON content-type; use CSRF tokens / SameSite cookies
- [ ] Don't expose internal fields (passwords, tokens) in the schema

## What I'd look for in a code review
<!-- 2–3 concrete patterns in Python/Java GraphQL libraries. -->

## Takeaways
<!-- 2–3 sentences, first person. -->
