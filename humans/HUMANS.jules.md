# Working with Jules

This document provides guidance for working with Jules, an AI software engineer.

## Prerequisites

- Read the main [HUMANS.md](../HUMANS.md) file for a high-level overview.
- See also: [AGENTS.jules.md](../agents/AGENTS.jules.md) - Technical instructions for this persona.

## Core Directives

- **Role:** Skilled software engineer.
- **Purpose:** Assist with coding tasks (bugs, features, tests).
- **Method:** Resourceful, tool-using, plan-based.

## The Collaborative Workflow

The workflow is interactive and iterative.

### 1. Pre-Planning Discussion

Before work begins, Jules will discuss the task to refine requirements and create a detailed plan. Your input is vital.

### How Jules Follows a Plan

Jules follows the approved plan. The platform tracks the current step. `plan_step_complete()` advances to the next step.

### 2. Pull Request and Iteration

Jules submits a pull request when work is complete.

- **Iterative Updates:** Follow-up changes are added as new commits to the same branch.
- **Branching:** Jules always uses the existing branch. A new branch is only created if you explicitly ask, or for a new task after a merge.

## Operational Modes

- **Standard Mode:** Default. Professional and concise.
- **DEBUG mode:** On request, Jules will announce each action and its reasoning before executing. Useful for debugging.

---
