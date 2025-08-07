
# Inbox Processing Guide - From Capture to Action

_How to efficiently process captured items from your inbox into actionable work_

## Overview

Processing is the critical step between **capture** (getting things into your inbox) and **action** (actually working on organized tasks). This guide shows you how to turn messy inbox notes into clean, actionable items.

## When to Process

### Daily Processing (Recommended)

- **End of workday:** 10-15 minutes
- **Morning start:** 5 minutes quick review
- **Between major tasks:** When switching context

### Trigger-Based Processing

- **Inbox has 5+ items** - Time to process
- **Before weekly planning** - Clean slate for planning
- **After intense meeting days** - Multiple captures need sorting

## The 4-Question Processing Framework

For every item in your inbox, ask these questions in order:

### 1. What actions does this create?

- Single tasks → `10-ACTIVE/Tasks/`
- Multi-step work → `10-ACTIVE/Projects/`
- Work tickets → `30-AREAS/Work/Active Tickets/`

### 2. What knowledge should I save?

- Technical decisions → `20-KNOWLEDGE/Notes/`
- Reference materials → `20-KNOWLEDGE/Reference/`
- Useful resources → `20-KNOWLEDGE/Resources/`

### 3. What existing work does this affect?

- Update existing tickets with new requirements
- Adjust project timelines and scope
- Note dependencies between items

### 4. Where should this note live long-term?

- Meeting records → `30-AREAS/Work/Meetings/`
- Module documentation → `30-AREAS/Work/Module Notes/`
- Personal reference → `30-AREAS/[relevant area]/`

## Step-by-Step Processing Workflow

### Step 1: Open Inbox Item (30 seconds)

- Read through the entire note
- Identify the type of content
- Note any urgency indicators

### Step 2: Extract Actions (2-3 minutes)

Mark actionable items in the note:

```markdown
## Actions Identified:
✅ New Tasks to Create:
- [ ] Specific actionable item 1
- [ ] Specific actionable item 2

✅ Knowledge to Capture:  
- Technical decision and reasoning
- Important reference information

✅ Existing Work to Update:
- Update PROJ-1234 scope
- Adjust timeline for PROJ-5678
```

### Step 3: Create New Items (3-5 minutes)

**For each new action:**

1. Create appropriately named file in correct location
2. Use relevant template
3. Add proper tags and metadata
4. Set priority and due dates if applicable

### Step 4: Update Existing Work (1-2 minutes)

**For affected existing items:**

1. Open existing tickets/projects
2. Add reference to the discussion/decision
3. Update scope, timeline, or requirements
4. Note any new dependencies

### Step 5: Capture Knowledge (2-3 minutes)

**For valuable information:**

1. Create or update reference documents
2. Link to related work items
3. Tag appropriately for future discovery

### Step 6: Link Everything (1 minute)

- Link new tasks to original discussion
- Cross-reference related items
- Ensure discoverability

### Step 7: Archive Original (30 seconds)

- Move processed note to appropriate long-term location
- Remove from inbox
- Clear for next processing session

## Processing Examples

### Example 1: CDH Team Discussion

**Inbox Item:** `Meeting CDH - Technical architecture discussion - 240807.md`

**Processing Result:**

```
New Tasks Created:
→ CDH PROJ-7890 - Research API versioning best practices.md
→ CDH PROJ-7891 - Design microservices architecture.md  
→ CDH PROJ-7892 - Refactor user authentication.md

Knowledge Captured:
→ CDH API Versioning Strategy - Team Decision Aug 2024.md
→ CDH Microservices Architecture Notes.md

Existing Work Updated:
→ CDH PROJ-5678 - Customer search API.md (scope expanded)

Original Note Moved To:
→ 30-AREAS/Work/Meetings/CDH Team Discussion - Technical architecture - 240807.md
```

### Example 2: Bug Discovery While Coding

**Inbox Item:** `Bug DLSM - Memory leak in AI model inference - 240807.md`

**Processing Result:**

```
New Task Created:
```