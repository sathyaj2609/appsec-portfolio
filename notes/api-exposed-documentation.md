\# Lab class: API testing – Exploiting an API endpoint using documentation



\*\*Date:\*\* 2026-11-17

\*\*Labs completed:\*\* Exploiting an API endpoint using documentation (Apprentice)

\*\*Time spent:\*\* \~25 min (including Burp setup and tooling issues)



\## How to detect it

\- Signals in traffic/responses: updating my email sent `PATCH /api/user/wiener`.

&#x20; The server returned a clear error when I removed the username

&#x20; ("Malformed URL: expecting an identifier"), which revealed how the endpoint is structured.

\- Tools/requests used: Burp Proxy HTTP history, Repeater, and Burp's browser.

\- Technique: trim the URL path one segment at a time

&#x20; (/api/user/wiener -> /api/user -> /api) and watch how responses change.

&#x20; Also try common docs paths such as /api, /swagger, /openapi.json.



\## How it's exploited

\- Core idea: the API exposed its own documentation at /api, listing GET, PATCH

&#x20; and DELETE on /user/\[username]. That showed me a DELETE endpoint the app UI

&#x20; never used, so I could delete another user (carlos).

\- Root cause: public API documentation, and no authorization check

&#x20; on the DELETE endpoint (my wiener session could delete a different user).



\## How to fix it

\- Require authentication and authorization on every endpoint, so a user can only

&#x20; act on their own resources and admin actions need admin roles.

\- Restrict or disable API documentation in production.

\- Defense in depth: log and alert on DELETE calls, and rate-limit sensitive actions.



\## Detection idea (for Semgrep / SAST)

\- Code pattern: Swagger/OpenAPI UI or docs route enabled with no auth guard.

\- Possible rule: flag docs endpoints registered without an authentication

&#x20; decorator/filter in a Python framework (Flask/FastAPI) or Java (Spring).



\## Real-world relevance

\- In a bug bounty, I'd check /api, /swagger and /openapi.json on every target,

&#x20; then compare what the docs allow with what the UI exposes.

\- In code review, I'd check that every route has its own authorization check

&#x20; and isn't relying on the UI hiding it.



\## Gotchas / what I got stuck on

\- The lab site expired after about 2 hours, causing 504 Gateway Timeout errors.

&#x20; Lesson: launch a lab and finish it in one sitting.

\- Burp showed "Stream failed to close correctly" over HTTP/2;

&#x20; switching the Repeater protocol to HTTP/1 in the Inspector fixed it.

\- Be careful with the Repeater target settings: it needs port 443 with HTTPS.

