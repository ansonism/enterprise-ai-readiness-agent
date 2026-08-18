# Enterprise AI Readiness Agent

    An executive-grade assessment agent that scores enterprise readiness for generative and agentic AI across strategy, data, architecture, security, governance, operating model, engineering, observability, and value realization.

    ## Why this exists

    Assess an organization's readiness to deploy AI and agentic systems at enterprise scale, identify capability gaps, prioritize investments, and generate a sequenced transformation roadmap.

    This repository is intentionally scaffolded as a **production-oriented agent project**, not a prompt-only demo. It starts with a deterministic mock provider so the complete orchestration path can be executed locally before adding any commercial LLM.

    ## Core workflow

    ingest_assessment_evidence -> score_readiness_domains -> validate_scores_against_evidence -> identify_blockers_and_dependencies -> prioritize_use_cases_and_foundations -> build_target_maturity_profile -> generate_30_60_90_and_12_month_roadmap -> produce_executive_assessment

    ## Specialized agents

    - `strategy_assessor`
- `data_assessor`
- `platform_assessor`
- `security_assessor`
- `governance_assessor`
- `operating_model_assessor`
- `engineering_assessor`
- `value_assessor`
- `readiness_judge`

    ## Planned tool adapters

    - `evidence_loader`
- `questionnaire_loader`
- `maturity_model`
- `scoring_engine`
- `roadmap_builder`

    ## Quick start

    ```bash
    python3 -m venv .venv
    source .venv/bin/activate
    pip install -e ".[dev]"
    enterprise-ai-readiness run examples/sample_input.json --output out/result.json
    pytest
    ```

    Or:

    ```bash
    make setup
    make demo
    make test
    ```

    ## Safety defaults

    - Mock/dry-run behavior is the default.
    - External systems are accessed only through explicit adapters.
    - No production mutation should be added without an approval gate.
    - Facts, assumptions, hypotheses and recommendations should remain distinguishable in outputs.
    - Credentials must come from environment/secret stores, never source control.

    ## Codex implementation guide

    Start with [`SKILL.md`](./SKILL.md). It defines the mission, architecture, implementation sequence, acceptance criteria and guardrails Codex should follow.

    ## Repository layout

    ```text
    .
    ├── AGENTS.md
    ├── SKILL.md
    ├── config/
    ├── docs/
    ├── evals/
    ├── examples/
    ├── kubernetes/
    ├── prompts/
    ├── scripts/
    ├── src/ai_readiness/
    ├── terraform/
    └── tests/
    ```

    ## Current state

    **Phase 1 core.** The typed harness validates configuration and domain inputs, writes an atomic checkpoint after every stage, supports idempotent resume by run ID, and emits redacted structured logs. The default CLI stores state under `out/state/`. `make demo`, `make test`, and `make lint` verify the runnable mock-provider implementation.