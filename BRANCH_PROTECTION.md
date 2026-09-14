# Branch Protection Configuration

This document outlines the branch protection rules for the APACGA EARTH repository, with focus on maintaining code quality while enabling team contributions.

## Repository Branch Protection

### Main Branch (`main`)

**Status**: Protected with selective enforcement  
**Push Access**: ✅ **Enabled** (push = true)  
**Last Updated**: 2026-09-14

---

## Protection Rules

### Require Pull Request Reviews

**Setting**: ✅ Enabled  
**Configuration**:
- **Dismiss stale pull request approvals**: Yes
- **Require approval count**: 1
- **Require review from code owners**: No (optional)
- **Restrict who can dismiss pull request reviews**: Administrators only

**Rationale**: Ensures at least one other team member reviews changes before merge.

---

### Require Status Checks to Pass

**Setting**: ⚠️ Conditional  
**Configuration**:
- **Require branches to be up to date**: No (allows direct push)
- **Status checks**: As needed per workflow
  - CI/CD tests
  - Code quality checks
  - Security scans
  
**Rationale**: Enables fast-track commits while maintaining quality gates.

---

### Require Signed Commits

**Setting**: ❌ Disabled  
**Rationale**: Optional for team; can enable if security requirement changes.

---

### Force Pushes & Deletions

**Setting**: ❌ Disabled  
**Configuration**:
- **Allow force pushes**: No
- **Allow deletions**: No
- **Restrict deletions to**: Administrators only

**Rationale**: Prevents accidental history rewrites and branch loss.

---

## Push Access Rules

### Who Can Push Directly?

| Permission Level | Can Push | Requires Review | Notes |
|------------------|:--------:|:---------------:|-------|
| **Write** | ✅ | ✅ | Create branches; merge via PR |
| **Triage** | ✅ | ✅ | Issue management; merge via PR |
| **Maintain** | ✅ | ❌ (optional) | Team leads; can bypass with caution |
| **SuperAdmin** | ✅ | ❌ (optional) | Project stewards; full control |

---

## Workflow: Direct Push vs Pull Request

### Scenario 1: Direct Commit (Feature Branch)
```bash
# Create feature branch
git checkout -b feature/new-feature

# Make changes and commit
git add .
git commit -m "feat: add new feature"

# Push to remote
git push origin feature/new-feature

# Create Pull Request on GitHub
# → Wait for review (minimum 1 approval)
# → Merge or squash-merge
```

**Result**: Code review enforced before merge to main.

---

### Scenario 2: Direct Push to Main (Hotfix/Steward)

**Permission**: SuperAdmin or Maintain (team leads) only  
**Use case**: Critical security fixes, emergency patches

```bash
# Checkout main and pull latest
git checkout main
git pull origin main

# Make critical changes
git commit -m "fix: critical security patch"

# Push directly (if authorized)
git push origin main
```

**Best practice**: Document critical changes in commit message and create post-hoc issue/PR.

---

## Enforcement Details

### Direct Push to Main - Enabled When:
- ✅ Contributor has **Write** or higher permission
- ✅ Changes pass any configured status checks
- ✅ Commit is signed (if required)
- ✅ No conflicting branch protection rules

### Direct Push to Main - Blocked When:
- ❌ Failing CI/CD pipelines (if status checks enabled)
- ❌ Failing security scans (if configured)
- ❌ Unsigned commits (if signature required)

---

## GitHub CLI Configuration

### View Current Protection Rules
```bash
gh repo rule list --repo amatcire-org/apacga-earth
```

### Enable/Update Branch Protection
```bash
# Create protection rule for main branch
gh repo rule create --repo amatcire-org/apacga-earth \
  --branch main \
  --require-pull-request-reviews \
  --required-approving-review-count 1 \
  --dismiss-stale-reviews

# View the rule
gh repo rule view --repo amatcire-org/apacga-earth --branch main
```

---

## GitHub API Configuration

### View Protection Status
```bash
curl -H "Authorization: token <TOKEN>" \
  https://api.github.com/repos/amatcire-org/apacga-earth/branches/main/protection
```

### Update Branch Protection
```bash
curl -X PUT \
  -H "Authorization: token <TOKEN>" \
  -H "Accept: application/vnd.github.v3+json" \
  https://api.github.com/repos/amatcire-org/apacga-earth/branches/main/protection \
  -d '{
    "required_pull_request_reviews": {
      "dismiss_stale_reviews": true,
      "require_code_owner_reviews": false,
      "required_approving_review_count": 1
    },
    "enforce_admins": false,
    "allow_force_pushes": false,
    "allow_deletions": false,
    "require_signed_commits": false
  }'
```

---

## Branch Strategy

### Main Branch (`main`)
- **Purpose**: Production-ready code
- **Protection**: Required PR review (1 approval)
- **Push**: ✅ Enabled (direct commits allowed with caution)
- **Merge strategy**: Squash or rebase (keep history clean)

### Development Branch (optional `develop`)
- **Purpose**: Integration and testing
- **Protection**: Lighter (optional PR requirement)
- **Push**: ✅ Enabled
- **Merge to Main**: Via tested PR

### Feature Branches
- **Naming**: `feature/*`, `fix/*`, `docs/*`, etc.
- **Protection**: None
- **Push**: ✅ Anyone with Write permission
- **Merge**: Via PR to main

---

## Bypass & Override

### When Can Push Rules Be Bypassed?

**SuperAdmin/Project Steward**:
- Emergency production fixes
- Critical security patches
- Documented exceptions

**Maintain Permission**:
- Team lead coordination
- Approved urgent changes

**Approval Process**:
1. Document reason in commit message
2. Create post-hoc issue/discussion
3. Notify team via Discussions or issue comments
4. Schedule PR review within 24 hours

---

## Status Checks (Optional Configuration)

If CI/CD workflows are enabled, configure checks:

```yaml
# Example: .github/workflows/push-checks.yml
name: Push Checks
on: [push, pull_request]
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - name: Run tests
        run: npm test
      - name: Security scan
        run: npm audit
```

**Set as required check** in branch protection to enforce before push.

---

## Monitoring & Auditing

### View Push Activity
```bash
# See recent commits to main
git log --oneline -20 origin/main

# See who pushed what
git log --pretty=format:"%h %an %ad %s" --date=short origin/main
```

### Audit Log (GitHub)
1. Go to **Settings** → **Audit log**
2. Filter for branch protection changes
3. Monitor push activity

---

## Questions & Troubleshooting

**"Push rejected - PR review required"**
- Create a feature branch: `git checkout -b feature/your-feature`
- Push and open a PR: `git push origin feature/your-feature`
- Get 1 approval, then merge

**"Can I push directly to main?"**
- Yes, if you have Write+ permission and pass status checks
- Best practice: Use PR workflow for all changes
- Emergency push: Document in commit and post-hoc issue

**"How do I enforce status checks?"**
- Enable in **Settings** → **Branches** → **Require status checks to pass**
- Configure workflows in `.github/workflows/`

**"Who can bypass branch protection?"**
- SuperAdmin and Maintain-level users (with caution)
- Override requires documentation and team notification

---

## Contact

For questions about branch protection:
- **Technical**: Working group leads, project steward
- **Workflow issues**: Create a GitHub issue or discussion
- **Security concerns**: Contact project steward directly
