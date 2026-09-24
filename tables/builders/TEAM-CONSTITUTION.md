# Team constitution: table builders

This file is your constitution: one part of a harness, the part that says what
always holds and what you learned the hard way.

Score without the constitution: 4 / 7
Score with the constitution:    _ / 7
Traps that flipped and why (one line):

---

## 1. Which parts does a harness for your team need?

- Rules: the constitution below (spelling convention, banned libraries).
- Context: a shared glossary of domain terms, so everyone and the assistant
  use one word per concept.
- Knowledge sources: the team wiki, project READMEs, harness files, Jira
  stories.
- Guardrails: dependency checks (licence, team bans) before a library is
  added.
- Review gates: passing tests and 80%+ coverage on new code before a change
  is done.
- Security: no leaked secrets, a security check on every change.
- Connectors: a way for the assistant to read Jira and the wiki (not there
  yet).

## 2. Per part: why does it need to be said, and what do you expect to gain?

### Rules
- Why: mixed UK/US spelling (`colour`/`color`) in code caused database
  problems in mid-September 2026.
- Expected gain: one spelling everywhere, so names in code, the database and
  design documents match.

### Context (glossary)
- Why: people with different native languages use different terms for the
  same thing; the agreed terms only live in people's heads.
- Expected gain: a written glossary the team and the assistant can check
  names against.

### Knowledge sources
- Why: decisions live in the wiki, READMEs and Jira; an assistant that is not
  pointed at them never reads them.
- Expected gain: the assistant follows existing decisions instead of
  re-deciding them.

### Guardrails
- Why: PrimeNG changed its licence terms and is no longer allowed.
- Expected gain: no dependency with an unwanted licence or a team ban gets
  added.

### Review gates
- Why: parts of the code were poorly tested or had failing tests, and that
  led to problems.
- Expected gain: every change lands with passing tests, and new code is
  covered to at least 80%.

### Security
- Why: code must not leak secret information or leave loopholes.
- Expected gain: every change is checked for security problems before it
  lands, and no secrets end up in code, logs or responses.

### Connectors
- Why: Jira stories hold the context per change, but there is no Jira MCP
  connector.
- Expected gain: the assistant can read the story behind a change.

## 3. Which existing tools and services could you already connect or pull into your harness?

- Project READMEs: readable by the assistant today (in the repo).
- Harness files: readable by the assistant today (in the repo).
- Wiki: holds decisions and standards; not connected to the assistant yet.
- Jira: holds stories; no MCP connector yet.

## 4. The one thing you would put in place next week

- Add a coverage check to our pipeline that fails a build when new code is
  below 80% or any test fails.

---

## Rules for the assistant

### Ground rules
- Before changing code, read the project's `README.md` and the harness files
  in the repo, and follow what they say.
- Our decisions, standards and runbooks live in `../flowmetrics-wiki`. Read
  the relevant ones before you change code, and respect their `status` header.
- Build only what the task asks for. No extra features, options, endpoints
  or unrelated refactors; if you think something more is needed, name it in
  your summary instead of building it.

### Rules from experience
- Use UK English spelling in code (identifiers, database columns, API
  fields, config keys) and in design documents: `colour`, `cancelled`,
  `serialise`. (Mixed `colour`/`color` caused database problems, September
  2026.)
- Do not add or use PrimeNG. (PrimeNG changed its licence terms.)
- A change is not finished until the full test suite runs and passes. Fix or
  update tests your change breaks; do not skip or delete them. (Poorly tested
  parts and failing tests led to problems.)
- New code has at least 80% test coverage. (Same origin.)
- Never put secrets (passwords, API keys, tokens, connection strings) in
  code, committed config, logs, error messages or responses.
- Before calling a change finished, review it for security problems and
  list what you checked and found in your summary. New endpoints and inputs
  must not expose internal data or bypass existing authentication or
  validation.

### Knowledge sources
- Project `README.md` files: project setup and conventions. In the repo.
- Harness files: team rules, including this constitution. In the repo.
- Team wiki: decisions and standards. For run 2, `../flowmetrics-wiki`.
- Jira stories: requirements per change. Not reachable by the assistant yet;
  ask the developer for the story if the task needs it.
