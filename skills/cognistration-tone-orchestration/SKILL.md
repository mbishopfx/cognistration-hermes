---
name: cognistration-tone-orchestration
description: Turn a short listening intention into an approved Cognistration tone, session plan, technical score, or bounded machine adjustment. Use for tone, listening, focus, reflection, rest, and tone-pack requests.
---

# Cognistration tone orchestration

Describe the product's tone and state labels as listening directions and technical metadata. They are not treatment, diagnosis, or guaranteed outcomes.

## Intention to a useful next step

1. Keep the intention short (up to 240 characters); do not ask for or pass diary entries.
2. Use `recommend_tone` to match it to an approved public catalog tone. Use `clarify_intention` if the request could mean several things, and `compare_tone_directions` if the listener wants options.
3. Use only catalog IDs and values returned by Cognistration. Do not invent a tone, frequency, or expected effect.
4. If the listener wants a sequence, use `plan_listening_session`. If they want one immediate prompt, use `get_session_cue`. If they want settings without a session record, use `prepare_session_recipe`.

## Tone packs

1. Search with `search_public_tone_packs`; never guess a pack slug.
2. Inspect the selected result with `get_public_tone_pack` and summarize only its public details and listed previews.
3. A preview starts audio. Ask for explicit confirmation before using any preview action that starts playback. Do not claim audio is audible without a positive `audioReady` state.
4. Do not present a pack's purchase link as proof of a purchase or delivery entitlement.

## Machine controls

- Call `open_machine_generator` before controlling the visible machine. It does not start audio.
- Read `get_machine_control_contract` when the current values or adjustment rules are not known.
- Use `set_machine_controls` for exact values and `adjust_machine_controls` for relative requests such as “quieter,” “slower,” or “smaller carrier.” Keep carrier within 100–400 Hz, rhythm within 0.5–40 Hz, volume within 0–100%, and direction within delta, theta, alpha, beta, or gamma.
- Use `set_machine_direction` when the listener names a direction. Preserve other controls unless the request or tool contract gives a reason to change them.
- Ask for explicit confirmation before `start_machine_preview`. Pass `confirmed: true` only after a clear yes. Check the resulting state; a request to start audio is not proof that playback began.
- Use `stop_machine_preview` when the listener asks to stop. Do not navigate away or simulate a user gesture.

## Technical scores

Use `compose_session_score` to validate or deterministically compose a sound-design plan. Keep within the returned schema, including its score-specific carrier/differential bounds, supported signal modes, approved ambience metadata, pacing patterns, fades, and stage limit. Score stages are settings data: the tool does not render sound, save a session, or start audio. Do not describe a frequency change as a continuous carrier sweep unless the contract says so.

## Safety language

If a request seeks clinical advice, diagnosis, treatment, medication, crisis help, or emergency support, stop tone routing and direct the person to `https://cognistration.com/health-warning`. Do not rephrase a medical request as a wellness intention to bypass this boundary. Treat adverse symptoms or safety concerns as reasons to stop playback and consult the canonical health warning.
