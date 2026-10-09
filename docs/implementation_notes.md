# Implementation Notes

## Architecture
Single Prompt Agent (from Topics 1-3) linked to one Retell Knowledge Base with 3 source documents. Prompt holds behavior only; facts live in the KB.

## Assumptions
- ASM-001: Source documents were reviewed for accuracy before upload.
- ASM-002: Sources contain no contradictions; changes update the source rather than appending.

## Limitations
- Rescheduling, pest control and other topics are intentionally not covered; the agent escalates.
- Answers depend on retrieval quality; re-test after any source edit.
- Tests 8, 9 and 10 were run before the final prompt change (Repeated Question Rule added after Test 11). They were not re-run with the final prompt to conserve test credits. Re-running them is recommended before production use.
- Testing was done with the Retell Test LLM (text chat), not live voice calls.

## Possible Enhancements
- Add a rescheduling policy document if the business defines one.
- Add more near-miss test questions (e.g., recurring vs one-time pricing).
- Log retrieved chunks per call for audit.

## Tuning Log
- Test 4 (ZIP 60707), attempt 1: agent said the ZIP was "not on file" and offered a team member. It did not guess, but it did not clearly say "not serviced" as expected. Result: Fail.
- Fix: edited the Service Area & Eligibility source and added the line "ZIP codes not listed above are not currently serviced by BrightHome." under the ZIP list. Followed the doc guidance: fix source structure first, prompt unchanged.
- Test 4, attempt 2 after fix: agent said BrightHome does not currently service ZIP 60707. Result: Pass.
- Test 11 (repeated question), attempts 1-2: with the original Escalation Triggers rule only, the agent refused correctly the 1st time but on the 2nd identical question it again asked 'would you like that?' and said the service 'isn't listed among our offered services' instead of escalating. Result: Fail.
- Fix: prompt-level (escalation is behavior, not a retrievable fact). Added a 'Repeated Question Rule' with an exact handoff line, and a rule to never say 'not offered'/'not listed' unless the retrieved content says so.
- Test 11, attempt 3 after fix: 1st time 'not on file'; 2nd time 'I'm connecting you with a team member now who can help with that.' Result: Pass.
