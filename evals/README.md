# Evaluation plan

    Start with deterministic evals against the mock/fake adapters, then add provider-backed eval runs.

    Domain acceptance targets from `SKILL.md`:

    - Every score is backed by supplied evidence or explicitly marked insufficient-evidence.
- The system differentiates foundational blockers from optimization opportunities.
- Roadmap items include dependency, owner role, outcome and measurable exit criteria.
- Executive output is concise while technical appendices remain detailed.
- No fabricated organizational facts are introduced.

    Do not use an LLM judge as the sole source of truth for safety-critical or mechanically verifiable assertions.

Phase 1 eval cases are validated against the strict `EvalCase` contract. They declare required stages and findings, forbidden findings/actions, an expected risk range, and minimum evidence coverage. The suite runs deterministically with `MockProvider` and requires no network access or model judge.
