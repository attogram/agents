# Working with Jules

This document provides guidance for human collaborators on how to work effectively with Jules, an AI software engineer.

## Prerequisites

For a high-level overview of how to work with AI agents in this repository, please first review the main [HUMANS.md](../HUMANS.md) file.

## Core Directives

- **Role:** Jules is an extremely skilled software engineer.
- **Purpose:** To assist you by completing coding tasks, such as solving bugs, implementing features, and writing tests.
- **Method:** Jules is resourceful and uses the tools at its disposal to accomplish goals. It follows a structured, plan-based approach to its work.

## The Collaborative Workflow

Working with Jules is an interactive and iterative process.

### 1. Pre-Planning Discussion
Before beginning any work, Jules will engage in a conversation to fully understand the task. This "pre-planning" phase is crucial for refining requirements and agreeing on a detailed plan. Your input during this stage is vital to ensure the final outcome meets your expectations.

### How Jules Follows a Plan
Jules's work is guided by the plan we agree upon. The platform it runs on helps it keep track of the steps. When Jules reports `plan_step_complete()`, the platform automatically advances it to the next step. This means Jules doesn't need to track step numbers itself; it focuses only on the current task provided by the system.

### 2. Pull Request and Iteration
Once a plan is agreed upon, Jules will perform the work and submit a pull request.
- **Iterative Updates:** For any follow-up changes or feedback, Jules will add new commits to the *same branch*.
- **Branching:** Jules will always work on the existing branch for a task. A new branch will **only** be created if you explicitly ask for one, or for a completely new and unrelated task after the current PR is merged.

## Operational Modes

Jules has different modes of operation you can request.

### Standard Mode
This is the default mode. Jules provides professional, concise communication, focusing on executing the plan efficiently.

### DEBUG mode
If you want to understand Jules's reasoning in extreme detail, you can ask it to enter "DEBUG mode". In this mode, it will announce each action it is about to take and why. This is useful for debugging or for gaining a granular understanding of its workflow.

---
