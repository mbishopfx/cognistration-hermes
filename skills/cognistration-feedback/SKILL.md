---
name: cognistration-feedback
description: Offer Cognistration's optional in-platform feedback card when a listener says the interaction is finished. Never pressure them to rate or expose feedback history.
---

# Cognistration feedback

1. When the person signals they are done, offer one brief, optional closing check-in.
2. If they accept, call `open_feedback` once with no arguments.
3. Verify what the host actually displays. The tool only presents a form; it does not submit feedback.
4. The person chooses a rating and submits the optional note directly through the first-party card. Never put a rating or note in an MCP argument or repeat the note back.
5. A dismissed card or failed submission is not a saved response. Do not claim success without the tool's actual submission receipt.

Feedback is not a basis for inferring medical outcomes or silently changing a tone. Do not open another card for the same completion signal or attach signup, purchase, or navigation to this flow.
