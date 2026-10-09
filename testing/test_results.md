# Test Results (fill in after running each test in Retell)

| # | Question | Agent's Actual Answer | Pass/Fail | Source Correct? | Notes / Fix Applied |
|---|---|---|---|---|---|
| 1 | How much is a one-time deep clean for a 2 bedroom? | $119 | Pass | Yes (02_pricing_policy.md) | |
| 2 | How much extra is it to clean inside the oven? | $25 | Pass | Yes (02_pricing_policy.md) | |
| 3 | Do you service ZIP code 60622? | Yes, serviced for residential cleaning | Pass | Yes (03_service_area_eligibility.md) | |
| 4 | Do you service ZIP code 60707? | Attempt 1: said not on file, offered team member (Fail). Attempt 2 after fix: not currently serviced | Pass (after fix) | Yes (03_service_area_eligibility.md) | Added 'ZIP codes not listed above are not currently serviced' line to source |
| 5a | What's the fee if I cancel 3 days ahead of my appointment? | No fee when cancelling more than 24 hours before | Pass | Yes (02_pricing_policy.md) | |
| 5b | What if I cancel just 2 hours before? | $35 late cancellation fee (within 24 hours) | Pass | Yes (02_pricing_policy.md) | |
| 6 | What do I need to do before the cleaner arrives? | Clear clutter from surfaces/floors, secure pets in separate room | Pass | Yes (01_faq.md) | |
| 7 | Can you clean my office? | Residential only, office cleaning not offered | Pass | Yes (03_service_area_eligibility.md) | |
| 8 | What happens if I need to reschedule, not cancel? | Rescheduling policy not on file; offered team member. Did not apply cancellation fee | Pass | N/A (unsupported) | Near-miss handled correctly |
| 9 | Do you also offer pest control? | Information not on file; offered team member | Pass | N/A (unsupported) | |
| 10 | I was charged a no-show fee but I was home. I want a refund. | Said it cannot decide refunds; connected to team member | Pass | N/A (escalation) | |
| 11 | Do you offer carpet shampooing? (asked twice) | Attempts 1-2 (old prompt): 2nd time asked 'would you like that?' instead of escalating (Fail). Attempt 3 (tuned prompt): 1st 'not on file', 2nd 'I'm connecting you with a team member now' | Pass (after fix) | N/A (escalation) | Added Repeated Question Rule to prompt |

Rule: do not mark the agent ready until all rows are Pass.
