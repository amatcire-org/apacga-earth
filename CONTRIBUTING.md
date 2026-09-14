# Contributing to APACGA EARTH

Thank you for your interest in contributing to APACGA EARTH! This document outlines the process for contributing code, documentation, and ideas.

## Getting Started

1. **Read the README** – Understand the project scope and structure
2. **Review COLLABORATORS.md** – Learn about permission levels and team structure
3. **Check existing issues/discussions** – Avoid duplicate work
4. **Fork or branch** – Create a feature branch for your work

## Permission Levels

### **Write** (Push enabled)
- Create and push commits to branches
- Create and review pull requests
- Comment on issues and discussions
- Participate in project discussions

### **Triage**
- All "Write" permissions, PLUS:
- Manage issue labels, milestones, and priorities
- Close and reopen issues
- Lock discussions

### **Maintain** ❌ DISABLED
- Use **Triage** instead for team coordination

### **Admin**
- Reserved for project stewards only
- Full repository control

See [COLLABORATORS.md](COLLABORATORS.md) for full details.

## Code of Conduct

All contributors must:
- Be respectful and inclusive
- Provide constructive feedback
- Respect intellectual property and privacy
- Follow local laws and regulations
- Report violations to the project steward

## Contribution Workflow

### 1. Create an Issue or Discussion
- **For bugs**: Open an [issue](https://github.com/amatcire-org/apacga-earth/issues) with steps to reproduce
- **For features**: Start a [discussion](https://github.com/amatcire-org/apacga-earth/discussions) to propose the idea
- **For documentation**: Create an issue linking to the section you want to improve

### 2. Create a Branch
```bash
git checkout -b feature/short-description
# or
git checkout -b fix/issue-number-short-description
```

Branch naming conventions:
- `feature/` – New functionality
- `fix/` – Bug fixes
- `docs/` – Documentation updates
- `refactor/` – Code refactoring
- `test/` – Test additions

### 3. Make Your Changes
- Keep commits atomic and well-documented
- Follow existing code style and conventions
- Add tests for new functionality
- Update documentation as needed

### 4. Commit Message Format
```
<type>: <short description>

<optional body with more details>

Fixes #<issue-number> (if applicable)
```

Types:
- `feat:` – New feature
- `fix:` – Bug fix
- `docs:` – Documentation
- `test:` – Tests
- `refactor:` – Code refactoring
- `chore:` – Maintenance

**Example**:
```
feat: add digital identity verification endpoint

Implements verifiable credential validation following W3C standards.
Adds unit tests and integration tests for new endpoints.

Fixes #42
```

### 5. Push and Create a Pull Request

```bash
git push origin feature/short-description
```

**PR Description template:**
```markdown
## Description
Brief description of what this PR does.

## Related Issue(s)
Fixes #<issue-number>

## Type of Change
- [ ] Bug fix
- [ ] New feature
- [ ] Documentation update
- [ ] Other (describe)

## How to Test
Steps to verify the changes.

## Checklist
- [ ] Code follows style guidelines
- [ ] Comments added for complex logic
- [ ] Documentation updated
- [ ] Tests added/updated
- [ ] All tests passing
```

### 6. Code Review
- At least one review required before merge
- Address feedback from reviewers
- Maintain constructive dialogue

### 7. Merge
- Once approved, merge using squash or rebase
- Delete feature branch after merge

## Documentation Standards

### README & Docs
- Use clear, concise language
- Include examples where helpful
- Link to related sections and external references
- Keep headings hierarchical (# → ## → ###)

### Code Comments
- Explain *why*, not *what*
- Use JSDoc/docstring format for functions
- Add inline comments for complex logic

### Knowledge Volumes
- Organize by topic/volume number
- Include references and citations
- Mark as draft or final
- Version control for significant updates

## Testing

- **Unit tests**: For individual functions/methods
- **Integration tests**: For component interactions
- **Documentation tests**: Verify examples work

Run tests before submitting:
```bash
npm test  # or equivalent for your language
```

## Pull Request Merge Policy

- **Default**: Squash and merge (clean history)
- **Option**: Rebase and merge (preserve commits)
- **Avoid**: Merge commits (keeps history linear)

Protected branch rules:
- At least 1 approval required
- All checks must pass
- Up-to-date with main branch

## Release & Versioning

- Semantic versioning: `MAJOR.MINOR.PATCH`
- Release notes included with each version
- Tags created for releases
- Changelog maintained in `CHANGELOG.md`

## Working with Teams

### Your Working Group
- **Find your group**: See [COLLABORATORS.md](COLLABORATORS.md)
- **Coordinate with leads**: Check in on priorities and direction
- **Async communication**: Use Discussions, issues, and comments
- **Synchronous meetings**: Scheduled as needed

### Cross-team Work
- Open issues with cross-team labels
- Tag relevant working group leads
- Use Discussions for design decisions

## Legal & Compliance

- All contributions must comply with the [MIT License](LICENSE)
- By contributing, you agree your work is licensed under MIT
- No proprietary or restricted content
- Respect regulatory guidelines for your region

## Questions or Issues?

- **GitHub Issues**: Report bugs or request features
- **GitHub Discussions**: Ask questions, discuss ideas
- **Project Steward**: Contact for governance questions
- **Working Group Leads**: Technical questions within your group

## Recognition

Contributors will be:
- Listed in release notes for significant contributions
- Mentioned in project documentation
- Recognized in the community

Thank you for contributing to APACGA EARTH! 🌍
