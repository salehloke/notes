
# Quick Capture Guide & Templates

_For rapid capture of work items across DLSM, CDH, and Enjoy Rewards modules_

## Core Principle

**Capture first, organize later.** Speed beats perfection when things are happening fast.

## Quick Capture Decision Tree

```
Something comes up → Quick Capture Template → Add to Inbox → Process later
```

**When to use Quick Capture:**

- During meetings (DSU, PO discussions, manager requests)
- Interruptions and impromptu discussions
- Mobile captures on the go
- Ideas that pop up while coding
- Bug reports or issues discovered
- Action items from team discussions

## Universal Quick Capture Template

### File Location: `01-INBOX/Quick Captures/`

### File Name: `TYPE MODULE - Brief description - YYMMDD-HHMM`

**Examples:**

- `Task DLSM - Fix AI model timeout - 240807-1145`
- `Meeting CDH - Manager requirement change - 240807-1100`
- `Bug ENJOY - Points calculation error - 240807-1430`
- `Idea DLSM - Cache optimization approach - 240807-0915`

## Quick Capture Templates

### 1. Universal Template (Most Common)

```markdown
---
created: {{date:YYYY-MM-DD HH:mm}}
tags: [inbox, MODULE_TAG]
type: TYPE
priority: tbd
---

# TYPE MODULE - Brief description

**Context:** Where/how this came up

**Details:**
[Capture everything here - don't worry about formatting]

**Action Needed:**
[What needs to happen next]

**Related:**
- Existing tickets: 
- People involved: 
- Deadline/urgency: 

---
*Process this later into proper ticket/task*
```

### 2. Meeting Interruption Template

```markdown
---
created: {{date:YYYY-MM-DD HH:mm}}
tags: [inbox, meeting, MODULE_TAG]
type: meeting
---

# Meeting MODULE - Who - {{date:HH:mm}}

**Who:** [Person/Role]
**Context:** [Why the meeting/interruption]
**Duration:** [Estimated time]

**Key Points:**
- 
- 
- 

**Decisions Made:**
- 
- 

**New Work Items:**
- [ ] 
- [ ] 

**Existing Work Changes:**
- [[Ticket Name]] - [What changed]
- [[Ticket Name]] - [What changed]

**Follow-up Needed:**
- [ ] 
- [ ] 

---
*Process: Create tickets + update existing work*
```

### 3. Bug/Issue Template

```markdown
---
created: {{date:YYYY-MM-DD HH:mm}}
tags: [inbox, bug, MODULE_TAG]
type: bug
priority: tbd
---

# Bug MODULE - Brief description

**Discovered:** [How/where you found it]
**Environment:** [Prod/Staging/Dev]
**Module:** [DLSM/CDH/ENJOY]

**What's happening:**
[Quick description of the issue]

**Expected vs Actual:**
- Expected: 
- Actual: 

**Impact:**
[Who/what is affected]

**Reproduction:**
[Quick steps if known]

**Immediate action:**
[Any quick fixes needed]

---
*Process: Create bug ticket + assess priority*
```

### 4. Requirement Change Template

```markdown
---
created: {{date:YYYY-MM-DD HH:mm}}
tags: [inbox, requirement, MODULE_TAG]
type: requirement-change
---

# Requirement MODULE - Brief change

**Source:** [Who requested the change]
**Affected Ticket:** [[Existing ticket if any]]
**Timeline pressure:** [Urgent/Normal/Future]

**Original Requirement:**
[What was originally planned]

**New/Changed Requirement:**
[What they want now]

**Impact Assessment Needed:**
- [ ] Effort estimate
- [ ] Timeline impact  
- [ ] Technical feasibility
- [ ] Dependencies affected

**Initial Thoughts:**
[Quick gut reaction - easy/hard/complex?]

---
*Process: Analyze impact + update tickets + communicate timeline*
```

### 5. Mobile Quick Capture

```markdown
---
created: {{date:YYYY-MM-DD HH:mm}}
tags: [inbox, mobile]
---

# {{title}}

**Module:** DLSM/CDH/ENJOY
**Type:** Task/Bug/Idea/Meeting

**Quick note:**
[Voice-to-text or quick typing]

---
*Expand this when back at desk*
```

### 6. Code Discovery Template

```markdown
---
created: {{date:YYYY-MM-DD HH:mm}}
tags: [inbox, technical, MODULE_TAG]
type: technical
---

# Tech MODULE - What you discovered

**While working on:** [[Current ticket]]
**Location:** [File/function/component]

**Discovery:**
[What you found - issue, improvement opportunity, etc.]

**Potential Impact:**
[Performance, security, maintainability, etc.]

**Action Options:**
- [ ] Fix now (if small)
- [ ] Create separate ticket
- [ ] Document for later
- [ ] Discuss with team

**Effort Estimate:**
[Quick gut feeling]

---
*Process: Decide immediate vs future action*
```

## Module-Specific Quick Tags

### DLSM Tags

- `#dlsm` - Drive Less Save More
- `#ai-model` - AI/ML related
- `#bau` - Business as usual maintenance
- `#performance` - Performance issues
- `#data-pipeline` - Data processing

### CDH Tags

- `#cdh` - Customer Data Hub
- `#api` - API related
- `#database` - Database changes
- `#integration` - Third-party integrations
- `#search` - Search functionality

### Enjoy Rewards Tags

- `#enjoy` - Enjoy Rewards
- `#rewards` - Rewards calculation
- `#points` - Points system
- `#notifications` - Email/push notifications
- `#dashboard` - User dashboard

### Universal Tags

- `#urgent` - Needs immediate attention
- `#bug` - Bug or issue
- `#feature` - New feature work
- `#meeting` - Meeting related
- `#requirement` - Requirement change
- `#technical` - Technical discovery/debt

## Quick Capture Workflow

### 1. During Interruptions (30 seconds)

```
1. Open Obsidian (mobile/desktop)
2. Create new note in 01-INBOX/Quick Captures/
3. Use appropriate template
4. Capture core info - don't perfect it
5. Tag with module + type
6. Get back to current work
```

### 2. Mobile Captures (15 seconds)

```
1. Obsidian mobile app
2. Voice-to-text or quick type
3. Minimal tags: #inbox #module
4. Process properly later at desk
```

### 3. Between Tasks (1 minute)

```
1. Something comes up while coding
2. Quick technical template
3. Don't lose your current context
4. Mark for processing later
```

## Processing Quick Captures (Daily 10-15 minutes)

### End of Day Processing Queue:

1. **Open `01-INBOX/Quick Captures/`**
    
2. **For each capture:**
    
    - Is it a new ticket? → Create in appropriate module folder
    - Does it change existing work? → Update existing tickets
    - Is it just information? → Move to knowledge base
    - Is it a follow-up action? → Add to task list
3. **Clean up:**
    
    - Move processed items to appropriate folders
    - Update work dashboard
    - Clear inbox for tomorrow

### Processing Decision Matrix:

```
Actionable? → YES → Single task? → YES → Create task
                                → NO → Create project
           → NO → Reference? → YES → Move to knowledge
                             → NO → Archive or delete
```

## QuickAdd Setup (Optional Enhancement)

### If you install QuickAdd plugin:

**Create macros for one-click capture:**

- `Ctrl+Shift+D` → DLSM quick capture
- `Ctrl+Shift+C` → CDH quick capture
- `Ctrl+Shift+E` → Enjoy quick capture
- `Ctrl+Shift+M` → Meeting capture
- `Ctrl+Shift+B` → Bug capture

## Mobile Efficiency Tips

### Voice Capture Strategy:

1. **Use voice-to-text** for speed
2. **Start with module name** - "DLSM bug in login"
3. **Include urgency** - "CDH urgent manager request"
4. **Don't worry about formatting** - process later

### One-Tap Templates:

- Set up Obsidian mobile widgets for instant capture
- Use consistent naming so you can find things later
- Sync frequently to avoid losing captures

## Pro Tips for Effective Quick Capture

### Do:

- ✅ Capture immediately when something comes up
- ✅ Use consistent naming and tagging
- ✅ Include enough context to remember later
- ✅ Note the source (who/where it came from)
- ✅ Mark urgency and deadlines
- ✅ Process regularly (daily/twice daily)

### Don't:

- ❌ Try to perfect the formatting during capture
- ❌ Spend time organizing while capturing
- ❌ Skip capturing because "I'll remember"
- ❌ Let the inbox pile up without processing
- ❌ Capture without any tags or context

## Example: Busy Day Capture Sequence

**9:30 AM DSU:** Normal meeting notes in proper location **10:15 AM Enjoy PO:** Quick capture → process later **11:00 AM CDH Manager:** Quick capture → process immediately (urgent) **2:30 PM Code Discovery:** Technical template → process end of day **4:45 PM DLSM Bug Report:** Bug template → create ticket immediately

**End of Day:** Process remaining inbox items, update work dashboard

---

_Remember: The goal is to never lose information, not to have perfect organization during chaotic days. Capture everything, organize when you have time._