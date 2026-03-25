---
layout: post
title: Syncfusion Flutter Agent Skills for AI Assistants | Syncfusion
description: Learn how to install and use Syncfusion Agent Skills to enhance AI assistants with accurate Syncfusion Flutter widget guidance.
control: Skills
platform: flutter
documentation: ug
domainurl: ##DomainURL##
---

# Syncfusion Flutter Agent Skills for AI Assistants

This guide introduces **Syncfusion Flutter Skills**, a knowledge package that enables AI assistants (VS Code, Cursor, CodeStudio, etc.) to understand and generate accurate Syncfusion<sup style="font-size:70%">&reg;</sup> Flutter code using official APIs, patterns, and theming guidelines.

Syncfusion<sup style="font-size:70%">&reg;</sup> Skills eliminate common issues with generic AI suggestions by grounding the assistant in accurate Syncfusion<sup style="font-size:70%">&reg;</sup> widget usage patterns, API structures, supported features, and project‑specific configuration.

## Installation

Choose one of the following commands to install [Syncfusion<sup style="font-size:70%">&reg;</sup> Flutter widgets skills](https://github.com/syncfusion.com/flutter-skills.git) based on your preference. Users can also explore Syncfusion skills from the [marketplace](https://skills.sh/syncfusion/).

```bash
# Install all widget skills at once
npx skills add syncfusion/flutter-skills -y

# Choose and install skills interactively from the terminal
npx skills add syncfusion/flutter-skills
```

This registers the Syncfusion<sup style="font-size:70%">&reg;</sup> skill pack so your AI assistant can automatically load it in supported IDEs such as [Code Studio](https://help.syncfusion.com/code-studio/reference/configure-properties/skills), [Visual Studio Code](https://code.visualstudio.com/docs/copilot/customization/agent-skills), and [Cursor](https://cursor.com/docs/skills).

To learn more about the Skills CLI, refer [here](https://skills.sh/docs). 

## What's included

1. **Widget Usage & API Knowledge** — Curated, Skill‑based guidance that captures how to add, configure, and compose Syncfusion® Flutter widgets, including key properties, callbacks, required parameters, and common integration patterns.
2. **Patterns & Best Practices** — Practical recommendations for API structures, state‑handling approaches, and feature‑configuration workflows (for example, paging, sorting, and filtering for data widgets). All guidance is authored directly within the Skill file rather than being fetched from documentation.
3. **Design‑System Guidance** — Includes information related to themes, dark/light variants, and icon usage patterns across Syncfusion® Flutter widgets.

## How Syncfusion<sup style="font-size:70%">&reg;</sup> Agent Skills Work

1. **Reads the relevant Skill files based on the user's query**, with the assistant retrieving widget usage patterns, APIs, and best‑practice guidance from the installed Syncfusion® Skills.
2. **Enforces Syncfusion<sup style="font-size:70%">&reg;</sup> best practices**, including:

   - Using the required widget properties and constructors for each widget.
   - Configuring applicable widget features (for example, paging, sorting, filtering, and other feature configurations).
   - Adding the correct theme and package imports.
3. **Generates widget‑accurate code**, avoiding invalid properties or unsupported patterns

### Using the AI Assistant

Once skills are installed, the assistant can be used to generate and update Syncfusion<sup style="font-size:70%">&reg;</sup> Flutter code for tasks such as:

- "Add a DataGrid with paging, sorting, and filtering"
- "Add a Line Chart with markers"
- "Create a Calendar with week view"

## See also

- [Agent Skills Standards](https://agentskills.io/home)
- [Skills CLI](https://skills.sh/docs)
