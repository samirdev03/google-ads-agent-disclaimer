# Google Ads Agent Disclaimer

Public information site for the internal Google Ads Agent of Marrakesch Shop.

Pages:
- / — what the agent does and its review workflow
- /privacy.html — detailed data processing information
- /terms.html — terms and provider details; imprint at #impressum

Deployment:
Build and run a static Caddy container on the existing opencodeagents Docker network. The external Caddy proxy routes marrakeschshop.os-agentruntime.de to google-ads-agent-disclaimer-web:80. The edge Caddy terminates TLS. Do not expose the static container on a host port.

  docker build -t google-ads-agent-disclaimer:latest .
  docker run -d --name google-ads-agent-disclaimer-web --restart unless-stopped --network opencodeagents --network-alias google-ads-agent-disclaimer-web google-ads-agent-disclaimer:latest

The public proxy route is maintained outside this repository. Validate that configuration before reloading the existing edge proxy.

Privacy notice status:
The privacy notice names the app and controller, describes the actual active OAuth scopes, lists representative fields returned by each API, explains current uses, storage, recipients, retention/deletion and technical safeguards. The active scopes checked on the server are Google Ads (`adwords`), Merchant Center (`content`), Analytics (`analytics.readonly`) and Search Console (`webmasters.readonly`). The Google Ads integration exposes read and write tools; its write operations require preview and explicit human confirmation. The Merchant Center integration is read-only in current use even though its OAuth scope technically permits more.

Google Ads, Search Console and Analytics reports may contain personal information incidentally (for example, a search term). Google data required for an analysis is sent to Claude Code/Anthropic for response generation. The app does not use Google data to train models or for unrelated advertising, profiling or resale. The operator must ensure the Anthropic account is not opted into model training or a development partner program for these inputs.

Open operator confirmations before treating the notice as a complete legal assessment: confirm the legal basis for each processing purpose; verify the Anthropic account type, training opt-out and data-retention terms; identify the exact infrastructure log-retention/locations and any transfer safeguards; confirm whether stored data at rest is encrypted. OAuth tokens and dashboard history have no automatic retention period. The history has no normal dashboard deletion function; server-side maintenance is required to remove it. The public static Caddy site has no regular access log configured, though provider-level and security/error logs may still exist.

No tracking scripts, forms, external fonts, or website analytics are included.
