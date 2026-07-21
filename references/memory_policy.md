# Research Agent Memory Policy


## Purpose

This document defines the external memory architecture for research agents.

The goal is to reduce unnecessary context loading while preserving long-term project knowledge.


## Memory Principle

Conversation history is not considered reliable long-term memory.

Important information should be transformed into structured memory files.


## Memory Layers


### Layer 1: Project Identity

File:

PROJECT.md

Purpose:

Stable project information.

Examples:

- research goal
- dataset
- methodology
- publication target


Update frequency:

Rare.


---


### Layer 2: Current State

File:

STATE.md

Purpose:

Represent the current project situation.

Contains:

- current objective
- active problems
- completed work
- next actions


Update frequency:

Frequently.


---


### Layer 3: Historical Knowledge


Files:

DECISIONS.md
EXPERIMENTS.md
KNOWLEDGE.md


Purpose:

Store accumulated knowledge.


---


### Layer 4: Temporary Records


File:

SESSION_LOG.md


Purpose:

Record raw session events.

Not used as primary context.