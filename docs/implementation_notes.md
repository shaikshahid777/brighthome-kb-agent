# Implementation Notes

## Architecture
Single Prompt Agent linked to one Retell Knowledge Base with three source documents. The prompt controls behavior; factual service, pricing, and policy information lives in the knowledge base.

## Assumptions
- **ASM-001:** Source documents were reviewed for accuracy before upload.
- **ASM-002:** Sources contain no contradictions; when information changes, update the source rather than appending conflicting content.
- The recorded test results describe Retell Test LLM text-chat runs; they are not evidence of live voice-call testing.

## Limitations
- Rescheduling, pest control, and other undocumented topics are intentionally not answered from guesswork; the agent offers escalation.
- Answers depend on retrieval quality. Re-test after any knowledge-base or prompt edit.
- Tests 8, 9, and 10 were run before the final prompt change (the Repeated Question Rule was added after Test 11). They were not re-run with the final prompt to conserve test credits. Re-running them is recommended before production use.
- Testing was performed with Retell Test LLM (text chat), not live voice calls.
- Test 11's first prompt version failed to escalate on the repeated question; the tuned version produced the required exact handoff response.

## Possible Enhancements
- Add a rescheduling policy document if BrightHome formally defines one.
- Add more near-miss test questions (for example, recurring versus one-time pricing).
- Log retrieved knowledge-base chunks per call for auditability.
- Re-run Tests 8–10 with the final prompt and complete a full regression run before production use.

## Tuning

### Fix A — ZIP 60707 eligibility (Test 4)
- **What was wrong:** On the first attempt, the agent said ZIP 60707 was "not on file" and offered a team member. It did not guess, but it also did not clearly answer that the ZIP was not serviced, which was the expected behavior.
- **What changed:** Updated `knowledge_base/03_service_area_eligibility.md` by adding the explicit sentence: **"ZIP codes not listed above are not currently serviced by BrightHome."** under the serviced ZIP-code list.
- **Verified outcome:** On the next attempt, the agent stated that BrightHome does not currently service ZIP 60707. Test 4 is recorded as **PASS after fix**.

### Fix B — Repeated-question escalation (Test 11)
- **What was wrong:** With the earlier prompt, the second identical question did not escalate. The agent said carpet shampooing "isn't listed among offered services"—a claim not stated in the knowledge base—and asked "would you like that?" instead of handing off.
- **What changed:** Added the highest-priority **Repeated Question Rule** requiring the exact response, **"I'm connecting you with a team member now who can help with that."** Also added the rule: **Never say a service is "not offered" or "not listed" unless that is explicitly stated in the retrieved content.**
- **Verified outcome:** After the prompt fix, the second question received the required exact handoff response. Test 11 is recorded as **FAIL before fix; PASS after fix**.
