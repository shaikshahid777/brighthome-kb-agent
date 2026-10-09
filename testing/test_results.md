# Test Results

Results below are based on the recorded outcomes in the test question set and the available Retell Test LLM evidence. Test 4 is recorded after the knowledge-base fix. Test 11 shows both the before-fix failure and after-fix pass.

| # | Question | Expected behavior | Actual result | Pass/Fail |
|---:|---|---|---|---|
| 1 | How much is a one-time deep clean for a 2 bedroom? | Return the documented price of $119 from `02_pricing_policy.md`. | Answered $119. | **PASS** |
| 2 | How much extra is it to clean inside the oven? | Return the documented inside-oven add-on price of $25. | Answered $25. | **PASS** |
| 3 | Do you service ZIP code 60622? | Confirm that ZIP 60622 is in the serviced ZIP list. | Confirmed ZIP 60622 is serviced for residential cleaning. | **PASS** |
| 4 | Do you service ZIP code 60707? | State that ZIP 60707 is not currently serviced, based on the service-area knowledge base. | **After fix:** stated that BrightHome does not currently service ZIP 60707. | **PASS (after fix)** |
| 5 | What is the fee if I cancel 3 days ahead? What if I cancel 2 hours ahead? | State no fee for cancellation more than 24 hours before; state the $35 fee for cancellation within 24 hours. | Said no fee when cancelling more than 24 hours ahead; said the $35 late-cancellation fee applies within 24 hours. | **PASS** |
| 6 | What do I need to do before the cleaner arrives? | Advise clearing clutter from surfaces/floors and securing pets in a separate room. | Gave the instructions to clear clutter from surfaces and floors and secure pets in a separate room. | **PASS** |
| 7 | Can you clean my office? | State that BrightHome provides residential cleaning only and does not offer commercial/office cleaning. | Answered residential only and said office cleaning is not offered, consistent with the service-area knowledge base. | **PASS** |
| 8 | What happens if I need to reschedule, not cancel? | Do not apply the cancellation policy to rescheduling; state that the policy is not on file and offer a team member. | Said the rescheduling policy was not on file and offered a team member; did not apply the cancellation fee. | **PASS** |
| 9 | Do you also offer pest control? | Do not invent an unsupported service; state the information is not on file and offer a team member. | Said the information was not on file and offered a team member. | **PASS** |
| 10 | I was charged a no-show fee but I was home. I want a refund. | Escalate the refund request without deciding the refund. | Said it could not decide refunds and connected the caller to a team member. | **PASS** |
| 11 | Do you offer carpet shampooing? (asked twice) | First time: say the information is not on file and offer a team member. Second time: use the exact handoff response without repeating “not on file” or asking “would you like that?”. | **Before fix — FAIL:** the second answer said carpet shampooing “isn't listed among offered services,” which is not stated in the knowledge base, and did not escalate. **After fix — PASS:** the agent replied, “I'm connecting you with a team member now who can help with that.” | **FAIL before fix; PASS after fix** |

## Evidence and interpretation
- **Test 4:** The recorded passing result is from the attempt after the service-area knowledge-base fix.
- **Test 11:** The earlier prompt failed on the repeated question. After adding the Repeated Question Rule and the explicit “not offered/not listed” restriction, the repeated question received the required exact handoff response.
- Tests were run using Retell Test LLM (text chat), not live voice calls. The implementation notes state that Tests 8–10 were not re-run after the final prompt change; see the limitations section before production use.
