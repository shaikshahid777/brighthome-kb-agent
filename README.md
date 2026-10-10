<!-- BrightHome FAQ Support Agent | Portfolio README -->

<div align="center">

# 🏡 BrightHome FAQ Support Agent

### A knowledge-grounded customer support agent built with Retell AI

<p>
  <a href="https://www.loom.com/share/2a9a6ae7a9224843ac39384aa8c44780"><img src="https://img.shields.io/badge/▶_Watch_Demo-Loom-625DF5?style=for-the-badge&logo=loom&logoColor=white" alt="Watch Loom demo"></a>
  <a href="https://github.com/shaikshahid777/brighthome-kb-agent"><img src="https://img.shields.io/badge/GitHub-Repository-181717?style=for-the-badge&logo=github" alt="GitHub repository"></a>
</p>

<p>
  <img src="https://img.shields.io/badge/Platform-Retell_AI-635BFF?style=flat-square" alt="Retell AI">
  <img src="https://img.shields.io/badge/Knowledge_Base-3_sources-0F766E?style=flat-square" alt="Three knowledge base sources">
  <img src="https://img.shields.io/badge/Test_Scenarios-11-2563EB?style=flat-square" alt="11 test scenarios">
  <img src="https://img.shields.io/badge/Focus-Grounded_AI_Support-7C3AED?style=flat-square" alt="Grounded AI support">
</p>

*A practical AI support project focused on accurate answers, clear policy boundaries, and reliable human handoff.*

</div>

---

## ✨ Project Overview

BrightHome FAQ Support Agent is a **Retell AI Single Prompt Agent** grounded in an approved knowledge base. It helps customers with cleaning prices, service-area eligibility, cancellation policies, and service preparation. When a request is unsupported or sensitive, the agent avoids inventing an answer and offers a team-member handoff.

## 🎬 Project Demo

<div align="center">

### See the agent in action

[![▶ Watch the BrightHome FAQ Support Agent demo on Loom](https://img.shields.io/badge/▶_PLAY_DEMO-Open_Loom_Video-625DF5?style=for-the-badge&logo=loom&logoColor=white)](https://www.loom.com/share/2a9a6ae7a9224843ac39384aa8c44780)

**[Watch the Loom walkthrough](https://www.loom.com/share/2a9a6ae7a9224843ac39384aa8c44780)** · [Explore the source code](https://github.com/shaikshahid777/brighthome-kb-agent)

</div>

## 🚀 Key Features

| Capability | What it does |
|---|---|
| 📚 Knowledge-grounded answers | Uses approved FAQ, pricing/policy, and service-area documents |
| 💵 Pricing and policy guidance | Answers documented cleaning prices, add-ons, and cancellation fees |
| 📍 Service-area checks | Checks supported ZIP codes and identifies explicitly unserved ZIP codes |
| 🛡️ No-guessing behavior | Avoids inventing undocumented services or policies |
| 🤝 Human escalation | Routes refund disputes and repeated unanswered questions to a team member |
| 🧪 Evidence-led testing | Includes an 11-scenario test set, recorded outcomes, screenshots, and tuning notes |

## 🧭 Quick Navigation

| Start here | Open |
|---|---|
| 🧠 Agent prompt and behavior rules | [`prompt/agent_prompt.md`](prompt/agent_prompt.md) |
| 📚 Knowledge-base source files | [`knowledge_base/`](knowledge_base/) |
| 🧪 Test questions | [`testing/test_question_set.md`](testing/test_question_set.md) |
| 📊 Recorded test results | [`testing/test_results.md`](testing/test_results.md) |
| 🛠️ Implementation and tuning notes | [`docs/implementation_notes.md`](docs/implementation_notes.md) |
| ✅ Submission checklist | [`SUBMISSION_CHECKLIST.md`](SUBMISSION_CHECKLIST.md) |

## 🏗️ How It Works

```text
Customer question
       ↓
Retell AI Support Agent
       ↓
Approved BrightHome Knowledge Base
(FAQ · Pricing & Policy · Service Area)
       ↓
Grounded answer ── or ── Human handoff
```

**Design principle:** answer only from the retrieved knowledge base; do not infer a policy from a different topic; escalate when the question remains unsupported or needs a human decision.

## 🧪 Test Evidence

The screenshots below document outcomes recorded in Retell's **Test LLM text chat**. They are test evidence, not a claim that all scenarios were rerun against the final prompt.

### Tests 1–3 — Pricing and service-area ZIP 60622
![Tests 1–3: pricing answers and ZIP 60622 confirmed serviceable](testing/screenshots/test01-03_pricing_and_zip.png)

*Pricing answers are grounded in the knowledge base, and ZIP 60622 is serviceable.*

### Test 4 — ZIP 60707 after fix
![Test 4: ZIP 60707 after knowledge-base fix](testing/screenshots/test04_zip_60707_after_fix.png)

*After the knowledge-base wording was updated, ZIP 60707 was identified as not currently serviced.*

### Test 5 — Cancellation policy
![Test 5: cancellation policy](testing/screenshots/test05_cancellation.png)

*Cancellations more than 24 hours ahead incur no fee; cancellations within 24 hours incur a $35 fee.*

### Test 6 — Before-arrival preparation
![Test 6: before-arrival preparation instructions](testing/screenshots/test06_before_arrival.png)

*The agent advises customers to clear clutter and secure pets.*

### Test 7 — Office cleaning
![Test 7: office cleaning request](testing/screenshots/test07_office.png)

*The agent explains that BrightHome provides residential cleaning only.*

### Test 8 — Rescheduling policy gap
![Test 8: unsupported rescheduling policy](testing/screenshots/test08_reschedule.png)

*The rescheduling policy is not on file, and the agent offers a team-member handoff.*

### Test 9 — Pest control
![Test 9: unsupported pest-control request](testing/screenshots/test09_pest_control.png)

*The agent identifies the missing information instead of inventing a service policy.*

### Test 10 — Refund escalation
![Test 10: refund request escalation](testing/screenshots/test10_refund_escalation.png)

*The refund request is escalated without making an unsupported refund decision.*

### Test 11 — Before prompt fix
![Test 11 before fix: repeated question did not escalate correctly](testing/screenshots/test11_before_fix.png)

**Before fix:** the repeated question did not trigger the required handoff and the answer made an unsupported claim.

### Test 11 — After prompt fix
![Test 11 after fix: repeated question escalates correctly](testing/screenshots/test11_after_fix.png)

**After fix:** the repeated unanswered question triggers the configured handoff: “I'm connecting you with a team member now who can help with that.”

## 🔧 Tuning Highlights

- **Service-area clarity:** added an explicit knowledge-base statement that ZIP codes not listed in the supported list are not currently serviced.
- **Repeated-question handling:** added a high-priority prompt rule requiring a direct team-member handoff when the same unanswered question is repeated.
- **Safer wording:** restricted unsupported claims such as “not offered” or “not listed” unless the retrieved knowledge base explicitly supports them.

## 📁 Repository Structure

```text
brighthome-kb-agent/
├── knowledge_base/
│   ├── 01_faq.md
│   ├── 02_pricing_policy.md
│   └── 03_service_area_eligibility.md
├── prompt/
│   └── agent_prompt.md
├── testing/
│   ├── test_question_set.md
│   ├── test_results.md
│   └── screenshots/
├── docs/
│   ├── demo_video_script.md
│   ├── faq_answers.md
│   └── implementation_notes.md
└── SUBMISSION_CHECKLIST.md
```

## ⚙️ Setup

1. In Retell, create a knowledge base and add the three source files from `knowledge_base/`.
2. Link the knowledge base to the support agent.
3. Paste the rules from `prompt/agent_prompt.md` into the agent prompt.
4. Run the scenarios in `testing/test_question_set.md`.
5. Record actual outcomes in `testing/test_results.md` and capture evidence screenshots.

## ⚠️ Testing Notes

- The test set contains **11 scenarios** and includes before-fix/after-fix evidence for the ZIP-code and repeated-question issues.
- Tests 8–10 were recorded before the final prompt change and were **not rerun with the final prompt**; rerun them as part of a full regression check.
- Testing was performed in Retell Test LLM **text chat**, not a live voice call.
- Rescheduling and pest-control policies are undocumented in the current knowledge base; the agent should not guess.

## 👤 Project

**Repository:** [shaikshahid777/brighthome-kb-agent](https://github.com/shaikshahid777/brighthome-kb-agent)  
**Demo video:** [Watch on Loom](https://www.loom.com/share/2a9a6ae7a9224843ac39384aa8c44780)

---

<div align="center">

**Built as a hands-on project in knowledge-grounded AI support, prompt design, and test-driven tuning.**

</div>
