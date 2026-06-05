Access & setup (flagged as the most important thing)

Get access to the Crafford subscriptions — your manager will ask Gary (PM) to set up an NDA so you can access them.
Get G Cloud / G Console access — talk to Arun, Lalith, and Nojiba (cloud ops) about what it takes.
More broadly, "figure out your access": map out where to find what, whose subscription is what, and what runs on each, so you can track production issues when they come up.

Learning the Azure side first

Study how the traditional hub is set up and how the networks are laid out (VPN/IPsec tunnels to on-prem, East/Central US regions).
Look at the PCE hub prod subscription and existing connectivity.
Look at the Crafford hub (the ExpressRoute/colo path via Equinix) — how it's laid out and what it can talk to.
Examine CNBH 17 (WOE advisory) and C1Base7s (investor platform) to understand how hubs and spokes are connected across the non-prod/pre-prod/prod swimlanes.

Learning the GCP side

Read the GCP code base independently over the next 1–2 weeks — both the foundation (hub, central policies, shared VPCs, DNS) and the landing zone code he's sending you.
Read the PTB document and design deck — the implementation maps directly to what's described there.
Understand how the GCP network is set up (VPCs and DNS), but don't over-invest here yet.
Ask Nojiba/Lalith for an overview of the GCP workspaces (which workspace calls which code).
Talk to Tomo about how automation is done and how the hub is set up (he noted these may be two separate meetings: "how it's set up" vs. "how it's really done").

Deliverable

Using Windsurf, reverse-engineer a design document from the Terraform, then compare it against what's actually in GitLab to spot gaps. Walk him through what the Terraform is doing (he's not strong on Terraform — mutual learning).

Hands-on project (to learn by doing)

Create a Jira ticket / project (via Cloud Cowork / storefront) to enable the GCP API the cloud ops team needs, so you learn how everything connects end to end.

Working habits he wants you to pick up

Start asking the code-review questions yourself — "Is this code reviewed? Who released it? Where's the documentation?"
Speak up with questions as you learn rather than silently absorbing everything.

One thing worth confirming with him: he mentioned both "Gaurav" and "Arun" in slightly tangled phrasing around who owns the landing zone work — might be worth clarifying who exactly you should coordinate with there. Want me to draft a short follow-up message to him confirming your priorities and access requests?
