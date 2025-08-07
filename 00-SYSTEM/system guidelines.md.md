# Obsidian System Guidelines

_Personal reference for my unified tracking system_

## Core Philosophy

One system to capture, organize, and retrieve everything. Every item gets processed and has a clear place.

## Folder Structure & Logic

### 00-SYSTEM/

**Purpose:** Behind-the-scenes files that keep the system running

- **Templates/** - Note templates for consistent formatting
- **Dashboards/** - Overview pages and dynamic queries
- **Archives/** - Old system files and completed projects

### 01-INBOX/

**Purpose:** Universal entry point - everything starts here before being sorted

- **Quick Captures/** - Rapid mobile captures, voice notes, fleeting thoughts
- **To Process/** - Items that need more thoughtful categorization

### 10-ACTIVE/

**Purpose:** Current work - things I'm actively progressing RIGHT NOW

- **Tasks/** - Individual actionable items I'm doing
- **Projects/** - Multi-step endeavors I'm actively working on
- **Daily Notes/** - Today's focus, captures, and reflections

### 20-KNOWLEDGE/

**Purpose:** Information to reference and learn from (not actionable, but valuable)

- **Notes/** - My own thoughts, learnings, and insights
- **Reference/** - Facts, procedures, how-to guides, documentation
- **Resources/** - Links, tools, external materials, bookmarks

### 30-AREAS/

**Purpose:** Life domains with ongoing responsibility (no end date, unlike projects)

- **Work/** - Job responsibilities, career development
- **Personal/** - Home, family, personal administration
- **Learning/** - Skills development, education, courses
- **Health/** - Fitness, medical, wellbeing tracking

## Naming Conventions

### For Inbox Items

**Format:** `Type - Brief Description - YYMMDD`

**Examples:**

- `Task - Call dentist for appointment - 240807`
- `Note - Python tutorial ideas - 240807`
- `Idea - Weekend trip to mountains - 240807`
- `Project - Home office renovation - 240807`
- `Resource - Article about productivity - 240807`

### Why This Format Works:

- **Type** - Immediate visual identification
- **Brief Description** - Clear content summary
- **Date** - Chronological sorting and context
- **Consistent** - Easy scanning and processing

## Note Structure Template

### Basic Inbox Item Format:

```markdown
---
created: 2024-08-07 14:30
tags: [inbox]
type: task
---

# Task - Call dentist for appointment - 240807

**Quick Details:**
- Need to schedule cleaning
- Prefer morning appointments
- Insurance info: Blue Cross

**Next Action:**
Call during lunch break

---
*Process this later*
```

### Key Elements:

1. **Frontmatter** - Metadata with creation date and tags
2. **Clear Title** - Matches filename for consistency
3. **Quick Details** - Essential context and information
4. **Next Action** - For tasks, what's the immediate step?
5. **Process Marker** - Reminder to sort later

## Tag System Philosophy

### Priority Tags

- `#urgent` - Needs immediate attention (same day)
- `#high` - Important, do soon (this week)
- `#medium` - Normal priority (within 2 weeks)
- `#low` - Nice to do when time allows

### Status Tags

- `#active` - Currently working on
- `#waiting` - Blocked, waiting for external input
- `#review` - Needs review or decision
- `#someday` - Future consideration

### Type Tags

- `#task` - Actionable item with clear next step
- `#project` - Multi-step endeavor
- `#note` - Knowledge, thoughts, insights
- `#idea` - Creative thoughts, brainstorming
- `#resource` - Tools, links, references

### Context Tags

- `#work` - Job and career related
- `#personal` - Personal life and home
- `#health` - Health, fitness, medical
- `#learning` - Education and skill building

## Processing Workflow

### Daily Inbox Processing (5-10 minutes)

1. **Review Quick Captures** - Sort mobile/rapid entries
2. **Categorize by Type** - Task, Note, Project, Idea, Resource
3. **Add Context Tags** - Work, personal, health, learning
4. **Set Priority** - Urgent, high, medium, low
5. **Move to Appropriate Folder** - Active, Knowledge, or Areas
6. **Link Related Items** - Connect to existing notes/projects

### Decision Tree for Processing:

```
Is it actionable?
├─ YES → Is it a single action?
│   ├─ YES → Move to 10-ACTIVE/Tasks/
│   └─ NO → Move to 10-ACTIVE/Projects/
└─ NO → Is it reference information?
    ├─ YES → Move to 20-KNOWLEDGE/
    └─ NO → Is it area-specific?
        ├─ YES → Move to 30-AREAS/[category]/
        └─ NO → Consider if needed, archive or delete
```

## Mobile Workflow Guidelines

### Quick Capture Best Practices:

- **Speed over perfection** - Capture first, organize later
- **Use voice-to-text** when possible
- **Minimal formatting** - Just get the idea down
- **One idea per note** - Easier to process later
- **Add basic tags** - #inbox at minimum

### Mobile Review:

- Check daily note for focus
- Review urgent/high priority items
- Mark completed tasks
- Quick capture of new thoughts

## System Maintenance

### Daily (5 minutes)

- Process inbox items
- Update task statuses
- Check overdue items
- Plan tomorrow's priorities

### Weekly (20 minutes)

- Archive completed projects
- Review someday/maybe items
- Clean up tags and links
- Backup system

### Monthly (30 minutes)

- Review system effectiveness
- Update folder structure if needed
- Archive old daily notes
- Celebrate progress and learnings

## Getting Started Checklist

### Phase 1: Foundation (Week 1)

- [ ] Create folder structure
- [ ] Install core plugins (Tasks, Templater, QuickAdd)
- [ ] Set up basic capture template
- [ ] Practice daily inbox processing

### Phase 2: Habits (Week 2)

- [ ] Establish morning planning routine
- [ ] Consistent inbox processing
- [ ] Evening review and tomorrow's prep
- [ ] First weekly review

### Phase 3: Optimization (Week 3+)

- [ ] Refine tag system based on usage
- [ ] Create custom dashboards
- [ ] Link related items systematically
- [ ] Fine-tune templates and workflow

## Key Principles to Remember

1. **Everything Goes Through Inbox First** - No exceptions
2. **Process Don't Perfect** - Regular processing beats perfect organization
3. **Link Liberally** - Connections make knowledge valuable
4. **Trust the System** - If it's captured, it's findable
5. **Iterate and Improve** - System evolves with usage
6. **Mobile-Friendly** - Must work on phone for real-world use
7. **One Source of Truth** - Don't duplicate systems

---

_Last Updated: August 7, 2024_ _System Status: Initial Setup_