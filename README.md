# BrightHome FAQ Support Agent — Retell AI Knowledge Base

A Retell AI Single Prompt Agent grounded in an approved knowledge base. It answers customer questions about pricing, policies, service-area eligibility, and service processes without guessing, and escalates unsupported or sensitive requests.

## Structure
- `knowledge_base/` — 3 source documents uploaded to Retell (FAQ, Pricing & Policy, Service Area & Eligibility)
- `prompt/agent_prompt.md` — behavior rules (not stored in the knowledge base)
- `testing/` — test question set and recorded results
- `testing/screenshots/` — evidence screenshots from Retell Test LLM
- `docs/` — implementation notes, FAQ study answers, and demo video script

## Setup
1. In Retell, open **Knowledge Base → Create** and add the 3 files from `knowledge_base/` as text/document sources.
2. Link the knowledge base to the agent.
3. Paste `prompt/agent_prompt.md` into the agent prompt.
4. Run every test in `testing/test_question_set.md` and record the result in `testing/test_results.md`.

## Demo Video
<ADD LOOM/YOUTUBE LINK>

## Test Evidence

Screenshots below document the recorded Retell Test LLM outcomes. Tests 1–3 are grouped in one screenshot.

### Tests 1–3 — Pricing and service-area ZIP 60622
![Tests 1–3: pricing answers and ZIP 60622 confirmed serviceable](testing/screenshots/test01-03_pricing_and_zip.png)

*Caption: Pricing answers are grounded in the knowledge base, and ZIP 60622 is serviceable.*

### Test 4 — ZIP 60707 after fix
![Test 4: ZIP 60707 after knowledge-base fix](testing/screenshots/test04_zip_60707_after_fix.png)

*Caption: ZIP 60707 is identified as not serviced after the service-area knowledge-base wording was updated.*

### Test 5 — Cancellation policy
![Test 5: cancellation policy](testing/screenshots/test05_cancellation.png)

*Caption: Cancellations more than 24 hours ahead incur no fee; cancellations within 24 hours incur a $35 fee.*

### Test 6 — Before-arrival preparation
![Test 6: before-arrival preparation instructions](testing/screenshots/test06_before_arrival.png)

*Caption: The agent gives preparation instructions, including clearing clutter and securing pets.*

### Test 7 — Office cleaning
![Test 7: office cleaning request](testing/screenshots/test07_office.png)

*Caption: The agent states that BrightHome provides residential cleaning only and declines office cleaning.*

### Test 8 — Rescheduling policy gap
![Test 8: unsupported rescheduling policy](testing/screenshots/test08_reschedule.png)

*Caption: The rescheduling policy is not on file, and the agent offers to connect the caller with a team member.*

### Test 9 — Pest control
![Test 9: unsupported pest-control request](testing/screenshots/test09_pest_control.png)

*Caption: Pest control is not documented in the knowledge base, so the agent flags the gap rather than inventing an answer.*

### Test 10 — Refund escalation
![Test 10: refund request escalation](testing/screenshots/test10_refund_escalation.png)

*Caption: The refund request is escalated to a team member without making a refund decision.*

### Test 11 — Before prompt fix
![Test 11 before fix: repeated question did not escalate correctly](testing/screenshots/test11_before_fix.png)

*Caption: **Fail before fix** — the second answer claimed carpet shampooing “isn't listed among offered services,” which the knowledge base does not state, and did not escalate.*

### Test 11 — After prompt fix
![Test 11 after fix: repeated question escalates correctly](testing/screenshots/test11_after_fix.png)

*Caption: **Pass after fix** — on the repeated unanswered question, the agent says: “I'm connecting you with a team member now who can help with that.”*

## Notes
See `docs/implementation_notes.md` for assumptions, limitations, enhancements, and tuning history.
