# Claude Preparedness Planner

A Claude-powered workspace for developing comprehensive, personalized preparedness strategies. This is not limited to any single context—it addresses holistic preparedness across physical safety, financial security, medical readiness, and more.

## How It Works

1. **Intake Interview**: The agent conducts a comprehensive interview to understand your situation, location, household, resources, and concerns.

2. **Risk Assessment**: Based on your intake, the agent generates a personalized risk profile identifying your highest-priority scenarios and current gaps.

3. **Action Planning**: Transform the assessment into a prioritized, budgeted action plan with clear phases and milestones.

4. **Document Generation**: Create SOPs (Standard Operating Procedures), decision flowcharts, and checklists tailored to your specific situation.

## Quick Start

Open this workspace in Claude Code and use these commands:

```
/intake     - Begin the intake interview
/assess     - Generate your risk assessment
/plan       - Create your action plan
/sop [scenario]  - Generate an SOP (e.g., /sop evacuation)
/flowchart [scenario] - Generate a decision flowchart
/checklist [category] - Generate a checklist (e.g., /checklist go-bag)
```

## Directory Structure

```
├── CLAUDE.md           # System prompt and workspace configuration
├── input/              # Your intake responses and existing documents
├── output/             # Generated assessments, plans, SOPs, flowcharts
├── agents/             # Agent configurations for specialized tasks
├── rules/              # Workflow rules and subcommand definitions
└── templates/          # Output templates for consistent formatting
```

## Preparedness Domains Covered

- **Physical Safety & Security** - Home security, safe rooms, evacuation
- **Natural Disasters** - Region-specific hazards and response
- **Medical & Health** - First aid, medications, special needs
- **Financial** - Emergency funds, insurance, document protection
- **Food & Water** - Storage, rotation, sustainability
- **Energy & Utilities** - Backup power, alternatives
- **Digital Security** - Data backup, offline access
- **Social & Community** - Communication plans, networks
- **Transportation** - Vehicle prep, go-bags, routes
- **Legal & Administrative** - Documents, directives, insurance

## Philosophy

- **No judgment** - People prepare for different scenarios based on their own experiences
- **Personalized** - Generic advice is less useful than tailored recommendations
- **Actionable** - Every output includes specific, concrete steps
- **Printable** - Critical documents designed for offline use
- **Iterative** - Plans evolve; regular review is built into the system

## Outputs

All generated documents are designed to be:
- Usable under stress (clear, simple language)
- Standalone (no need for additional context)
- Printable (formatted for physical copies)
- Versioned (dated for tracking updates)

## License

Personal use. Adapt freely for your own preparedness planning.
