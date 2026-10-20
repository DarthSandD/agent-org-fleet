# Darren Labs Org Index

The full agent org chart: 115 titled roles across 10 departments, NVIDIA-style ladder (C-suite agent, VP, Director, Principal, Staff, Senior, Engineer, Associate). Each role file in this folder pairs at spawn time with the base soul at `~/workspace/soul-forge-full/SUBAGENT_SOUL.md`. No generic names: every title is a real big-company title.

## Spawn rule

Every spawn gets: base `SUBAGENT_SOUL.md` + one role file from this folder + the role's matched skills preloaded. QA verification is always a separate spawn from the builder. Pushes to GitHub, real money, irreversible deletes and credentials always pause for Darren.

## Default staffing

Every future build auto-staffs from this org without waiting for a staffing request: the coordinator reads the task, picks roles from the task to role lookup below, and spawns them in parallel when the parts are independent. A standard build staffs at minimum a builder at Senior level of the matching function, a separate QA/verifier spawn for verification, and the relevant leadership role (VP, Director, or Principal level) only when the task crosses functions or hits a hard blocker. Small, single-file fixes staff one Engineer or Associate plus the QA spawn. Escalation follows the reporting lines in the org tree; nobody reviews their own work.

## Org tree (reporting lines)

### Executive
- **CTO-Chief Architect** (reports to Darren, CEO) - CTO-Chief_Architect.md
- **Chief of Staff** (reports to Darren, CEO) - Chief_of_Staff.md
- VP Engineering, VP Product, VP Design, VP Data (report to CTO-Chief Architect)
- Head of AI Research (reports to VP Engineering)

### Engineering (Director_of_Engineering under VP Engineering; Director_of_Mobile under VP Engineering)
- Frontend: Staff_Frontend_Engineer > Senior_Frontend_Engineer > Frontend_Engineer > Associate_Frontend_Engineer
- Backend: Staff_Backend_Engineer > Senior_Backend_Engineer > Backend_Engineer > Associate_Backend_Engineer; SDK_Engineer > Senior_Backend_Engineer
- Fullstack: Senior_Fullstack_Engineer > Fullstack_Engineer > Associate_Fullstack_Engineer
- Mobile: Senior_Mobile_Engineer > Mobile_Engineer > Associate_Mobile_Engineer (Director_of_Mobile above)
- Embedded: Senior_Embedded_Engineer > Embedded_Engineer > Associate_Embedded_Engineer; Firmware_Engineer > Senior_Embedded_Engineer
- API_Design_Engineer > Director_of_Engineering

### Platform and Infrastructure (Director_of_Platform under VP Engineering)
- Principal_Platform_Architect > CTO-Chief_Architect
- Staff_SRE, Senior_SRE, Release_Manager, Database_Reliability_Engineer, Chaos_Engineer > Director_of_Platform
- DevOps_Engineer, Platform_Engineer, Network_Engineer, Cloud_Cost_Engineer, Build_CI_Engineer > Senior_SRE

### QA (Director_of_QA under VP Engineering; QA_Lead under Director_of_QA)
- Staff_QA_Engineer, Senior_QA_Automation_Engineer, QA_Engineer, QA_Associate, Performance_Test_Engineer > QA_Lead

### Security (Head_of_Security under Director_of_Platform)
- Security_Architect, Senior_Security_Engineer, AppSec_Engineer, Compliance_Engineer, Data_Privacy_Officer, Incident_Response_Engineer > Head_of_Security
- Penetration_Test_Engineer > Senior_Security_Engineer

### Data and ML/AI (Senior_Data_Engineer under Director_of_Engineering; Principal_ML_Architect under CTO-Chief_Architect)
- ML: Staff_ML_Engineer > Principal_ML_Architect; Senior_ML_Engineer, ML_Engineer, MLOps_Engineer, Prompt_Engineer, Agent_Orchestration_Engineer, Computer_Vision_Engineer, Speech_Engineer, Evaluation_Engineer > Staff_ML_Engineer
- Data: Data_Engineer, Analytics_Engineer > Senior_Data_Engineer; BI_Analyst > Analytics_Engineer

### Product and Program (VP_Product; Senior_TPM under VP_Engineering)
- Senior_Product_Manager > VP_Product; Product_Manager, Associate_PM, Product_Analyst, Product_Operations, UX_Researcher > Senior_Product_Manager; Product_Marketing_Manager > VP_Product
- Senior_TPM > VP_Engineering; TPM, Scrum_Master > Senior_TPM

### Design (Design_Director under VP_Design)
- Principal_Product_Designer, Senior_UX_Designer, Senior_UI_Designer, Brand_Designer, Accessibility_Engineer, Visual_QA_Designer > Design_Director
- UX_Designer, Interaction_Designer > Senior_UX_Designer; UI_Designer, Motion_Designer > Senior_UI_Designer
- Design_Systems_Engineer > Head_of_Design_Systems; Prototyping_Engineer > Principal_Product_Designer

### Content, Marketing and Growth (Content_Strategist under VP_Product)
- Senior_Copywriter, Technical_Copywriter, SEO_Specialist, Social_Media_Manager, Video_Producer, Community_Manager > Content_Strategist
- Product_Marketing_Manager > VP_Product (also in Product above)
- Growth_Engineer > Senior level; Email_Lifecycle_Engineer, Paid_Media_Specialist > Growth_Engineer

### Research, Documentation and Support
- REA_Research_Lead > CTO-Chief_Architect; Research_Analyst > REA_Research_Lead; Solutions_Architect > CTO-Chief_Architect
- Senior_Technical_Writer > Director_of_Engineering; Technical_Writer, API_Docs_Engineer, Knowledge_Base_Curator, Localization_Engineer > Senior_Technical_Writer
- Support_Engineer_L3 > Director_of_Engineering; Support_Engineer_L2 > Support_Engineer_L3; Developer_Advocate > Director_of_Engineering

## Task to role lookup

| Task | Spawn role |
|---|---|
| Architecture decision, REA spec, hard blocker | CTO-Chief_Architect |
| New feature, whole thing | Senior level of the matching function + QA_Verifier equivalent (Staff_QA_Engineer) |
| Web UI build or fix | Senior_Frontend_Engineer (mid/associate for small pieces) |
| API, database, backend logic | Senior_Backend_Engineer |
| Cross-stack build | Senior_Fullstack_Engineer |
| Mobile app work | Senior_Mobile_Engineer |
| Embedded, firmware, IoT | Senior_Embedded_Engineer or Firmware_Engineer |
| Deploy, infra, CI, release | DevOps_Engineer, Release_Manager, Platform_Engineer |
| Outage, reliability | Staff_SRE / Senior_SRE |
| Verify a fix, reproduce a bug | Staff_QA_Engineer or QA_Engineer (separate spawn, never the builder) |
| Security review, pentest, privacy | Security_Architect / Penetration_Test_Engineer / Data_Privacy_Officer |
| ML model, evals, agents, prompts | Staff_ML_Engineer / Prompt_Engineer / Agent_Orchestration_Engineer |
| Data pipelines, dashboards | Senior_Data_Engineer / Analytics_Engineer / BI_Analyst |
| Product spec, priorities | Senior_Product_Manager |
| UX, UI, brand, motion | Senior_UX_Designer / Senior_UI_Designer / Brand_Designer / Motion_Designer |
| Copy, SEO, social, video | Senior_Copywriter / SEO_Specialist / Social_Media_Manager / Video_Producer |
| Research, reverse engineering | REA_Research_Lead / Research_Analyst |
| Docs, API docs, support answers | Senior_Technical_Writer / API_Docs_Engineer / Support_Engineer_L3 |

## Notes

- RESEARCH_NOTES.md holds the fleet design research (patterns only, nothing copied).
- Old generic roles were retired out of the live folder. If you retire or
  replace a role, move the old file to `roles/_retired/` with a date stamp and
  a note saying do not spawn from them.
- Word counts per role file: 150-350 words, tight by design. Matched skill paths inside each file were verified to exist on disk at build time.
