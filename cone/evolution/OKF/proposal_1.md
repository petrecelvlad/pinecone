---
type: Evolution Proposal
title: Evolution & Improvement Roadmap
description: Comprehensive strategy to evolve cone-lite — partially superseded by OKF migration.
tags: [evolution, proposal]
timestamp: 2026-06-23T00:00:00Z
status: PROPOSED
impact: MEDIUM
affected_pillar: both
author: External agent
---

Evolution & Improvement Roadmap
Here is a comprehensive strategy to evolve Cone-Lite from a promising framework into a foundational ecosystem standard.

Phase 1: Deepen OKF Integration & Validation
The migration to OKF is a strong first step. The next priority is to fully leverage its capabilities for interoperability and trust.

Improvement Area
Current State
Proposed Evolution
Benefit
Schema Alignment	Migrated to OKF v0.1 .	Map all Propolis metadata fields to OKF's type, title, description, resource, tags, and timestamp 
marktechpost
 .	Standardized Context. Enables any OKF-compliant consumer (visualizer, agent, tool) to understand Cone-Lite bundles natively.
Validation Tooling	None evident.	Create an okf-validator script (e.g., in package.json) that checks YAML frontmatter and link integrity.	Quality Assurance. Ensures bundles are always conformant and prevents agents from ingesting malformed context.
Graph Visualization	Directory structure only.	Adopt or reference Google's static HTML visualizer that turns any OKF bundle into an interactive graph view in a single self-contained file 
searchenginejournal
 .	Human Insight. Provides a powerful, no-install way for developers and architects to visualize and navigate the knowledge graph.

Phase 2: Expand the Ecosystem & Agent Support
To move beyond a template, the framework needs tools and connectors that make it easy to adopt and maintain.

🔧 **Ecosystem Expansion Details**
Agent SDKs & Hooks: Develop lightweight libraries (e.g., @cone-lite/sdk-claude, @cone-lite/sdk-copilot) that provide pre-built functions for agents to:
Parse the AGENT.md and load the correct onboarding sequence.
Interpret @propolis metadata and enforce file constraints.
Append to the session log and propose handoff summaries.
IDE Plugin (VS Code): Build an extension that:
Auto-completes @propolis blocks based on the current file's type.
Provides a sidebar view of the knowledge graph (via the visualizer).
Shows the current agent's active persona and loaded skills.
Pre-built Bundles & Starter Templates: Curate and publish example bundles for common tech stacks (e.g., React + Node.js, Python + FastAPI) that demonstrate OKF+Cone-Lite best practices. This lowers the barrier to entry.
Phase 3: Enhance the Self-Evolution Mechanism
The framework includes a self-evolution skill, which is its most powerful long-term feature. This needs to be made more robust and actionable.

Identifies Friction

Successful Pattern

Agent Works

Session Ends

Evolution Skill Triggered

Analyze Session

Generate Proposal
e.g., 'Add skill: Debug Memory Leak'

Generate Proposal
e.g., 'Update persona: Prioritize Testability'

Store in
cone/evolution/

Human Reviews & Approves

Proposal Integrated
into Agent or Project Pillar

Proposed Enhancements:

Structured Proposal Format: Define a standard OKF-based template for evolution proposals (e.g., type: EvolutionProposal). This makes proposals machine-readable and processable.
Impact Analysis: The evolution skill should analyze the potential impact of a proposal on existing documents and sessions before generating it.
Automated Merge Path: For low-risk, high-value proposals (like adding a new skill), create a semi-automated path where a human can approve and the framework automatically integrates the change into the correct cone/ subdirectory.


@propolis blocks must be structured as OKF-compliant YAML frontmatter, ensuring any OKF-compatible consumer tool can instantly read Cone-Lite files.

2. Add an OKF Bundle Linter Script
To guarantee the cone/ directory remains a valid OKF bundle as it evolves, we need immediate automated validation.

Action: Introduce a lightweight validation step into the existing package.json scripts.
Deliverable: A script command (e.g., npm run lint:okf) that recursively scans the cone/ directory, checks every markdown file for the required OKF type field, validates YAML syntax, and flags broken internal markdown links. This prevents agents from ingesting malformed context.
3. Integrate a Static Knowledge Graph Visualizer
The directory structure is hard for humans to parse holistically. We can leverage existing open-source OKF tooling to solve this immediately.

Action: Add a build step that compiles the cone/ directory into a single, standalone HTML file.
Deliverable: A new script command (e.g., npm run visualize) that generates a self-contained graph.html file in the root directory. This file will render the OKF markdown links as an interactive, searchable node graph, giving developers a visual UI to audit the agent's knowledge architecture without any backend or installation requirements.
4. Standardize the Evolution Proposal Template
The framework includes a self-evolution skill, but it currently lacks a machine-readable output format.

Action: Create a formal OKF-concept template for the cone/evolution/ directory.
Deliverable: A template markdown file defining type: EvolutionProposal. It will specify required YAML fields (e.g., affected_pillar, proposal_type, impact_level) and a standardized markdown body structure (Problem, Proposed Change, Integration Steps). This ensures that when the agent generates self-improvement ideas, they are outputted in a structured, queryable format rather than freeform text.