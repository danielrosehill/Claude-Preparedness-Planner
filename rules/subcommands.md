# Subcommand Definitions

This document defines the slash commands available in the Preparedness Planner workspace.

## Command Reference

### `/intake`

**Purpose**: Begin or continue the intake interview process

**Behavior**:
1. Check if `input/intake-responses.md` exists
   - If exists: Ask if user wants to review/update or start fresh
   - If not: Begin new intake interview
2. Load the intake-agent.md agent configuration
3. Conduct conversational interview through all sections
4. Save responses to `input/intake-responses.md`
5. Prompt user to proceed with `/assess`

**Arguments**: None

**Output**: `input/intake-responses.md`

---

### `/assess`

**Purpose**: Generate risk assessment based on intake data

**Behavior**:
1. Verify `input/intake-responses.md` exists
   - If not: Prompt to run `/intake` first
2. Load assessment-agent.md configuration
3. Analyze intake data against risk framework
4. Generate comprehensive risk assessment
5. Save to `output/risk-assessment-[YYYY-MM-DD].md`
6. Display summary and prompt for `/plan`

**Arguments**: None

**Prerequisites**: Completed intake (`/intake`)

**Output**: `output/risk-assessment-[date].md`

---

### `/plan`

**Purpose**: Generate prioritized action plan

**Behavior**:
1. Verify risk assessment exists
   - If not: Prompt to run `/assess` first
2. Load action-planner.md configuration
3. Transform risks and gaps into actionable plan
4. Include budget estimates and timelines
5. Save to `output/action-plan-[YYYY-MM-DD].md`

**Arguments**:
- `[budget]` (optional): Maximum budget constraint (e.g., `/plan $500`)
- `[timeframe]` (optional): Target completion (e.g., `/plan 3months`)

**Prerequisites**: Completed assessment (`/assess`)

**Output**: `output/action-plan-[date].md`

---

### `/sop [scenario]`

**Purpose**: Generate Standard Operating Procedure for specific scenario

**Behavior**:
1. Load sop-generator.md configuration
2. If intake exists, personalize to user's situation
3. Generate comprehensive SOP for scenario
4. Save to `output/sop-[scenario]-[YYYY-MM-DD].md`

**Arguments**:
- `[scenario]` (required): The scenario to create SOP for

**Common Scenarios**:
- `evacuation` - Emergency evacuation procedure
- `shelter-in-place` - Sheltering procedures
- `power-outage` - Extended power failure response
- `medical-emergency` - Medical emergency response
- `home-intrusion` - Security incident response
- `fire` - House fire response
- `earthquake` - Earthquake response
- `severe-weather` - Storm/severe weather response
- `water-outage` - Water service failure
- `financial-emergency` - Sudden financial crisis

**Output**: `output/sop-[scenario]-[date].md`

---

### `/flowchart [scenario]`

**Purpose**: Generate decision flowchart for specific scenario

**Behavior**:
1. Load flowchart-generator.md configuration
2. Create Mermaid-format decision tree
3. Include criteria definitions
4. Save to `output/flowchart-[scenario]-[YYYY-MM-DD].md`

**Arguments**:
- `[scenario]` (required): The scenario to create flowchart for

**Output**: `output/flowchart-[scenario]-[date].md`

---

### `/checklist [category]`

**Purpose**: Generate itemized checklist for a preparedness category

**Behavior**:
1. Generate comprehensive checklist
2. Include quantities and specifications
3. Add sourcing suggestions
4. Save to `output/checklist-[category]-[YYYY-MM-DD].md`

**Arguments**:
- `[category]` (required): Category to generate checklist for

**Categories**:
- `go-bag` - Emergency go-bag contents
- `car-kit` - Vehicle emergency kit
- `first-aid` - Medical supplies
- `food` - Food storage checklist
- `water` - Water storage and purification
- `documents` - Critical documents
- `communications` - Communication equipment
- `tools` - Essential tools
- `shelter` - Shelter-in-place supplies
- `power` - Backup power equipment
- `sanitation` - Hygiene and sanitation
- `custom` - Custom category (will prompt for details)

**Output**: `output/checklist-[category]-[date].md`

---

### `/review`

**Purpose**: Review and update existing preparedness documents

**Behavior**:
1. List all existing outputs with dates
2. Identify documents past review date
3. Prompt for specific document to review
4. Walk through document section by section
5. Generate updated version with revision notes

**Arguments**:
- `[document]` (optional): Specific document to review

**Output**: Updated document with incremented version

---

### `/quick [scenario]`

**Purpose**: Generate quick reference card for a scenario

**Behavior**:
1. Create condensed, single-page reference
2. Focus on immediate actions only
3. Optimized for printing on index card or single sheet
4. Save to `output/quick-ref-[scenario]-[YYYY-MM-DD].md`

**Arguments**:
- `[scenario]` (required): The scenario for quick reference

**Output**: `output/quick-ref-[scenario]-[date].md`

---

### `/status`

**Purpose**: Display current preparedness planning status

**Behavior**:
1. Check for existing intake, assessment, plan
2. List all generated documents
3. Show upcoming review dates
4. Summarize progress against plan
5. Suggest next actions

**Arguments**: None

**Output**: Status display (no file created)

---

### `/drill [scenario]`

**Purpose**: Walk through a drill for a specific scenario

**Behavior**:
1. Load relevant SOP if exists
2. Conduct tabletop walkthrough
3. Identify gaps or issues discovered
4. Log drill completion
5. Update drill dates in relevant SOPs

**Arguments**:
- `[scenario]` (required): The scenario to drill

**Output**: `output/drill-log-[date].md`

---

## Command Chaining

Commands can be run in sequence for full workflow:

```
/intake → /assess → /plan → /sop [various] → /checklist [various]
```

## Error Handling

If a command cannot complete:
1. Explain what's missing
2. Suggest the prerequisite command
3. Offer to run the prerequisite automatically
