# Changelog

All notable changes to the AIOX specification will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

### Planned
- Video content metadata properties
- Audio content metadata properties
- Real-time validation API
- Extended confidence scoring methods

---

## [1.0.0] - 2025-11-10

### Added
- Initial stable release of AIOX specification
- Core metadata properties (13+ properties)
- `AIOX.Badge` root type
- `AIOX.ContentMetadata` type with properties:
  - `intent` (8 values)
  - `tone` (8 values)
  - `orientation` (4 values)
  - `domain` (free text)
  - `utility` (8 values)
  - `targetAudience` (8 values)
  - `narrativeType` (8 values)
  - `mediaType` (6 values)
  - `geolocationSensitivity` (5 values)
  - `marketSegments` (9+ values)
- `AIOX.QuestionAnswerSet` for Q&A data
- `AIOX.QAPair` with confidence scores
- `AIOX.ManifestoReference` for publisher policies
- Processing transparency properties:
  - `processingMethod`
  - `processedAt`
  - `version`
- JSON-LD format with `application/x-aiox+json` MIME type
- Complete JSON Schema for validation
- Comprehensive documentation
- Real-world examples (blog post, article, product)
- WordPress implementation guide
- Security and privacy considerations
- Compatibility layer with Schema.org

### Documentation
- README.md with quick start guide
- SPECIFICATION.md with complete technical spec
- LICENSE.md with dual licensing model
- CONTRIBUTING.md with contribution guidelines
- Property reference guide
- Implementation guide
- FAQ document
- Comparison with Schema.org

### Examples
- Basic article example
- Blog post example
- Technical documentation example
- WordPress PHP implementation
- JavaScript implementation
- Static site implementation

### Tools
- JSON Schema (v1.0)
- Online validator (planned)
- Example generator (planned)

---

## Version History Summary

| Version | Date | Description |
|---------|------|-------------|
| 1.0.0 | 2025-11-10 | Initial stable release |
| 0.9.0 | 2025-11-01 | Beta release for testing |
| 0.5.0 | 2025-10-15 | Alpha release for early adopters |
| 0.1.0 | 2025-10-01 | Initial draft specification |

---

## Upgrade Guide

### Migrating to 1.0.0 from Beta (0.9.0)

**Breaking Changes:** None

**New Features:**
- Finalized all property values
- Complete JSON Schema
- Production-ready documentation

**Action Required:**
- Update version number to "1.0.0" in your implementation
- No other changes needed

### Migrating from Alpha (0.5.0) to 1.0.0

**Breaking Changes:**
- `audience` property renamed to `targetAudience`
- `contentType` property renamed to `utility`
- Removed `experimental` flag

**Action Required:**
1. Update property names in your implementation
2. Update version number to "1.0.0"
3. Review new allowed values for properties

**Example Migration:**

```json
// Before (0.5.0)
{
  "version": "0.5.0",
  "content": {
    "audience": "general",
    "contentType": "tutorial",
    "experimental": true
  }
}

// After (1.0.0)
{
  "version": "1.0.0",
  "content": {
    "targetAudience": "general",
    "utility": "tutorial"
  }
}
```

---

## Deprecation Policy

AIOX follows semantic versioning:

- **Major version (X.0.0):** May include breaking changes
  - Deprecated features removed
  - Required properties may change
  - 6 months notice before removal

- **Minor version (1.X.0):** Backward compatible additions
  - New optional properties
  - New allowed values
  - Enhanced features

- **Patch version (1.0.X):** Bug fixes only
  - Documentation corrections
  - Schema validation fixes
  - Clarifications

---

## Future Roadmap

### Version 1.1.0 (Planned Q1 2026)
- [ ] Video content properties
  - `videoDuration`
  - `videoQuality`
  - `hasSubtitles`
  - `videoFormat`
- [ ] Audio content properties
  - `audioDuration`
  - `audioFormat`
  - `hasTranscript`
- [ ] Enhanced confidence scoring
  - Source-level confidence
  - Fact-checking integration

### Version 1.2.0 (Planned Q2 2026)
- [ ] Internationalization support
  - `language` property
  - `translationAvailable`
  - Multi-language Q&A
- [ ] Accessibility properties
  - `a11yCompliant`
  - `readingLevel`
  - `alternativeFormatsAvailable`

### Version 2.0.0 (Planned Q3 2026)
- [ ] Major revision based on community feedback
- [ ] Potential breaking changes for optimization
- [ ] Enhanced AI-specific features
- [ ] Real-time content update properties

---

## Release Process

1. **Pre-Release:**
   - Community discussion (2-4 weeks)
   - RFC if major changes
   - Beta testing period
   - Documentation review

2. **Release:**
   - Update CHANGELOG.md
   - Update version in all examples
   - Tag release on GitHub
   - Publish announcement
   - Update documentation site

3. **Post-Release:**
   - Monitor for issues
   - Address critical bugs quickly
   - Gather community feedback
   - Plan next version

---

## How to Stay Updated

- **Watch this repo** for release notifications
- **Join [Discord](https://discord.gg/aioxsuite)** for real-time updates
- **Subscribe to [newsletter](https://aioxsuite.com/newsletter)** for major releases
- **Follow [@aioxstandard](https://twitter.com/aioxsuite)** on Twitter/X

---

## Security Updates

Security issues are addressed immediately in patch releases.

**Report security issues to:** security@aioxsuite.com

Security patches will be:
- Released within 48 hours of confirmed issue
- Documented with CVE if applicable
- Announced via all channels

---

## Contributing to Changelog

When submitting a PR that changes functionality:
1. Add entry to `[Unreleased]` section
2. Use appropriate category (Added, Changed, Deprecated, Removed, Fixed, Security)
3. Link to PR or issue number
4. Keep descriptions clear and concise

---

[Unreleased]: https://github.com/aiox-suite/specification/compare/v1.0.0...HEAD
[1.0.0]: https://github.com/aiox-suite/specification/releases/tag/v1.0.0
