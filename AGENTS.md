# Skill Development Guidelines

## Skill Authoring

Skills in this repo should be tool-agnostic by default. If a skill is intended to work in more than one tool, avoid assuming tool-specific files, install paths, or memory mechanisms unless the skill explicitly verifies them first.

If a skill is intentionally tool-specific, say so clearly in the description and workflow.

## Creating Skills

See README.md for instructions on creating a new skill.

## Registry

The `skills.json` file is the authoritative registry of all available skills. It's automatically generated during the build process.
