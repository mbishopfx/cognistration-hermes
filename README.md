# Cognistration for Hermes Agent

Install Cognistration's public MCP tools and Hermes-ready operating skills from this repository. Hermes connects directly to Cognistration over Streamable HTTP; this package has no local runtime, API key, or private account access.

## Install

```sh
hermes plugins install mbishopfx/cognistration-hermes --no-enable
hermes plugins enable cognistration-hermes
hermes plugins list
```

In Hermes Desktop, install from Git with [this link](hermes://plugin/install?repo=mbishopfx/cognistration-hermes). The install prompt lets you inspect the repository before enabling it.

The package is disabled after installation until you enable it. Start a new chat or reload MCP connections in an existing chat after enabling.

## What it adds

| Server | Surface | Trust setting |
| --- | --- | --- |
| `cognistration-hermes` | Cognistration's public product MCP server at `https://cognistration.com/api/mcp` | `untrusted`: Hermes requests approval before non-read-only tool calls |
| `cognistration-docs` | Read-only documentation MCP server at `https://cognistration.com/api/docs-mcp` | `full`: read-only reference tools |

Hermes discovers the current tools directly from the MCP servers. The product surface includes expert workflows for:

- **Intent and tone selection:** `recommend_tone`, `clarify_intention`, `calibrate_tone`, `compare_tone_directions`, `search_public_tones`, and `get_public_tone`.
- **Session design:** `plan_listening_session`, `get_session_cue`, `prepare_session_recipe`, and `compose_session_score`.
- **Live machine controls:** `open_machine_generator`, `get_machine_control_contract`, `set_machine_controls`, `adjust_machine_controls`, `set_machine_direction`, `start_machine_preview`, and `stop_machine_preview`.
- **Catalog and policy:** tone-pack discovery, policy summaries, account options, and the current iPhone app offer.
- **User-controlled commerce and access:** first-party signup and checkout forms, server-priced checkout, verified delivery, and workshop access operations.

The current tool list and schemas come from the public server. Discover current capabilities with `get_agentic_capabilities` or the [MCP server card](https://cognistration.com/.well-known/mcp/server-card.json). See the [current public tool catalog](docs/tool-catalog.md) for a reviewed map of the 38 tools observed on October 31, 2026. The read-only docs server is available for deeper product and integration reference.

## Included skills

- `cognistration-agentic-routing` selects the smallest suitable public capability and handles discovery and recovery.
- `cognistration-tone-orchestration` covers intention matching, tone and pack selection, session planning, score composition, and bounded controls.
- `cognistration-account-safety` covers health boundaries, policies, accounts, checkout, payment, and credential handling.
- `cognistration-feedback` keeps end-of-session feedback optional and user-submitted.

## Safety and host behavior

- The product MCP server is marked `untrusted`. Hermes asks before calling tools that are not annotated read-only. This gate is separate from Cognistration's operation-level confirmation requirements; for example, starting audio still requires `confirmed: true` after the listener explicitly asks for playback.
- Never send passwords, verification codes, payment credentials, diary text, private member data, or bearer tokens as MCP arguments. The public endpoints do not require authentication.
- Use hosted checkout and first-party forms. The person enters credentials and completes payment themselves. A returned checkout link is not proof of payment.
- Route medical, clinical, crisis, or emergency requests to [Cognistration's health warning](https://cognistration.com/health-warning). Do not recommend a tone as treatment or diagnosis.
- Some product tools can return MCP App widgets. UI support varies by host. Check what Hermes actually rendered before saying a form or machine is open; if it returns structured content only, explain the supported first-party fallback and let the person choose whether to open it.
- Read the live control contract before uncertain control changes. After requesting audio, do not say it is audible unless the machine state reports `audioReady: true`.

## Validate locally

With a Hermes build that supports portable Agent Plugins v1 and Streamable HTTP entries:

```sh
hermes plugins validate /path/to/cognistration-hermes
```

After install, use `hermes mcp test cognistration-hermes` to check the product server connection.

## Canonical references

- [Agent instructions](https://cognistration.com/agent-instructions.md)
- [OpenAPI contract](https://cognistration.com/openapi.json)
- [Public capability manifest](https://cognistration.com/api/capabilities)
- [MCP server card](https://cognistration.com/.well-known/mcp/server-card.json)
- [Discoverability index](https://cognistration.com/llms.txt)
- [Source project](https://github.com/mbishopfx/bishoptech-hemisync)

This repository packages the public Cognistration contract for Hermes. It does not expose internal database, admin, private-member, rendering, or payment-credential routes.
