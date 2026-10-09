# Topic 4 FAQ - Answers (study notes)

**Q1.** A Knowledge Base is a collection of documents, URLs or text linked to an agent so it can pull accurate reference info during a call. The prompt is for behavior/tone; the KB is for large factual, lookup content (pricing, policies, FAQs) that is impractical to keep in a prompt.

**Q2.** Once linked, retrieval happens automatically before every response. The system finds the most relevant chunk(s) based on the conversation so far and gives them to the agent as context. No special prompt instruction is needed.

**Q3.** Chunking breaks each source document into smaller indexed pieces during setup. It decides how precisely the right fact can be retrieved, so clean sections give better retrieval.

**Q4.** KB: pricing tables, service areas, cancellation policy text, FAQ answers. Prompt: behavior rules like "never guess", "escalate billing disputes".

**Q5.** Each section covers one clearly headed topic. Mixing pricing, cancellation and service area in one paragraph makes it hard for retrieval to isolate the right fact.

**Q6.** Specific headers that name the exact topic. Good: "Late Cancellation Fee". Poor: "Policies".

**Q7.** Retrieval may surface an outdated or conflicting value. Remove or correct old content instead of leaving it beside the new version.

**Q8.** (1) FAQ: services, booking, home presence, supplies, pre-appointment prep. (2) Pricing & Policy: room pricing, recurring discount, add-ons, late cancellation, no-show, satisfaction guarantee. (3) Service Area & Eligibility: ZIP codes, residential-only, property access.

**Q9.** State the information is not on file and offer to connect the caller with a team member, instead of guessing. This is a prompt-level rule.

**Q10.** Don't apply a documented policy to an undocumented scenario. Example: don't use the cancellation fee for rescheduling; say rescheduling is not covered.

**Q11.** Caller disputes a charge, requests a refund decision, or repeats the same unanswered question a second time.

**Q12.** To verify the agent retrieves and states correct answers, each traceable to a source. The implementation doc's set has 9 questions (the test-case doc expands to 11 test cases).

**Q13.** Questions worded like an adjacent topic (e.g., reschedule vs cancel). They catch cases where retrieval applies the wrong policy.

**Q14.** Revisit source structuring first (clearer headers, better topic separation) before changing the prompt.

**Q15.** RSK-001 stale/contradictory content: remove or correct outdated material before uploading. RSK-002 adjacent-topic confusion: distinct headers per topic plus near-miss questions in testing.
