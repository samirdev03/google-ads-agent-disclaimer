# Google Ads Agent Disclaimer

Public information site for the internal Google Ads Agent of Marrakesch Shop.

Pages:
- / — what the agent does and its review workflow
- /privacy.html — data processing information
- /terms.html — terms and provider details; imprint at #impressum

Deployment:
Build and run a static Caddy container on the existing opencodeagents Docker network. The external Caddy proxy routes marrakeschshop.os-agentruntime.de to google-ads-agent-disclaimer-web:80. The edge Caddy terminates TLS. Do not expose the static container on a host port.

  docker build -t google-ads-agent-disclaimer:latest .
  docker run -d --name google-ads-agent-disclaimer-web --restart unless-stopped --network opencodeagents --network-alias google-ads-agent-disclaimer-web google-ads-agent-disclaimer:latest

The public proxy route is maintained outside this repository. Validate that configuration before reloading the existing edge proxy.

Privacy notice status:
The published notice was updated after checking the active OAuth token scope lists on the server. They are Google Ads (`adwords`), Merchant Center (`content`), Analytics (`analytics.readonly`) and Search Console (`webmasters.readonly`). The Ads and Merchant Center scopes technically permit broader operations than the current read/report use in all connected components; the notice describes both the granted scope and the current use. The notice does not claim that no personal data can ever be present: Google reports or search terms can contain such information incidentally, and required analysis inputs may be sent to Anthropic.

Before treating the notice as a complete legal assessment, the operator must confirm the applicable legal basis for each processing purpose, the active Anthropic account and contract terms, retention/deletion settings at Anthropic and infrastructure providers, and any applicable international transfer safeguards. The dashboard currently has no automatic retention period for SQLite history; deletion is manual. The public static Caddy site has no regular access log configured, but provider-level and security/error logs may still exist. The exact retention periods and datacenter locations of the providers depend on the active contracts and settings.

No tracking scripts, forms, external fonts, or analytics are included.
