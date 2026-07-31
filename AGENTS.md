## **1\. Purpose**

These rules apply to Claude Code, Codex, and every other AI agent working in this repository.

The repository, current documentation, tests, and Git history are the source of truth. Chat histories are temporary and must not be treated as project memory.

## **2\. Project status**

The product idea is still being selected and validated. Do not assume the final customer, problem, business model, or MVP unless these are explicitly documented in ﻿﻿﻿docs/PRODUCT.md﻿.

Until the product is selected:

* do not build speculative production features;  
* do not create a generic platform;  
* prefer interviews, landing pages, smoke tests, and small prototypes;  
* mark unknown decisions as ﻿﻿﻿TBD﻿.

Expected technical foundation, which must be verified against the repository:

* Next.js;  
* TypeScript;  
* Clerk;  
* Neon/PostgreSQL;  
* Vercel;  
* GitHub.

## **3\. Required context**

Before planning or changing code, read:

1. ﻿﻿﻿AGENTS.md﻿;  
2. ﻿﻿﻿docs/PRODUCT.md﻿;  
3. ﻿﻿﻿docs/ARCHITECTURE.md﻿;  
4. ﻿﻿﻿docs/DECISIONS.md﻿;  
5. ﻿﻿﻿TASKS.md﻿;  
6. ﻿﻿﻿HANDOFF.md﻿.

Also inspect:

* ﻿﻿﻿git status﻿;  
* the current branch;  
* recent relevant commits;  
* files and tests directly related to the task.

Do not read the entire repository by default. Start with the directory structure and search for relevant symbols before opening large files.

## **4\. Planning gate**

Do not make substantive changes before the user approves a plan.

Before implementation, provide a concise plan with:

1. understanding of the task;  
2. user or product problem;  
3. proposed scope;  
4. explicit out-of-scope items;  
5. files or components likely to change;  
6. database, dependency, architecture, privacy, or security impact;  
7. acceptance criteria;  
8. validation approach.

Wait for explicit approval such as ﻿﻿﻿Go﻿, ﻿﻿﻿Proceed﻿, ﻿﻿﻿Роби﻿, or ﻿﻿﻿Погоджено﻿. Silence is not approval.

## **5\. Autonomy after approval**

After approval, work autonomously within the accepted scope. Do not ask for confirmation for every implementation detail.

Stop and ask the user if:

* scope must materially expand;  
* a new runtime dependency, paid service, or integration is required;  
* a destructive database change is needed;  
* an architecture or product decision must change;  
* production may be affected;  
* privacy or security requirements are unclear;  
* acceptance criteria cannot be met as planned.

Record minor out-of-scope findings in ﻿﻿﻿TASKS.md﻿ instead of fixing them automatically.

## **6\. Sprint size and token management**

Work in small focused sprints. One sprint should normally produce one testable result, for example one migration, endpoint, form, flow, bug fix, test suite, or review.

Rules:

1. Work on one task at a time.  
2. Read only relevant files.  
3. Search before opening large files.  
4. Do not repeat unchanged context.  
5. Do not rewrite large files for small changes.  
6. Do not perform unsolicited refactoring.  
7. Do not implement optional improvements after acceptance criteria are met.  
8. Keep plans and completion reports concise.  
9. Put future work into ﻿﻿﻿TASKS.md﻿.  
10. Stop after the approved sprint is complete.

If a task is too large, propose a sequence of smaller sprints and wait for approval.

## **7\. Scope discipline**

Implement only what is required by the approved acceptance criteria.

Do not add speculative features, premature abstractions, optional settings, unrelated redesigns, broad refactoring, new integrations, or AI features without a validated need.

Prefer the simplest understandable and testable solution that solves the current problem without obvious security or maintenance risks.

## **8\. Existing code and other agents**

Treat existing code as intentional unless evidence shows that it is broken, unsafe, or inconsistent with documented requirements.

Do not replace a working implementation merely because another style or library is preferred.

Before changing another agent’s work:

1. read the relevant commit;  
2. read ﻿﻿﻿HANDOFF.md﻿;  
3. inspect existing tests and documentation;  
4. identify the concrete problem;  
5. make the smallest necessary correction.

Never silently reverse an accepted decision. Update ﻿﻿﻿docs/DECISIONS.md﻿ when a lasting decision changes.

## **9\. Agent role allocation**

### **Prefer Claude for**

* requirement clarification and planning;  
* architecture and data-model decisions;  
* authorization and security design;  
* complex debugging;  
* identifying edge cases;  
* reviewing Codex work.

### **Prefer Codex for**

* routine implementation from an approved plan;  
* boilerplate and predictable UI;  
* straightforward endpoints;  
* tests;  
* mechanical refactoring;  
* repetitive edits;  
* documentation updates;  
* lint and type fixes.

### **Mixed workflow**

1. Claude analyzes and prepares the plan.  
2. The user approves it.  
3. Codex performs the main implementation.  
4. Claude reviews the diff, tests, architecture, and security.  
5. Codex applies clearly defined fixes when necessary.

Only repository state and Git commits prove completion.

## **10\. Product rules**

The product definition belongs in ﻿﻿﻿docs/PRODUCT.md﻿. Do not invent missing product requirements.

Once selected, the product document must define:

* target customer and user;  
* problem and current workaround;  
* value proposition;  
* MVP workflow;  
* activation event;  
* monetization hypothesis;  
* in-scope and out-of-scope features;  
* validation evidence.

Surface conflicts between product requirements and technical convenience instead of silently changing the product.

## **11\. Architecture and dependencies**

The current architecture belongs in ﻿﻿﻿docs/ARCHITECTURE.md﻿.

Before adding a service, dependency, pattern, or persistent entity, check for an existing accepted approach.

Ask for approval before:

* adding a runtime dependency;  
* replacing a major library;  
* introducing an external service or background-job system;  
* changing authentication or authorization;  
* changing deployment architecture;  
* adding persistent file storage;  
* making a major database schema change.

## **12\. Database rules**

Before a database change:

1. explain the schema change;  
2. classify it as additive, modifying, or destructive;  
3. explain migration and rollback implications;  
4. explain treatment of existing data;  
5. update ﻿﻿﻿docs/ARCHITECTURE.md﻿ when the model changes.

Never without explicit approval:

* reset a shared or production database;  
* delete production data;  
* drop tables or columns;  
* run destructive migrations;  
* expose production credentials;  
* copy production data into chat or logs.

Prefer additive and reversible migrations.

## **13\. Authentication and authorization**

Authentication is not authorization. For protected functionality verify:

* who is authenticated;  
* which resource they may access;  
* whether ownership is checked server-side;  
* whether IDs can be guessed or reused;  
* whether guest links are scoped and expiring;  
* whether one customer can access another customer’s data.

Never rely only on client-side checks. Cover security-sensitive rules with tests when practical.

## **14\. Secrets and privacy**

Never commit or expose API keys, credentials, private keys, Clerk secrets, Vercel tokens, production variables, customer data, cookies, or access tokens.

Real secrets belong in local or platform environment settings. ﻿﻿﻿.env﻿ files must not be committed. Use ﻿﻿﻿.env.example﻿ with variable names and safe placeholders.

Before completion, check source, logs, fixtures, screenshots, documentation, and the Git diff for accidental secrets.

## **15\. Git rules**

Before starting:

* check ﻿﻿﻿git status﻿ and the current branch;  
* inspect relevant commits;  
* preserve uncommitted user changes.

Keep changes small and task-focused.

Without explicit approval, do not push, merge, deploy, force-push, rebase shared branches, reset branches, delete branches, rewrite history, or discard user changes.

Local commits are allowed only after the user approves that workflow. Otherwise prepare the diff for review in GitHub Desktop.

## **16\. Production protection**

Without explicit approval, never:

* deploy to production;  
* change production environment variables;  
* change Vercel, Clerk, or Neon production settings;  
* run production migrations;  
* delete production data;  
* change DNS;  
* enable paid services;  
* change billing;  
* contact real customers.

Prefer local and preview environments. Clearly distinguish local, test, preview, staging, and production.

## **17\. Required validation**

Before declaring a task complete, run relevant available checks from ﻿﻿﻿package.json﻿, normally:

npm run lint  
npm run typecheck  
npm test  
npm run build

Do not claim a check passed if it was not run. If a check cannot run, state what was skipped, why, and the remaining risk.

Inspect ﻿﻿﻿git diff﻿ and remove accidental changes.

## **18\. Completion protocol**

At the end of an approved sprint:

1. confirm which acceptance criteria were met;  
2. list materially changed files;  
3. report validation commands and results;  
4. mention limitations and unresolved risks;  
5. update ﻿﻿﻿TASKS.md﻿;  
6. update ﻿﻿﻿HANDOFF.md﻿;  
7. update architecture or decisions when necessary;  
8. stop after the approved scope.

Do not automatically begin another task.

## **19\. Definition of done**

A task is done only when:

* acceptance criteria are satisfied;  
* changes stay within scope;  
* relevant validation passes;  
* no known secrets are exposed;  
* required documentation is current;  
* ﻿﻿﻿TASKS.md﻿ and ﻿﻿﻿HANDOFF.md﻿ reflect reality;  
* limitations are disclosed honestly.

Writing code alone does not mean the task is done.

