# Collaborators & Team Permissions

This document outlines the permission levels and team structure for the APACGA EARTH project.

## Permission Levels

### **Write** ✍️
Permission for README and code contributions.

**Capabilities:**
- Push to branches
- Create and review pull requests
- Comment on issues and discussions
- Create and manage issues
- Participate in project discussions

**Does NOT include:**
- Repository settings management
- Branch protection rules
- Team access management
- Webhook or deploy key management

**Typical roles:** Team members, contributors, documentation writers

---

### **Maintain** 🔧
Permission for broader repository maintenance and team oversight.

**Capabilities:**
- All "Write" permissions, PLUS:
- Manage branch protection rules
- Manage team access and collaborator permissions
- Update repository settings (description, topics, visibility)
- Manage branch deletion and merging policies
- Create and manage webhooks
- Trigger GitHub Actions workflows
- Archive and unarchive branches
- Manage GitHub Pages settings

**Does NOT include:**
- Delete repository
- Change organization access policies
- Transfer repository ownership

**Typical roles:** Working group leads, technical leads, governance leads, project stewards

---

## Working Group Structure

| Working Group | Lead Role | Permission | Notes |
|---------------|-----------|-----------|-------|
| **Architecture & Infrastructure** | Lead | Maintain | Oversees system design, APIs, security controls |
| **Governance & Compliance** | Lead | Maintain | Manages decision-making processes, regulatory guidance |
| **Digital Identity** | Lead | Maintain | Manages verifiable credentials, DIDs, trust frameworks |
| **Financial Sandbox** | Lead | Maintain | Manages payment rails, token models, compliance testing |
| **AI, Data & Digital Twin** | Lead | Maintain | Manages model lifecycle, responsible AI practices |
| **Knowledge & Documentation** | Lead | Maintain | Curates technical references, whitepapers, volumes |

**Team members** within each group: **Write** permission

---

## How to Add Collaborators

### Via GitHub UI:
1. Go to **Settings** → **Collaborators and teams**
2. Click **Add people** or **Create a team**
3. Search for GitHub username
4. Select appropriate role:
   - **Write** – for team members
   - **Maintain** – for team leads
5. Send invitation

### Via GitHub CLI:
```bash
# Add collaborator with Write permission
gh repo collaborator add <username> --permission write

# Add collaborator with Maintain permission
gh repo collaborator add <username> --permission maintain
```

### Via GitHub API:
```bash
# Add collaborator with Write permission
curl -X PUT https://api.github.com/repos/amatcire-org/apacga-earth/collaborators/<username> \
  -H "Authorization: token <TOKEN>" \
  -d '{"permission":"pull"}'

# Add collaborator with Maintain permission
curl -X PUT https://api.github.com/repos/amatcire-org/apacga-earth/collaborators/<username> \
  -H "Authorization: token <TOKEN>" \
  -d '{"permission":"maintain"}'
```

---

## Team Management Best Practices

1. **Assign team leads** with **Maintain** permission to manage their working group
2. **Assign team members** with **Write** permission to contribute within their scope
3. **Use GitHub Teams** to group collaborators by working group for easier management
4. **Review permissions quarterly** to ensure they align with current roles
5. **Document additions** in [CONTRIBUTING.md](CONTRIBUTING.md) when role requirements change

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
3. Mention a working group lead who can sponsor your access
4. A project steward or working group lead will review and approve

---

## Contact

For questions about permissions or team structure:
- **Project Steward**: Create an issue or start a [discussion](https://github.com/amatcire-org/apacga-earth/discussions)
- **Working Group Leads**: Reach out via GitHub Discussions or mention in issues
