# Google Ads Agent Disclaimer Implementation Plan

> **For agentic workers:** Use the native execution method for this plan. Deploy incrementally and verify each task before continuing.

**Goal:** Publish an accurate three-page German website for the Marrakesch Shop Google Ads Agent at https://marrakeschshop.os-agentruntime.de with valid HTTPS.

**Architecture:** Static HTML and local CSS are built into a small Caddy image. The existing public Caddy instance obtains/serves TLS for the new host and reverse-proxies only that host to a dedicated static container on its existing Docker network.

**Tech Stack:** HTML, CSS, Docker, Caddy 2, GitHub CLI.

**Spec:** docs/superpowers/specs/2026-10-14-google-ads-agent-disclaimer.md

## Global Constraints
- Do not expose OAuth credentials, tokens, dashboard secrets, or personal Google account data.
- Do not modify or restart the Claude Docker Compose project.
- Change only the new domain route in the active public Caddyfile; validate and reload the existing edge proxy.
- Use only the operator details confirmed by the user and published by the shop.
- No analytics scripts, forms, embedded external fonts, or cookies on the website.
- Clearly state that Google decides brand verification and API access.

## Review Focus
- New hostname gets a valid certificate and existing dashboard hostname continues routing to its existing upstream.
- All three pages work directly and cross-link correctly on mobile and desktop.
- Privacy copy accurately distinguishes website request data from Google account data and identifies unconfirmed retention/provider details.
- CSP permits only local static assets and prevents framing.
- Public repo contains only site sources and operational docs, no credentials or server environment files.

---

### Task 1: Static public pages

**Files:**
- Create: site/index.html
- Create: site/privacy.html
- Create: site/terms.html
- Create: site/styles.css
- Create: site/favicon.svg

- [ ] Write the German page copy, site navigation, operator link and accurate tool/data-flow description.
- [ ] Ensure page links are local and the footer links to the imprint already published at marrakesch-shop.de.
- [ ] Verify each page has a title, language, description, responsive viewport and semantic headings.

### Task 2: Static web container

**Files:**
- Create: Dockerfile
- Create: Caddyfile
- Create: .dockerignore
- Create: README.md

- [ ] Build the static site into Caddy 2 with read-only content and no request access log.
- [ ] Set same-origin security headers and a restrictive Content-Security-Policy.
- [ ] Document the public reverse-proxy hostname and deployment commands without secrets.

### Task 3: GitHub repository

**Files:**
- Repository: samirdev03/google-ads-agent-disclaimer

- [ ] Initialize Git in /root/apps/google-ads-disclaimer and commit only the site source and documentation.
- [ ] Create a public repository of the requested name and push main.
- [ ] Verify the remote repository URL and pushed commit.

### Task 4: Server deployment and HTTPS route

**Files:**
- Modify: /root/apps/opencodeagents-release-9f08841/caddy/Caddyfile (append only the new host route)
- Create: /root/apps/google-ads-disclaimer source checkout and static container

- [ ] Upload the committed source into /root/apps/google-ads-disclaimer.
- [ ] Build and start a dedicated static Caddy container on the existing opencodeagents Docker network; expose no host port.
- [ ] Validate the active public Caddyfile before reload, then reload (do not restart) the existing edge Caddy.
- [ ] Verify the new HTTPS host, certificate hostname/date, page response, and existing dashboard hostname.

### Task 5: Final review

- [ ] Check all three page routes, local navigation, security headers, and absence of third-party scripts/cookies.
- [ ] Confirm the website and public GitHub repository are reachable.
- [ ] Report remaining data retention/provider facts that the operator should confirm before treating the notice as final legal advice.
