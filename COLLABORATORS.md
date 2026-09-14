# Collaborators & Team Permissions

This document outlines the permission levels and team structure for the APACGA EARTH project.

## Permission Levels

### **Write** (Push enabled) ✍️
Permission for README and code contributions.

**Capabilities:**
- Push to branches
- Create and review pull requests
- Comment on issues and discussions
- Create and manage issues
- Participate in project discussions

**Does NOT include:**
- Issue/PR triage management
- Branch protection rules
- Repository settings management
- Webhook or deploy key management

**Typical roles:** Team members, contributors, documentation writers

---

### **Triage** 🏷️
Permission for issue and pull request management.

**Capabilities:**
- All "Write" permissions, PLUS:
- Manage issue labels, milestones, and priorities
- Close and reopen issues and pull requests
- Lock discussions and conversations
- Assign issues to team members
- Mark issues as duplicates
- Filter and organize project board columns

**Does NOT include:**
- Branch protection rules
- Repository settings management
- Webhook or deploy key management
- Merge pull requests

**Typical roles:** Working group leads (for organizing team work), project coordinators

---

### **Maintain** 🔧
Permission for broader repository maintenance and team oversight.

**Capabilities:**
- All "Write" and "Triage" permissions, PLUS:
- Manage branch protection rules
- Manage team access and collaborator permissions
- Update repository settings (description, topics, visibility)
- Manage branch deletion and merging policies
- Create and manage webhooks
- Manage deploy keys
- Edit GitHub Pages settings
- Manage pull request merge options

**Does NOT include:**
- Delete repository
- Change organization access policies
- Transfer repository ownership
- View organization secrets

**Typical roles:** Technical leads, governance leads, senior maintainers

---

### **SuperAdmin** 👑
Full repository control and organization management.

**Capabilities:**
- All "Write", "Triage", and "Maintain" permissions, PLUS:
- Delete or archive the repository
- Transfer repository ownership
- Manage organization-level settings
- Manage organization secrets and variables
- Create and manage GitHub Apps
- Audit logs and security settings

**Does NOT include:**
- Organization account deletion (owner-level only)

**Typical roles:** Project steward, organization owner, executive leadership

---

## Permission Comparison Table

| Capability | Write | Triage | Maintain | SuperAdmin |
|------------|:-----:|:------:|:--------:|:----------:|
| Push commits | ✅ | ✅ | ✅ | ✅ |
| Create/review PRs | ✅ | ✅ | ✅ | ✅ |
| Comment on issues | ✅ | ✅ | ✅ | ✅ |
| Manage issue labels/milestones | ❌ | ✅ | ✅ | ✅ |
| Close/reopen issues | ❌ | ✅ | ✅ | ✅ |
| Lock conversations | ❌ | ✅ | ✅ | ✅ |
| Manage branch protection | ❌ | ❌ | ✅ | ✅ |
| Manage collaborators | ❌ | ❌ | ✅ | ✅ |
| Update repository settings | ❌ | ❌ | ✅ | ✅ |
| Manage webhooks | ❌ | ❌ | ✅ | ✅ |
| Delete repository | ❌ | ❌ | ❌ | ✅ |
| Transfer repository | ❌ | ❌ | ❌ | ✅ |

---

## Working Group Structure

| Working Group | Lead Role | Permission | Team Members | Notes |
|---------------|-----------|-----------|--------------|-------|
| **Architecture & Infrastructure** | Lead | Maintain | Multiple | Oversees system design, APIs, security controls |
| **Governance & Compliance** | Lead | Maintain | Multiple | Manages decision-making processes, regulatory guidance |
| **Digital Identity** | Lead | Maintain | Multiple | Manages verifiable credentials, DIDs, trust frameworks |
| **Financial Sandbox** | Lead | Maintain | Multiple | Manages payment rails, token models, compliance testing |
| **AI, Data & Digital Twin** | Lead | Maintain | Multiple | Manages model lifecycle, responsible AI practices |
| **Knowledge & Documentation** | Lead | Maintain | Multiple | Curates technical references, whitepapers, volumes |

**Working group leads** receive **Maintain** permission for full team oversight.

**Team members** within each group: **Write** permission for contributions.

**Coordinators** (optional): **Triage** permission for organizing work and managing priorities.

---

## How to Add Collaborators

### Via GitHub UI:
1. Go to **Settings** → **Collaborators and teams**
2. Click **Add people** or **Create a team**
3. Search for GitHub username
4. Select appropriate role:
   - **Write** – for team members (push code)
   - **Triage** – for coordinators (manage issues/PRs)
   - **Maintain** – for team leads (manage branches & team)
   - **SuperAdmin** – for stewards only (full control)
5. Send invitation

### Via GitHub CLI:
```bash
# Add collaborator with Write permission
gh repo collaborator add <username> --permission pull

# Add collaborator with Triage permission
gh repo collaborator add <username> --permission triage

# Add collaborator with Maintain permission
gh repo collaborator add <username> --permission maintain

# Add collaborator with SuperAdmin permission
gh repo collaborator add <username> --permission admin
```

### Via GitHub API:
```bash
# Add with Write permission
curl -X PUT https://api.github.com/repos/amatcire-org/apacga-earth/collaborators/<username> \
  -H "Authorization: token <TOKEN>" \
  -d '{"permission":"pull"}'

# Add with Triage permission
curl -X PUT https://api.github.com/repos/amatcire-org/apacga-earth/collaborators/<username> \
  -H "Authorization: token <TOKEN>" \
  -d '{"permission":"triage"}'

# Add with Maintain permission
curl -X PUT https://api.github.com/repos/amatcire-org/apacga-earth/collaborators/<username> \
  -H "Authorization: token <TOKEN>" \
  -d '{"permission":"maintain"}'

# Add with SuperAdmin permission
curl -X PUT https://api.github.com/repos/amatcire-org/apacga-earth/collaborators/<username> \
  -H "Authorization: token <TOKEN>" \
  -d '{"permission":"admin"}'
```

---

## Team Management Best Practices

1. **Assign team leads** with **Maintain** permission to manage their working group
2. **Assign team members** with **Write** permission to contribute within their scope
3. **Assign coordinators** with **Triage** permission for issue/PR management
4. **Reserve SuperAdmin** for project stewards only
5. **Use GitHub Teams** to group collaborators by working group for easier management
6. **Review permissions quarterly** to ensure they align with current roles
7. **Document changes** in pull requests when permission structure evolves

---

## Current Collaborators

To view current collaborators and their permissions:
- Go to **Settings** → **Collaborators and teams** on the repository page
- Or use: `gh repo collaborators list`

---

## Requesting Access

To request collaborator access to this repository:
1. Open a [GitHub Issue](https://github.com/amatcire-org/apacga-earth/issues) with your request
2. Include your GitHub username and desired working group
3. Mention a working group lead or project steward who can sponsor your access
4. Specify the permission level you need:
   - **Write** – for code/documentation contributions
   - **Triage** – for issue coordination
   - **Maintain** – for team leadership (leads only)
5. A project steward or working group lead will review and approve

---

## Off-boarding Collaborators

When a collaborator leaves or changes roles:
1. Go to **Settings** → **Collaborators and teams**
2. Click the **X** next to their name to remove access
3. Document the change in your project records
4. If transferring responsibilities, ensure successor has appropriate permissions

---

## Contact & Questions

For questions about permissions or team structure:
- **GitHub Issues**: Report permission-related concerns
- **GitHub Discussions**: Ask questions about roles and responsibilities
- **Project Steward**: Contact for governance questions
- **Working Group Leads**: Ask about your group's structure
