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
The policy describes current known code paths and services. Exact infrastructure retention, physical server location, the active Anthropic account terms, and applicable international transfer safeguards still require operator confirmation. Review these points before treating the notice as final legal advice or as a final compliance statement.

No tracking scripts, forms, external fonts, or analytics are included.
