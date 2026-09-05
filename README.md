<!-- SPDX-License-Identifier: Apache-2.0 AND CC-BY-4.0 -->
<!-- Copyright (c) 2026 NVIDIA Corporation. All rights reserved. -->

# NVIDIA Agent Skills

**Official, NVIDIA-verified skills for AI agents.**

[![NVIDIA](https://img.shields.io/badge/NVIDIA-Verified-76B900?style=flat&logo=nvidia&logoColor=white)](https://nvidia.com)
[![Agent Skills Spec](https://img.shields.io/badge/Agent%20Skills-Specification-blue)](https://agentskills.io)
[![License](https://img.shields.io/badge/License-Apache%202.0%20%2B%20CC--BY--4.0-green.svg)](LICENSE)

> 📖 **Docs:** [docs.nvidia.com/skills](https://docs.nvidia.com/skills) &nbsp;·&nbsp;
> 📺 **Livestream:** [From Vulnerable to Verified](https://www.youtube.com/watch?v=sVpKonYJ4D4&list=PL5B692fm6--vEL0FwctKghCpyEnBGAQJA&index=1) &nbsp;·&nbsp;
> 📝 **Blog:** [NVIDIA Verified Agent Skills: Capability Governance for AI Agents](https://developer.nvidia.com/blog/nvidia-verified-agent-skills-provide-capability-governance-for-ai-agents/)

---

Skills are portable instruction sets that teach AI agents how to use NVIDIA CUDA-X libraries, AI Blueprints, and platform tools correctly. This repository is a catalog: skills are maintained in their respective product repos and mirrored here daily via an automated sync pipeline. We are making NVIDIA skills available publicly and building this catalog in the open; see the [Roadmap](#roadmap) for what is planned next.

---

## Quickstart

Install NVIDIA skills with the default [`skills` CLI](https://github.com/vercel-labs/skills) flow:

```bash
npx skills add nvidia/skills
```

The CLI runs through `npx` and prompts you to choose a skill and install destination. You do not need to clone this repo or copy skill folders by hand.

The skill is available the next time your agent loads skills and encounters a relevant task. For example, ask your agent to "solve a linear programming problem with cuOpt" and the skill guides it through the cuOpt Python API.

### Install One Skill Without Prompts

Use this when you already know the skill name and want to skip prompts.

```bash
npx skills add nvidia/skills --skill cuopt-numerical-optimization-api-python --yes
```

Replace `cuopt-numerical-optimization-api-python` with any skill name from the [Skill Catalog](#skill-catalog).

### Install for a Specific Agent

Use `--agent` to target a specific AI coding agent. These are common client targets; for the full list of supported clients, see the [`skills` CLI Supported Agents table](https://github.com/vercel-labs/skills#supported-agents).

**Claude Code**

```bash
npx skills add nvidia/skills --skill cuopt-numerical-optimization-api-python --agent claude-code
```

**Codex**

```bash
npx skills add nvidia/skills --skill cuopt-numerical-optimization-api-python --agent codex
```

**Cursor**

```bash
npx skills add nvidia/skills --skill cuopt-numerical-optimization-api-python --agent cursor
```

**Kiro**

```bash
npx skills add nvidia/skills --skill cuopt-numerical-optimization-api-python --agent kiro-cli
```

Use `--agent` more than once to install the same skill into multiple agents.

```bash
npx skills add nvidia/skills \
  --skill cuopt-numerical-optimization-api-python \
  --agent claude-code \
  --agent codex \
  --agent cursor \
  --agent kiro-cli
```

### Browse the Catalog

Use this when you want to see available NVIDIA skills before installing anything.

```bash
npx skills add nvidia/skills --list
```

For non-interactive installs, global installs, agent-specific installs, updates, removals, and fallback manual copying, see [Advanced installation](docs/advanced-install.mdx).

---

## Skill Catalog

<!-- skills-table-start -->
| Product | Description | Skills | Catalog | Source | Version |
|---------|-------------|:------:|---------|--------|---------|
| **AIQ** | NVIDIA AI-Q Blueprint - deploy local AI-Q services and run shallow or deep research workflows as agent skills. | 2 | [`skills/aiq-research/`](skills/aiq-research) | [Source](https://github.com/NVIDIA-AI-Blueprints/aiq/tree/develop/skills/aiq-research) | [`bf4e67d`](https://github.com/NVIDIA-AI-Blueprints/aiq/commit/bf4e67d1564ef8d2ec8f65b5f9001e512befc095) · 2026-08-28 |
| **cuOpt** | GPU-accelerated optimization — vehicle routing, linear programming, quadratic programming, installation, server deployment, and developer tools. | 9 | [`skills/cuopt/`](skills/cuopt) | [Source](https://github.com/NVIDIA/cuopt/tree/main/skills) | [`0cccfd3`](https://github.com/NVIDIA/cuopt/commit/0cccfd3e426f391feaadc2afd1f9ead1533ab2ac) · 2026-09-03 |
| **DeepStream** | Agentic skills for guided DeepStream development. | 2 | [`skills/deepstream/`](skills/deepstream) | [Source](https://github.com/NVIDIA-AI-IOT/DeepStream_Coding_Agent/tree/main/skills) | [`3daf16a`](https://github.com/NVIDIA-AI-IOT/DeepStream_Coding_Agent/commit/3daf16ae5168dd685608bb929fb4f5513f308045) · 2026-05-28 |
| **Megatron-Bridge** | Bridge between NeMo and Megatron — data processing, model conversion, and training utilities. | 21 | [`skills/Megatron-Bridge/`](skills/Megatron-Bridge) | [Source](https://github.com/NVIDIA-NeMo/Megatron-Bridge/tree/main/skills) | [`da6680c`](https://github.com/NVIDIA-NeMo/Megatron-Bridge/commit/da6680cc90141089050a954d83ed6eb9d1085007) · 2026-09-04 |
| **Megatron-Core** | Large-scale distributed training — model parallelism, pipeline parallelism, and mixed precision. | 9 | [`skills/Megatron-Core/`](skills/Megatron-Core) | [Source](https://github.com/NVIDIA/Megatron-LM/tree/main/skills) | [`b1fe759`](https://github.com/NVIDIA/Megatron-LM/commit/b1fe7599e18a213292600177ad7ff290a1127160) · 2026-09-05 |
| **NeMo-RL** | RLHF training on Ray — GRPO, DPO, and SFT for LLMs and VLMs with FSDP2 and Megatron-Core. | 5 | [`skills/NeMo-RL/`](skills/NeMo-RL) | [Source](https://github.com/NVIDIA-NeMo/RL/tree/main/skills) | [`5368eff`](https://github.com/NVIDIA-NeMo/RL/commit/5368eff5f6bc7287f5a3d7fdc762530396610b1c) · 2026-09-04 |
| **Skill Card Generator** | Reads an agent skill's source files and produces a skill card plus a review table. Use when a skill directory exists and a governance card needs to be generated or updated. | 1 | [`skills/skill-card-generator/`](skills/skill-card-generator) | [Source](https://github.com/NVIDIA/Trustworthy-AI/tree/main/skills/skill-card-generator) | [`efdbb21`](https://github.com/NVIDIA/Trustworthy-AI/commit/efdbb21af78cb17eaf55ef5533d956939ab9f1dc) · 2026-08-27 |
| **Video Search and Summarization** | VSS Blueprint — deploy profiles, search and summarize video, generate analysis reports, manage alerts and incidents, query VIOS sensors, and use the RTVI VLM microservice. | 16 | [`skills/video-search-and-summarization/`](skills/video-search-and-summarization) | [Source](https://github.com/NVIDIA-AI-Blueprints/video-search-and-summarization/tree/main/skills) | [`b5cf39f`](https://github.com/NVIDIA-AI-Blueprints/video-search-and-summarization/commit/b5cf39f32f287663f6a6b7060b8f085cca219137) · 2026-08-31 |
<!-- skills-table-end -->

---

## Getting Help & Contributing

For skill-related issues, feature requests, new skill ideas, discussions, and contributions — use the source repo for the relevant product:

<!-- help-table-start -->
| Product | Issues | Discussions | Contributing | Security |
|---------|--------|-------------|--------------|----------|
| **AIQ** | [Issues](https://github.com/NVIDIA-AI-Blueprints/aiq/issues) | [Discussions](https://github.com/NVIDIA-AI-Blueprints/aiq/discussions) | [Contributing](https://github.com/NVIDIA-AI-Blueprints/aiq/blob/develop/CONTRIBUTING.md) | [Security](https://github.com/NVIDIA-AI-Blueprints/aiq/blob/develop/SECURITY.md) |
| **cuOpt** | [Issues](https://github.com/NVIDIA/cuopt/issues) | [Discussions](https://github.com/NVIDIA/cuopt/discussions) | [Contributing](https://github.com/NVIDIA/cuopt/blob/main/CONTRIBUTING.md) | [Security](https://github.com/NVIDIA/cuopt/blob/main/SECURITY.md) |
| **DeepStream** | [Issues](https://github.com/NVIDIA-AI-IOT/DeepStream_Coding_Agent/issues) | [Discussions](https://github.com/NVIDIA-AI-IOT/DeepStream_Coding_Agent/discussions) | [Contributing](https://github.com/NVIDIA-AI-IOT/DeepStream_Coding_Agent/blob/main/CONTRIBUTING.md) | [Security](https://github.com/NVIDIA-AI-IOT/DeepStream_Coding_Agent/blob/main/SECURITY.md) |
| **Megatron-Bridge** | [Issues](https://github.com/NVIDIA-NeMo/Megatron-Bridge/issues) | [Discussions](https://github.com/NVIDIA-NeMo/Megatron-Bridge/discussions) | [Contributing](https://github.com/NVIDIA-NeMo/Megatron-Bridge/blob/main/CONTRIBUTING.md) | [Security](https://github.com/NVIDIA-NeMo/Megatron-Bridge/blob/main/SECURITY.md) |
| **Megatron-Core** | [Issues](https://github.com/NVIDIA/Megatron-LM/issues) | [Discussions](https://github.com/NVIDIA/Megatron-LM/discussions) | [Contributing](https://github.com/NVIDIA/Megatron-LM/blob/main/CONTRIBUTING.md) | [Security](https://github.com/NVIDIA/Megatron-LM/blob/main/SECURITY.md) |
| **NeMo-RL** | [Issues](https://github.com/NVIDIA-NeMo/RL/issues) | [Discussions](https://github.com/NVIDIA-NeMo/RL/discussions) | [Contributing](https://github.com/NVIDIA-NeMo/RL/blob/main/CONTRIBUTING.md) | [Security](https://github.com/NVIDIA-NeMo/RL/blob/main/SECURITY.md) |
| **Skill Card Generator** | [Issues](https://github.com/NVIDIA/Trustworthy-AI/issues) | [Discussions](https://github.com/NVIDIA/Trustworthy-AI/discussions) | [Contributing](https://github.com/NVIDIA/Trustworthy-AI/blob/main/CONTRIBUTING.md) | [Security](https://github.com/NVIDIA/Trustworthy-AI/blob/main/SECURITY.md) |
| **Video Search and Summarization** | [Issues](https://github.com/NVIDIA-AI-Blueprints/video-search-and-summarization/issues) | [Discussions](https://github.com/NVIDIA-AI-Blueprints/video-search-and-summarization/discussions) | [Contributing](https://github.com/NVIDIA-AI-Blueprints/video-search-and-summarization/blob/main/CONTRIBUTING.md) | [Security](https://github.com/NVIDIA-AI-Blueprints/video-search-and-summarization/blob/main/SECURITY.md) |
<!-- help-table-end -->

For issues with **this catalog repo itself** (README, structure, listing a new product): [open an issue here](../../issues).

---

## Verifying Skills

Every published skill ships with a detached OMS signature (`skill.oms.sig`). The sync pipeline drops any skill missing `skill.oms.sig`, `skill-card.md`, or `evals.json` before publishing, so anything in the catalog has all three artifacts.

Verify a skill against the NVIDIA trust anchor [`nv-agent-root-cert.pem`](nv-agent-root-cert.pem):

```bash
pip install model-signing
model_signing verify certificate SKILL_DIR \
  --signature SKILL_DIR/skill.oms.sig \
  --certificate_chain nv-agent-root-cert.pem \
  --ignore_unsigned_files
```

See [Verify Signed Agent Skills](docs/signing-agent-skills.mdx) for signature layout, the trust pipeline, and policy options.

---

## Roadmap

- ✅ Public skills catalog with NVIDIA-verified skills across multiple products
- ✅ Automated sync pipeline with skills mirrored from product repos daily
- ✅ Security scanning for all published skills covering instruction safety and supply-chain integrity
- ✅ Skills signing so every published skill carries a verifiable NVIDIA signature
- ✅ Skills universal evaluation criteria and task-specific criteria
- ✅ Skill Card with machine-readable metadata for identity, provenance, quality, and behavioral boundaries
- 🔲 Compliance gates before external publication
- 🔲 Syndication to external marketplaces and MCP hubs

---

## Repository Structure

```
NVIDIA/skills/
├── skills/                      # Verified skills, mirrored daily from product repos
│   ├── README.md                 # Install guidance for people browsing this folder directly
│   ├── aiq-research/             # AIQ — deep/shallow research workflow
│   ├── aiq-deploy/               # AIQ — local service deployment
│   └── cuopt/                    # cuOpt skills (routing, optimization, server, install, …)
├── components.d/                # Product registry — one file per component, teams onboard here
│   ├── README.md                 # Schema and onboarding instructions
│   ├── aiq.yml
│   ├── cuopt.yml
│   └── …                         # one file per registered product
├── plugins/                     # Packaged plugin distributions
│   └── nvidia-skills/            # Curated NVIDIA skills bundle (Claude Code, Codex)
├── plugins.d/                   # Plugin build registry — config for `build-plugins.py`
│   ├── README.md
│   ├── _defaults.yml
│   └── nvidia-skills.yml
├── .claude-plugin/              # Claude Code marketplace metadata
│   └── marketplace.json
├── .agents/plugins/             # Agent marketplace metadata (other clients)
│   └── marketplace.json
├── docs/                        # Long-form documentation (published via Fern)
│   ├── README.md                 # How to build the docs locally
│   ├── index.mdx
│   ├── advanced-install.mdx
│   ├── agent-skill-trust-pipeline.mdx
│   ├── release-checklist.mdx
│   ├── scanning-agent-skills.mdx
│   ├── signing-agent-skills.mdx
│   └── skill-cards.mdx
├── fern/                        # Fern docs site configuration
├── .github/
│   ├── workflows/                # Sync pipeline, plugin validation, DCO check
│   └── scripts/                  # regenerate-readme.sh, build-plugins.py
├── nv-agent-root-cert.pem       # Trust anchor for OMS signature verification
├── CHANGELOG.md
├── CONTRIBUTING.md              # Contribution guidelines
├── SECURITY.md                  # Security reporting policy
├── CODE_OF_CONDUCT.md           # Community code of conduct
└── LICENSE                      # Apache 2.0 / CC BY 4.0
```

Skills are maintained in their respective product repos (see the **Source** column in the [Skill Catalog](#skill-catalog)) and automatically synced to this repo daily. Products only appear under `skills/` after the sync pipeline confirms each skill carries `skill.oms.sig`, `skill-card.md`, and `evals.json`.

---

## Standards & Compatibility

This repository adheres to the [Agent Skills specification](https://agentskills.io/specification):

- Skills are portable directories with a `SKILL.md` file at their root.
- Metadata uses YAML frontmatter with required `name` and `description` fields.
- Skills follow a progressive disclosure model — lightweight metadata loads at startup, full instructions load on activation.
- Validate your skill using the [`skills-ref`](https://github.com/agentskills/agentskills/tree/main/skills-ref) reference library.

---

## License

This project is dual-licensed under the [Apache License 2.0](LICENSE) and [Creative Commons Attribution 4.0 International (CC BY 4.0)](LICENSE).
