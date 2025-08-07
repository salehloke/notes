# Homelab Notes Structure for Jira/Confluence Migration

## 📁 Folder Structure

```
homelab-docs/
├── 📋 Issues/                    # For Jira tickets
│   ├── 🔴 Critical/
│   ├── 🟡 High/
│   ├── 🔵 Medium/
│   ├── 🟢 Low/
│   └── ✅ Resolved/
├── 📚 Knowledge-Base/            # For Confluence pages
│   ├── Infrastructure/
│   ├── Procedures/
│   ├── Troubleshooting/
│   └── Reference/
├── 🚀 Projects/                  # For Jira epics
│   ├── Active/
│   ├── Planned/
│   └── Completed/
├── 📝 Daily-Logs/               # Daily work logs
├── 🔧 Templates/                # Reusable templates
└── 📊 Reports/                  # Status reports
```

## 🎫 Issue Template (For Jira Conversion)

### File Naming Convention:
`ISSUE-{YYYYMMDD}-{Priority}-{ShortDescription}.md`

Example: `ISSUE-20250728-HIGH-ProxmoxVMBootFailure.md`

### Issue Template Structure:

```markdown
---
# JIRA MAPPING FIELDS
issue_type: Bug|Task|Story|Epic
priority: Critical|High|Medium|Low
status: Open|In Progress|Resolved|Closed
assignee: your-name
labels: [homelab, proxmox, networking, storage]
components: [Infrastructure, Security, Monitoring]
created: 2025-07-28
updated: 2025-07-28
---

# [ISSUE-001] VM Boot Failure on Proxmox Node

## 📋 Summary
**Brief description for Jira summary field**
VM fails to boot after Proxmox update, stuck at GRUB loader

## 🎯 Issue Type
- [ ] Bug/Problem
- [ ] Feature Request  
- [ ] Task/Improvement
- [ ] Epic/Project

## 🔥 Priority & Severity
**Priority:** High
**Severity:** Service Impacting
**Business Impact:** Lab environment unavailable

## 🏷️ Labels/Tags
`proxmox` `vm-management` `boot-issues` `update-related`

## 📝 Description
### What Happened?
Detailed description of the issue...

### Expected Behavior
What should have happened...

### Actual Behavior  
What actually happened...

## 🔍 Environment Details
- **Affected System:** Proxmox VE 8.1
- **VM ID:** 100, 101, 102
- **Hardware:** Dell R720
- **Network:** VLAN 10
- **Time Discovered:** 2025-07-28 09:30

## 📊 Steps to Reproduce
1. Updated Proxmox VE from 8.0 to 8.1
2. Rebooted the host
3. Attempted to start VMs
4. VMs hang at GRUB prompt

## 🔧 Investigation Notes
### Initial Analysis
- Checked VM configurations - no changes
- Reviewed update logs
- Tested different VMs - same issue

### Logs & Evidence
```bash
# Commands run and output
qm status 100
# Result: stopped

journalctl -u pveproxy | tail -20
# Relevant log entries
```

### Screenshots/Files
- `screenshot-grub-error.png`
- `vm-config-backup.conf`

## ✅ Resolution Steps
### Attempted Fixes
1. **Tried:** Booting with different GRUB options
   - **Result:** No change
   - **Time:** 30 minutes

2. **Tried:** Rolling back VM snapshots
   - **Result:** VMs boot successfully
   - **Time:** 15 minutes

### Final Solution
1. Identified GRUB configuration issue post-update
2. Updated VM boot parameters in Proxmox
3. Modified GRUB_CMDLINE_LINUX in VM templates
4. Tested on all affected VMs

### Resolution Commands
```bash
# Commands that fixed the issue
qm set 100 --boot order=scsi0
qm set 100 --args '-cpu host'
qm start 100
```

## 📈 Impact Assessment
- **Downtime:** 2 hours
- **Affected Services:** All development VMs
- **Users Impacted:** 1 (homelab user)
- **Data Loss:** None

## 🛡️ Prevention Measures
1. **Immediate:**
   - Create VM snapshots before Proxmox updates
   - Document VM configurations

2. **Long-term:**
   - Implement staging environment for updates
   - Automated VM configuration backups
   - Create update runbook

## 🔗 Related Issues
- Links to related problems
- Dependencies
- Follow-up tasks

## 📊 Time Tracking
- **Time to Detect:** 15 minutes
- **Time to Investigate:** 1.5 hours  
- **Time to Resolve:** 30 minutes
- **Total Time:** 2 hours 15 minutes

## 📋 Acceptance Criteria
- [ ] All VMs boot successfully
- [ ] No performance impact
- [ ] Prevention measures documented
- [ ] Knowledge base updated

## 📚 Knowledge Base Links
- [Proxmox Update Procedures](link)
- [VM Troubleshooting Guide](link)
- [GRUB Configuration Reference](link)
```

## 📚 Knowledge Base Template (For Confluence)

### File Naming Convention:
`KB-{Category}-{Topic}.md`

Example: `KB-Infrastructure-ProxmoxVMManagement.md`

### Knowledge Base Structure:

```markdown
---
# CONFLUENCE MAPPING FIELDS
space: Homelab
parent_page: Infrastructure
labels: [proxmox, virtualization, procedures]
created: 2025-07-28
updated: 2025-07-28
reviewed: 2025-07-28
author: your-name
---

# Proxmox VM Management Procedures

## 📋 Page Info
**Last Updated:** 2025-07-28
**Reviewed By:** Your Name
**Next Review:** 2025-08-28

## 🎯 Purpose
This document provides step-by-step procedures for managing VMs in Proxmox VE.

## 👥 Audience
- Homelab administrators
- System engineers
- Support team members

## 📋 Table of Contents
- [VM Creation](#vm-creation)
- [VM Configuration](#vm-configuration)
- [Backup Procedures](#backup-procedures)
- [Troubleshooting](#troubleshooting)

## 🚀 VM Creation

### Prerequisites
- Proxmox VE installed and configured
- ISO images uploaded
- Storage configured
- Network VLANs defined

### Step-by-Step Process

#### 1. Create New VM
```bash
# Web UI Method
1. Login to Proxmox web interface
2. Click "Create VM" button
3. Configure VM parameters

# CLI Method
qm create 100 --name test-vm --memory 2048 --cores 2
```

#### 2. Configure Storage
```bash
qm set 100 --scsi0 local-lvm:32
```

### ⚠️ Important Notes
- Always create snapshots before major changes
- Follow naming conventions: `{environment}-{purpose}-{number}`
- Document VM purposes and dependencies

## 🔧 Troubleshooting

### Common Issues

#### VM Won't Start
**Symptoms:** VM status shows "stopped", won't respond to start command

**Diagnosis Steps:**
1. Check VM configuration
2. Verify storage availability
3. Review system logs

**Solutions:**
```bash
# Check VM status
qm status {vmid}

# Review configuration
qm config {vmid}

# Check logs
journalctl -u pveproxy
```

## 📊 Reference Information

### Useful Commands
| Command | Purpose |
|---------|---------|
| `qm list` | List all VMs |
| `qm start {vmid}` | Start VM |
| `qm stop {vmid}` | Stop VM |
| `qm snapshot {vmid} {name}` | Create snapshot |

### Configuration Files
- VM configs: `/etc/pve/qemu-server/`
- Storage configs: `/etc/pve/storage.cfg`
- Network configs: `/etc/network/interfaces`

## 🔗 Related Documents
- [Proxmox Installation Guide](link)
- [Network Configuration](link)
- [Backup Strategies](link)

## 📝 Change Log
| Date | Author | Changes |
|------|--------|---------|
| 2025-07-28 | Your Name | Initial creation |
| 2025-07-28 | Your Name | Added troubleshooting section |
```

## 🚀 Project Template (For Jira Epics)

### File Naming Convention:
`PROJECT-{YYYYMMDD}-{ProjectName}.md`

Example: `PROJECT-20250728-KubernetesClusterSetup.md`

### Project Structure:

```markdown
---
# JIRA EPIC MAPPING
epic_name: Kubernetes Cluster Implementation
project_key: HOMELAB
components: [Infrastructure, Container Platform]
labels: [kubernetes, cluster, infrastructure]
start_date: 2025-08-01
target_date: 2025-09-15
---

# [EPIC] Kubernetes Cluster Implementation

## 🎯 Epic Summary
Implement a production-ready Kubernetes cluster for containerized workload management

## 📋 Epic Description
### Business Value
- Modernize application deployment
- Improve resource utilization
- Enable auto-scaling capabilities
- Standardize development workflows

### Success Criteria
- [ ] 3-node K8s cluster operational
- [ ] Basic monitoring implemented
- [ ] Sample application deployed
- [ ] Documentation completed

## 📊 Story Breakdown

### Sprint 1: Infrastructure Setup
- [ ] **STORY-001:** Provision VM infrastructure
- [ ] **STORY-002:** Configure networking
- [ ] **STORY-003:** Set up storage classes

### Sprint 2: Kubernetes Installation  
- [ ] **STORY-004:** Install master nodes
- [ ] **STORY-005:** Join worker nodes
- [ ] **STORY-006:** Configure networking plugin

### Sprint 3: Essential Services
- [ ] **STORY-007:** Deploy monitoring stack
- [ ] **STORY-008:** Configure ingress controller
- [ ] **STORY-009:** Set up persistent volumes

### Sprint 4: Testing & Documentation
- [ ] **STORY-010:** Deploy test applications
- [ ] **STORY-011:** Performance testing
- [ ] **STORY-012:** Create operation runbooks

## 📈 Metrics & KPIs
- **Deployment time:** Target < 2 hours
- **Uptime:** Target > 99.5%
- **Resource utilization:** Target 60-80%

## 🔗 Dependencies
- Proxmox cluster operational
- Network VLANs configured
- Storage array available

## 📝 Risks & Mitigation
| Risk | Impact | Probability | Mitigation |
|------|--------|-------------|------------|
| Hardware failure | High | Low | Implement HA configuration |
| Network issues | Medium | Medium | Redundant network paths |

## 📚 Resources
- [Kubernetes Documentation](link)
- [Infrastructure Requirements](link)
- [Network Diagrams](link)
```

## 📝 Daily Log Template

### File Naming Convention:
`DAILY-{YYYY-MM-DD}.md`

Example: `DAILY-2025-07-28.md`

```markdown
# Daily Log - 2025-07-28 (Week 31)

## 🎯 Today's Focus
- [ ] Resolve Proxmox VM boot issues
- [ ] Update network documentation
- [ ] Review security alerts

## 🔧 Issues Worked On

### ISSUE-001: VM Boot Failure
**Time:** 09:00 - 11:30
**Status:** Resolved ✅
**Next Steps:** Update runbook
**Jira Ticket:** HOMELAB-123

### ISSUE-002: Network Latency
**Time:** 14:00 - 15:30  
**Status:** In Progress 🔄
**Next Steps:** Check switch configuration
**Jira Ticket:** HOMELAB-124

## 📚 Knowledge Updates
- Updated VM troubleshooting guide
- Added network topology diagram
- Documented GRUB configuration fix

## 🔄 Tomorrow's Priorities
- [ ] Complete network latency investigation
- [ ] Start Kubernetes planning
- [ ] Review backup procedures

## 📊 Time Tracking
- **Issues:** 3 hours
- **Documentation:** 1 hour
- **Learning:** 30 minutes
- **Planning:** 30 minutes
```

## 🔄 Migration Process to Jira/Confluence

### Automated Migration Script Ideas:

```bash
#!/bin/bash
# migrate-to-jira.sh

# Extract frontmatter fields
issue_type=$(grep "issue_type:" $1 | cut -d' ' -f2)
priority=$(grep "priority:" $1 | cut -d' ' -f2)
summary=$(grep "^# " $1 | head -1 | sed 's/^# //')

# Create Jira ticket via API
curl -X POST \
  -H "Content-Type: application/json" \
  -d '{
    "fields": {
      "project": {"key": "HOMELAB"},
      "summary": "'$summary'",
      "issuetype": {"name": "'$issue_type'"},
      "priority": {"name": "'$priority'"}
    }
  }' \
  https://your-jira.atlassian.net/rest/api/2/issue/
```

### Migration Checklist:
- [ ] Set up Jira project structure
- [ ] Configure Confluence spaces
- [ ] Create custom fields mapping
- [ ] Test migration scripts
- [ ] Train team on new structure
- [ ] Migrate historical data
- [ ] Update templates for direct creation

This structure ensures your notes are Jira/Confluence ready from day one, with clear separation between operational issues (Jira) and knowledge documentation (Confluence).