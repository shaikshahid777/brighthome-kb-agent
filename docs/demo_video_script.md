# Demo Video Script (2.5 minutes maximum)

**Demo:** https://www.loom.com/share/2a9a6ae7a9224843ac39384aa8c44780

| Time | SAY | SHOW / DO |
|---|---|---|
| 0:00–0:10 — Intro | “Hi, I’m Shaik Mohammad Shaheed. This is my BrightHome FAQ Support Agent, built with Retell AI and a knowledge base for customer support.” | Show the project title in GitHub README. |
| 0:10–0:30 — GitHub repo | “The repository includes three knowledge-base documents, the agent prompt, test results, screenshots, and implementation notes.” | Scroll through the README navigation and repository structure. |
| 0:30–0:55 — Retell agent | “The agent answers from approved sources and avoids guessing. Unsupported or sensitive questions should be handed off to a team member.” | Show the Retell agent, linked knowledge base, and prompt rules. |
| 0:55–1:55 — Test examples | “For a two-bedroom deep clean, the documented price is $119. ZIP 60707 is not serviced after a knowledge-base fix. Cancellation more than 24 hours ahead has no fee; within 24 hours it is $35. Rescheduling is undocumented, so the agent does not assume the cancellation policy applies. Refund decisions are escalated.” | Run or show recorded results for the price, ZIP 60707, cancellation, rescheduling, and refund scenarios. Then ask “Do you offer carpet shampooing?” twice in the same chat; show the exact team-member handoff on the repeated question. |
| 1:55–2:15 — Tuning | “I improved ZIP-code handling with a clearer knowledge-base rule and fixed repeated-question escalation with a higher-priority prompt instruction.” | Show the relevant tuning notes and the before/after screenshots for Tests 4 and 11. |
| 2:15–2:25 — Close | “This project helped me practise knowledge-base design, prompt tuning, and evidence-based testing. You can find the source and demo links in the README. Thank you.” | Return to README and point to the Loom demo link. |

## Recording Tips

1. Use Retell Test LLM text chat for the demo; don't describe it as a live voice test.
2. For the repeated-question scenario, keep both identical questions in the same conversation.
3. Tests 8–10 were not rerun with the final prompt, so describe the existing recorded results accurately and avoid claiming that all 11 tests passed after the final change.
