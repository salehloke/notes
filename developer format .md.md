
# Developer Work Organization System

## Work Structure in Obsidian

### Folder Organization

```
📁 30-AREAS/
└── Work/
    ├── Active Tickets/
    ├── Sprint Notes/
    ├── Module Notes/
    │   ├── DLSM/
    │   ├── CDH/
    │   └── Enjoy Rewards/
    └── Work Dashboard.md
```

## Ticket Naming Convention

### Format: `[MODULE] TICKET-ID - Brief Description`

**Examples:**

- `[DLSM] PROJ-1234 - Fix login validation bug`
- `[CDH] PROJ-5678 - Add customer search API`
- `[ENJOY] PROJ-9012 - Update rewards calculation`
- `[DLSM] BAU-3456 - Weekly database cleanup`

### Why This Format:

- **[MODULE]** - Instant visual grouping
- **TICKET-ID** - Direct Jira reference
- **Brief Description** - Context without opening

## Ticket Note Template

### Template: Work Ticket

```markdown
---
created: {{date:YYYY-MM-DD}}
tags: [work, ticket, MODULE_TAG]
ticket: TICKET-ID
module: MODULE_NAME
priority: medium
status: in-progress
sprint: Sprint-XX
---

# [MODULE] TICKET-ID - Brief Description

## Ticket Info
- **Jira:** [TICKET-ID](jira-link-here)
- **Module:** MODULE_NAME
- **Type:** Feature/Bug/BAU
- **Priority:** High/Medium/Low
- **Sprint:** Sprint-XX

## Task Breakdown
- [ ] Analyze requirements
- [ ] Code changes
- [ ] Testing
- [ ] Code review
- [ ] Deploy

## Notes & Progress


## Blockers/Issues


## Related
- Links to other tickets
- Related documentation

---
*Started: {{date:YYYY-MM-DD}}*
```

## Module Tags for Easy Filtering

- `#dlsm` - Drive Less Save More
- `#cdh` - Customer Data Hub
- `#enjoy` - Enjoy Rewards
- `#bau` - Business As Usual
- `#feature` - New feature work
- `#bug` - Bug fixes
- `#sprint-current` - Current sprint items

## Work Dashboard Query

### Main Work View

```dataview
TABLE WITHOUT ID
link(file.link, file.name) as "Ticket",
priority,
status,
sprint,
module
FROM #work AND #ticket
WHERE status != "done"
SORT priority desc, file.ctime asc
```

### By Module Views

```dataview
TABLE WITHOUT ID
link(file.link, file.name) as "DLSM Tickets",
priority,
status,
sprint
FROM #work AND #dlsm
WHERE status != "done"
SORT priority desc
```

## Daily Work Workflow

### Morning Setup (5 minutes)

1. **Open Work Dashboard** - See all active tickets
2. **Check Sprint Board** - Any new assignments?
3. **Review Yesterday's Progress** - Update ticket statuses
4. **Set Today's Focus** - Pick 2-3 main tickets to work on

### During Work

- **Quick Updates** - Update ticket status as you progress
- **Capture Notes** - Technical decisions, solutions, blockers
- **Link Related Work** - Connect tickets that impact each other

### End of Day (5 minutes)

1. **Update Ticket Status** - Reflect current progress
2. **Log Blockers** - Note what's preventing progress
3. **Plan Tomorrow** - What tickets to tackle next
4. **Update Jira** - Sync status back to Jira if needed

## Sprint Management

### Sprint Note Template

```markdown
---
tags: [work, sprint]
sprint: Sprint-XX
start: YYYY-MM-DD
end: YYYY-MM-DD
---

# Sprint XX - [Sprint Goal]

## Sprint Tickets
- [ ] [[DLSM] PROJ-1234 - Fix login bug]
- [ ] [[CDH] PROJ-5678 - Add search API]
- [ ] [[ENJOY] PROJ-9012 - Update rewards]

## Daily Progress
### Monday
- Completed: 
- In Progress: 
- Blockers: 

### Tuesday
- Completed: 
- In Progress: 
- Blockers: 

## Retrospective Notes
### What Went Well
- 

### What Could Improve
- 

### Action Items
- 
```

## Quick Capture for Work Items

### Mobile/Desk Capture Format

```markdown
---
tags: [work, inbox]
---

# Work Item - Brief description

**Module:** DLSM/CDH/ENJOY
**Type:** Bug/Feature/BAU/Question
**Context:** 

**Details:**


---
*Process into proper ticket later*
```

## Module-Specific Notes

### Keep Running Notes for Each Module

- **Technical decisions** - Why certain approaches were chosen
- **Architecture notes** - How systems connect
- **Common issues** - Recurring problems and solutions
- **Deployment notes** - Release procedures, environments
- **Team contacts** - Who to reach for specific areas

## BAU (Business As Usual) Tracking

### For Regular DLSM Maintenance

```markdown
---
tags: [work, bau, dlsm]
type: maintenance
---

# [DLSM] BAU - Weekly database cleanup

## Recurring Task Details
- **Frequency:** Weekly
- **Day:** Every Monday
- **Time Estimate:** 30 minutes

## Checklist
- [ ] Run cleanup scripts
- [ ] Check error logs
- [ ] Verify data integrity
- [ ] Update documentation

## Notes
- Last run: [date]
- Issues found: 
- Next scheduled: [date]
```

## Pro Tips for Developer Workflow

### Linking Strategy

- Link tickets to module overview: `[[DLSM Module Overview]]`
- Reference related tickets: `Related to [[PROJ-1234]]`
- Link to technical documentation: `See [[API Documentation]]`

### Status Updates

- Use consistent status tags: `#todo` `#in-progress` `#review` `#testing` `#done`
- Quick status changes via tag updates
- Filter dashboard by status for different views

### Code Notes

- Capture technical decisions in ticket notes
- Link to specific code files/branches when relevant
- Note complex logic for future reference

### Search Efficiency

- Search by ticket ID: `PROJ-1234`
- Search by module: `tag:#dlsm`
- Search by sprint: `sprint:"Sprint-15"`
- Search by status: `tag:#in-progress`

---

_This system balances detailed tracking with low friction - capture what you need, when you need it, without slowing down your development work._