# BrightHome FAQ Support Agent - Retell AI Knowledge Base (Lesson 5)

A Retell AI Single Prompt Agent backed by a Knowledge Base that answers pricing, policy, service-area and process questions only from approved sources, refuses to guess, and escalates disputes.

## Structure
- `knowledge_base/` - 3 source documents uploaded to Retell (FAQ, Pricing & Policy, Service Area & Eligibility)
- `prompt/agent_prompt.md` - behavior rules (not stored in KB)
- `testing/` - test question set and results
- `testing/screenshots/` - evidence screenshots from Retell Test LLM
- `docs/` - implementation notes, FAQ study answers, demo video script

## Setup
1. In Retell: Knowledge Base > Create > add the 3 files from `knowledge_base/` (as Text/Document).
2. Link the KB to the agent.
3. Paste `prompt/agent_prompt.md` into the agent prompt.
4. Run every test in `testing/test_question_set.md`; record in `testing/test_results.md`.

## Demo Video
<ADD LOOM/YOUTUBE LINK>

## Notes
See `docs/implementation_notes.md` for assumptions, limitations and enhancements.
