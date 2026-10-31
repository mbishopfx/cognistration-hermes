# Public MCP tool catalog

This is the public tool surface observed at `https://cognistration.com/api/mcp` on October 31, 2026. Hermes negotiates with the server and discovers the live schemas at runtime; this snapshot is reference material, not a replacement for `tools/list` or `get_agentic_capabilities`.

Hermes names these tools with the MCP server prefix, for example `mcp__cognistration_hermes__recommend_tone`.

## Capability and discovery

- `get_agentic_capabilities` — current public capability boundary and discovery metadata.

## Catalog

- `search_public_tones`, `get_public_tone` — search and inspect approved public tone entries.
- `search_public_tone_packs`, `get_public_tone_pack` — search and inspect published tone packs and their public previews.

## Intention and session planning

- `recommend_tone` — map a short intention to an approved tone.
- `clarify_intention` — turn a broad request into a small set of listening directions.
- `calibrate_tone` — translate listener feedback into bounded control suggestions.
- `compare_tone_directions` — compare approved directions with fit and tradeoffs.
- `plan_listening_session` — build an arrive, practice, and close plan without starting audio or saving a record.
- `get_session_cue` — return a small prompt without receiving or storing diary text.
- `prepare_session_recipe` — produce a portable, technical-settings-only recipe.
- `compose_session_score` — validate or compose a bounded multi-stage technical score; no audio or persistence side effect.

## Policy, account, and offers

- `get_policy_info` — read canonical safety, terms, privacy, cookies, AI, pricing, or account summaries.
- `get_account_options` — explain the public preview and private workspace options.
- `open_account_signup` — present the user-controlled first-party signup form.
- `get_ios_app_offer` — show the current iPhone app offer and canonical listing details.
- `open_phone_download_options` — present the available phone-download paths; this does not itself charge or accept credentials.

## Checkout, delivery, and access

- `open_tone_pack_checkout` — present the first-party tone-pack checkout flow for user review and submission.
- `create_tone_pack_checkout` — create a server-priced hosted checkout after explicit confirmation.
- `get_tone_pack_delivery` — verify a checkout session before returning delivery information.
- `create_workshop_access_checkout` — create the fixed workshop checkout after confirmation.
- `get_workshop_access` — verify a completed workshop checkout and issue the access grant.
- `get_workshop_access_status` — check a grant without echoing its bearer key.
- `revoke_workshop_access` — revoke a specific grant after explicit confirmation.
- `get_machine_payment_options`, `get_tone_pack_payment_options`, `get_autonomous_payment_options` — read payment-route readiness; none of these tools processes a payment.

## Live machine and education

- `get_machine_control_contract` — read bounded control values, defaults, and semantics.
- `open_machine_generator` — request the interactive machine in hosts that support MCP Apps.
- `set_machine_controls` — set exact bounded values on an already-open machine.
- `adjust_machine_controls` — apply a bounded relative control change.
- `set_machine_direction` — choose a published listening direction and optional presets.
- `start_machine_preview` — request local playback only with explicit confirmation; check `audioReady` before claiming sound is active.
- `stop_machine_preview` — stop local playback.
- `open_machine_fullscreen` — request a larger view in compatible hosts.
- `open_science_guide` — present an educational guide about the signal and evidence boundaries; it does not start audio.
- `open_feedback` — present an optional feedback form; submission remains the listener's action.

## Boundaries

- This is the public endpoint. It does not grant access to private member tools, workspace records, admin routes, internal databases, or render operations.
- Tool annotations and schemas are part of the live contract. The product server is marked `untrusted` in the package so Hermes asks before each non-read-only call.
- Audio, checkout creation, access revocation, and payment actions retain their own explicit-confirmation requirements even when Hermes also asks for approval.
- The host may not render MCP App UI. Never claim a form or machine opened unless the host confirms it; use the structured response and user-approved first-party fallback.
