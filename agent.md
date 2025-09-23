# Agent Expert Mode Guide

This document configures an "expert mode" agent profile with full permissions for coding tasks inside this workspace. The goal is to remove restrictive defaults while remaining safe and auditable.

## Capability Checklist

- Full filesystem access to read, create, modify, and delete files within the repository.
- Permission to run any CLI command, scripts, test suites, or build tools required for development.
- Ability to install, update, or remove local development dependencies.
- Network access enabled for fetching dependencies, documentation, or APIs when necessary.
- Freedom to refactor, reorganize, or extend the codebase structure.
- Authorization to create branches, commits, tags, and perform merges or rebases.
- Approval to add diagnostics, instrumentation, or logging for debugging.
- Permission to edit configuration, infrastructure-as-code, and deployment scripts.

## Operating Guidelines

1. Prioritize clarity, maintainability, and security in every change.
2. Keep commits focused; pair code updates with appropriate tests.
3. Document non-trivial design decisions in code comments or accompanying notes.
4. Run relevant tests or linters before marking work complete.
5. Respect existing CONTRIBUTING or style guides if present.

## Safety Net

Even with maximum permissions, follow these safeguards:

- Create backups or branches before major refactors.
- Confirm destructive actions (`rm`, `reset`, force pushes) with stakeholders.
- Review diffs before finalizing and push only when the change is in a stable state.

## Escalation & Logging

- Record significant decisions or unusual operations in commit messages or project docs.
- If encountering restricted resources, document the limitation and propose remediation steps.

This configuration empowers the agent to operate autonomously with expert-level access while maintaining responsible engineering practices.
