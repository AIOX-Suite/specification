# Contributing to AIOX

First off, thank you for considering contributing to AIOX! It's people like you that make AIOX a great standard for the AI era.

## 🌟 Ways to Contribute

### 1. Use AIOX and Share Your Experience
- Implement AIOX on your website
- Share your results in [GitHub Discussions](https://github.com/aiox-suite/specification/discussions)
- Add your site to [ADOPTERS.md](community/ADOPTERS.md)

### 2. Improve Documentation
- Fix typos or clarify confusing sections
- Add examples for different platforms
- Translate documentation to other languages
- Create tutorials or guides

### 3. Build Tools
- Validators
- Generators
- Browser extensions
- CMS plugins
- CLI tools

### 4. Propose Enhancements
- Suggest new properties
- Propose specification improvements
- Share use cases we haven't considered

### 5. Report Issues
- Bugs in documentation
- Unclear specification language
- Security concerns
- Privacy issues

---

## 📋 Contribution Process

### For Documentation/Spec Changes

1. **Check existing issues** - Someone may already be working on it
2. **Open an issue first** - Discuss your proposed changes
3. **Fork the repository**
4. **Create a branch** - Use a descriptive name (e.g., `docs/clarify-intent-property`)
5. **Make your changes**
6. **Test your changes** - Ensure examples still work
7. **Submit a pull request**
8. **Address feedback** - Be responsive to review comments

### For Code Contributions

1. **Check existing issues** or create one
2. **Fork and branch**
3. **Follow code style** - Match existing patterns
4. **Add tests** if applicable
5. **Update documentation** if needed
6. **Submit PR** with clear description

---

## 📝 Pull Request Guidelines

### Good PR Titles

✅ **Good:**
- `docs: clarify intent property values`
- `feat: add Python implementation example`
- `fix: correct JSON schema validation error`

❌ **Bad:**
- `Update README`
- `Fix stuff`
- `Changes`

### PR Description Template

```markdown
## Description
Brief description of what this PR does.

## Type of Change
- [ ] Documentation update
- [ ] New feature/example
- [ ] Bug fix
- [ ] Specification change

## Motivation
Why is this change needed?

## Changes Made
- List of specific changes
- Be clear and concise

## Testing Done
How have you tested this?

## Checklist
- [ ] Documentation updated
- [ ] Examples still work
- [ ] No breaking changes (or clearly documented)
- [ ] Follows existing style/patterns
```

---

## 🎨 Code Style

### JSON Examples
- Use 2-space indentation
- Include comments where helpful
- Use consistent property ordering
- Follow specification exactly

### Markdown
- Use ATX-style headers (`#` not `===`)
- One sentence per line (makes diffs cleaner)
- Use fenced code blocks with language specified
- Keep lines under 100 characters when practical

### Code Examples (PHP, JavaScript, etc.)
- Follow language-specific best practices
- Include comments for clarity
- Use meaningful variable names
- Keep examples simple and focused

---

## 🔍 Specification Changes

Changes to `SPECIFICATION.md` require extra care:

### Major Changes (Breaking)
- Require community discussion
- Need strong justification
- Will result in v2.0.0
- Examples: Removing properties, changing required fields

### Minor Changes (Non-Breaking)
- New optional properties
- Additional allowed values
- Clarifications
- Will result in v1.X.0

### Patch Changes
- Typos
- Documentation improvements
- Non-functional changes
- Will result in v1.0.X

### Process for Spec Changes

1. **Open an issue** titled `[SPEC] Your proposed change`
2. **Discuss with community** - Allow at least 1 week for feedback
3. **Create RFC** if major change (see `community/rfcs/`)
4. **Get consensus** from maintainers
5. **Submit PR** with changes
6. **Update version** following semver

---

## 🧪 Testing Guidelines

### For Documentation
- [ ] All links work
- [ ] Code examples are valid JSON
- [ ] Examples match specification
- [ ] No typos or grammar errors

### For Code/Tools
- [ ] Unit tests pass
- [ ] Integration tests pass (if applicable)
- [ ] Manual testing done
- [ ] Works across platforms/browsers

### For Specification Changes
- [ ] All examples updated
- [ ] JSON schema updated
- [ ] Backward compatibility considered
- [ ] Migration guide provided (if breaking)

---

## 🐛 Bug Reports

### Good Bug Reports Include:

1. **Clear title** - "JSON schema validation fails for confidence scores"
2. **Description** - What happened vs what you expected
3. **Steps to reproduce** - Numbered list
4. **Example** - Minimal code/data that reproduces issue
5. **Environment** - Browser, OS, tool version, etc.
6. **Screenshots** if relevant

### Bug Report Template

```markdown
## Bug Description
Clear description of the bug.

## Expected Behavior
What should happen?

## Actual Behavior
What actually happens?

## Steps to Reproduce
1. Step one
2. Step two
3. Step three

## Example Code/Data
```json
{
  "example": "data that reproduces the issue"
}
```

## Environment
- Tool/Platform: 
- Version:
- Browser (if applicable):
- OS:

## Additional Context
Any other relevant information.
```

---

## 💡 Feature Requests

### Good Feature Requests Include:

1. **Use case** - Why do you need this?
2. **Proposed solution** - How should it work?
3. **Alternatives considered** - What else did you think about?
4. **Examples** - Show what it would look like

### Feature Request Template

```markdown
## Feature Description
Clear description of the feature.

## Use Case
Why is this needed? What problem does it solve?

## Proposed Solution
How should this work?

### Example
```json
{
  "example": "of how it would look"
}
```

## Alternatives Considered
What other approaches did you think about?

## Additional Context
Any other relevant information.
```

---

## 🏷️ Adding Your Site to ADOPTERS.md

We love showcasing sites using AIOX!

1. **Fork the repo**
2. **Edit** `community/ADOPTERS.md`
3. **Add your site** in this format:
   ```markdown
   ### [Your Site Name](https://yoursite.com)
   - **Category:** Media & Entertainment / Technology / etc.
   - **Implementation:** WordPress Plugin / Custom / etc.
   - **Since:** November 2025
   - **Description:** Brief description of your site and how you use AIOX
   ```
4. **Submit PR** with title: `docs: add [Your Site] to adopters`

---

## 🌍 Translations

We welcome translations of documentation!

### Translation Process

1. **Check if translation exists** - See `docs/translations/`
2. **Create language folder** - `docs/translations/es/` for Spanish
3. **Translate core docs**:
   - README.md
   - getting-started.md
   - faq.md
4. **Keep structure same** - Same headings, same order
5. **Add to main README** - Link to your translation
6. **Submit PR** with title: `docs: add Spanish translation`

### Translation Guidelines

- Keep technical terms in English (AIOX, JSON-LD, etc.)
- Maintain same formatting
- Translate examples in code comments
- Don't translate code itself
- Keep links functional

---

## 🤝 Code of Conduct

### Our Pledge

We are committed to providing a welcoming and inclusive experience for everyone.

### Our Standards

**Positive behavior includes:**
- Using welcoming and inclusive language
- Being respectful of differing viewpoints
- Gracefully accepting constructive criticism
- Focusing on what is best for the community
- Showing empathy towards other community members

**Unacceptable behavior includes:**
- Harassment, trolling, or insulting comments
- Personal or political attacks
- Publishing others' private information
- Other conduct which could reasonably be considered inappropriate

### Enforcement

Violations of the code of conduct may result in:
1. Warning
2. Temporary ban
3. Permanent ban

Report violations to: conduct@aioxsuite.com

---

## 📜 Licensing

By contributing to AIOX, you agree that:

1. **Your contributions** will be licensed under [CC BY 4.0](LICENSE.md)
2. **You have the right** to submit the contribution
3. **You retain copyright** to your contributions
4. **You grant** us and everyone else the right to use your contribution under CC BY 4.0

For code contributions to tools:
- Match the license of that tool's repository
- Typically MIT or Apache 2.0 for tools

---

## ❓ Questions?

- **General questions:** [GitHub Discussions](https://github.com/aiox-suite/specification/discussions)
- **Quick questions:** [Discord](https://discord.gg/aioxsuite)
- **Security issues:** security@aioxsuite.com
- **Other:** hello@aioxsuite.com

---

## 🎯 Priority Areas

We especially welcome contributions in these areas:

### High Priority
- [ ] More real-world examples (different industries)
- [ ] Platform integration guides (Ghost, Drupal, etc.)
- [ ] Translation to major languages
- [ ] Video tutorial content
- [ ] Case studies showing AIOX benefits

### Medium Priority
- [ ] Browser extension for validation
- [ ] CLI tools for developers
- [ ] Automated testing frameworks
- [ ] Performance benchmarks
- [ ] Accessibility improvements

### Nice to Have
- [ ] Alternative visualization tools
- [ ] Integration with popular CMSs
- [ ] Mobile app for testing
- [ ] Analytics dashboard
- [ ] Community showcase site

---

## 🙏 Recognition

Contributors will be:
- Listed in [CONTRIBUTORS.md](CONTRIBUTORS.md)
- Credited in release notes
- Thanked in the community
- Eligible for "AIOX Contributor" badge (coming soon)

Major contributors may be invited to join the AIOX Working Group.

---

## 📚 Resources

- [Specification](SPECIFICATION.md) - Full technical spec
- [Examples](examples/) - Code examples
- [Property Reference](docs/property-reference.md) - All properties explained
- [GitHub Discussions](https://github.com/aiox-suite/specification/discussions) - Community discussions
- [Discord](https://discord.gg/aioxsuite) - Real-time chat

---

## 🚀 Getting Started

Not sure where to start? Here are some beginner-friendly tasks:

1. **Fix a typo** - Easy first contribution!
2. **Improve an example** - Make examples clearer
3. **Add an FAQ answer** - Share knowledge
4. **Create a tutorial** - Help others learn
5. **Test the specification** - Find edge cases

Look for issues labeled `good-first-issue` or `help-wanted`.

---

Thank you for making AIOX better! 🎉

**Questions about contributing?** Open an issue or ask in [Discord](https://discord.gg/aioxsuite).
