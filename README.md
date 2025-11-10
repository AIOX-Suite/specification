# AIOX: AI-Optimized Content Exchange Standard

[![License: CC BY 4.0](https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg)](LICENSE.md)
[![Version](https://img.shields.io/badge/version-1.0.0-blue.svg)](CHANGELOG.md)
[![Adopters](https://img.shields.io/badge/adopters-15+-green.svg)](community/ADOPTERS.md)
[![Discord](https://img.shields.io/badge/discord-join-7289da.svg)](https://discord.gg/aiox)

> The open standard for AI-ready content metadata

## 🎯 What is AIOX?

AIOX provides rich metadata that helps AI systems understand not just **what** your content says, but **how**, **why**, and **for whom** it was created.

When AI crawlers like ChatGPT, Claude, Gemini, and Perplexity visit your website, they need more than raw HTML. They need context. AIOX provides that context.

## ⚡ Quick Start

Add AIOX to your webpage in 30 seconds:

```html
<script type="application/x-aiox+json">
{
  "@context": "https://aioxsuite.com/context/v1",
  "@type": "AIOX.Badge",
  "version": "1.0.0",
  "content": {
    "@type": "AIOX.ContentMetadata",
    "intent": "instructional",
    "tone": "formal",
    "targetAudience": "general",
    "domain": "Technology"
  }
}
</script>
```

**Result:** AI systems now understand your content's intent, tone, audience, and domain.

[View Full Documentation →](docs/getting-started.md)

## ✨ Features

- ✅ **13+ AI-specific metadata properties** (vs Schema.org's 5)
- ✅ **Processing transparency** - Shows how content was analyzed
- ✅ **Confidence scores** - AI knows how certain to be
- ✅ **Compatible with Schema.org** - Works together, not instead
- ✅ **Publisher manifesto support** - Define your policies
- ✅ **Open specification** - Free to implement anywhere

## 🚀 Why AIOX?

### Schema.org vs AIOX

| Feature | Schema.org | AIOX |
|---------|-----------|------|
| Basic metadata | ✅ Yes | ✅ Yes |
| Content intent | ❌ No | ✅ Yes (instructional, persuasive, etc.) |
| Target audience | ❌ No | ✅ Yes (technical level, expertise) |
| Tone & style | ❌ No | ✅ Yes (formal, casual, technical) |
| Confidence scores | ❌ No | ✅ Yes (0.0-1.0 range) |
| Processing method | ❌ No | ✅ Yes (OpenAI, Gemini, Claude, custom) |
| Domain classification | ⚠️ Limited | ✅ Yes (specific domains) |
| AI-optimized | ❌ No | ✅ Yes |
| Who controls | Google | You |

[Read detailed comparison →](docs/comparison-schema-org.md)

## 📦 Implementation Tools

### For WordPress

- **[AIOX Suite](https://wordpress.org/plugins/aiox-suite/)** (Free)
  - AI crawler analytics
  - Basic AIOX metadata
  - Badge display
  - Schema.org compatibility

- **[AIOX Suite Pro](https://aioxsuite.com)** (Commercial)
  - Full 13+ metadata properties
  - AI processing (OpenAI, Gemini, Claude)
  - Q&A generation with confidence scores
  - Custom manifesto configuration
  - Priority support
  - AI Forensics™ Tool

### For Developers

- **[Online Validator](https://validator.aioxsuite.com)** - Validate your AIOX implementation
- **[JSON Schema](schema/aiox-v1.0.json)** - Programmatic validation
- **[Examples](examples/)** - Real-world implementations
- **[Integration Guides](integrations/)** - Platform-specific guides

## 🏢 Who's Using AIOX?

- **[Viblu Studios](https://viblu.com)** - Media & Entertainment
- **Your Company Here** - [Add your site](community/ADOPTERS.md)

[See all adopters →](community/ADOPTERS.md)

## 📖 Documentation

### Getting Started
- [Quick Start Guide](docs/getting-started.md) - Implement in 5 minutes
- [Property Reference](docs/property-reference.md) - All 13+ properties explained
- [Implementation Guide](docs/implementation-guide.md) - Detailed integration
- [FAQ](docs/faq.md) - Common questions answered

### Technical Docs
- [Full Specification](SPECIFICATION.md) - Complete technical spec
- [JSON Schema](schema/aiox-v1.0.json) - Validation schema
- [Examples](examples/) - Code examples for all platforms
- [API Reference](docs/api-reference.md) - For developers

### Comparisons & Context
- [AIOX vs Schema.org](docs/comparison-schema-org.md)
- [Why AIOX Matters](docs/why-aiox.md)
- [Use Cases](docs/use-cases.md)

## 🛠️ Example Implementations

### Basic Article

```json
{
  "@context": "https://aioxsuite.com/context/v1",
  "@type": "AIOX.Badge",
  "version": "1.0.0",
  "processingMethod": "openai-gpt4",
  "processedAt": "2025-11-10T14:19:31+00:00",
  "content": {
    "@type": "AIOX.ContentMetadata",
    "url": "https://example.com/article/",
    "title": "How to Implement AIOX",
    "summary": "Step-by-step guide to implementing AIOX on your website",
    "intent": "instructional",
    "tone": "formal",
    "orientation": "second_person",
    "domain": "Technology",
    "utility": "how_to",
    "targetAudience": "technical",
    "narrativeType": "guide",
    "mediaType": "text_heavy",
    "geolocationSensitivity": "global",
    "marketSegments": ["b2b", "education"]
  },
  "qaData": {
    "@type": "AIOX.QuestionAnswerSet",
    "totalPairs": 3,
    "pairs": [
      {
        "@type": "AIOX.QAPair",
        "id": "qa-1",
        "question": "What is AIOX?",
        "answer": "AIOX is an open standard for AI-optimized content metadata.",
        "confidence": 0.95,
        "source": "ai_extraction"
      }
    ]
  },
  "manifesto": {
    "@type": "AIOX.ManifestoReference",
    "url": "https://example.com/.well-known/aiox.jsonc",
    "version": "1.0",
    "description": "Publisher policies and content structure"
  }
}
```

[View more examples →](examples/)

## 🤝 Contributing

We welcome contributions from:
- **Publishers** who want better AI integration
- **Developers** who want to build tools
- **AI Companies** who want to support the format
- **Standards Bodies** who want to collaborate

See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

### Ways to Contribute

1. **Implement AIOX** on your site and share your experience
2. **Build tools** (validators, generators, plugins)
3. **Improve documentation** (examples, guides, translations)
4. **Propose enhancements** to the specification
5. **Report issues** or bugs you find

## 🗺️ Roadmap

### ✅ Version 1.0 (Current)
- Complete specification
- WordPress plugin (free & pro)
- JSON Schema validator
- Core documentation
- Example implementations

### 🚧 In Progress (Q1 2026)
- Browser extension for validation
- CLI tools for developers
- CMS integrations (beyond WordPress)
- Video content metadata properties
- Audio content metadata properties

### 📅 Planned (Q2 2026)
- AIOX 2.0 specification
- Real-time validation API
- Content recommendation engine
- Machine learning model for metadata extraction
- W3C Community Group submission

[View detailed roadmap →](community/ROADMAP.md)

## 💬 Community

Join the AIOX community:

- **[GitHub Discussions](https://github.com/aiox-suite/specification/discussions)** - Ask questions, share ideas
- **[Discord Server](https://discord.gg/aioxsuite)** - Real-time chat with the community
- **[Newsletter](https://aioxsuite.com/newsletter)** - Bi-weekly updates
- **[Twitter/X](https://twitter.com/aioxsuite)** - Latest news and tips
- **[LinkedIn](https://linkedin.com/company/aioxsuite)** - Professional updates

## 📊 Stats

- **15+** production sites using AIOX
- **13+** metadata properties
- **3** AI processing methods supported (OpenAI, Gemini, Claude)
- **100%** compatible with Schema.org
- **0** cost to implement the specification

## 📜 License

### Specification License (Open)

The AIOX specification is licensed under [Creative Commons Attribution 4.0 International (CC BY 4.0)](LICENSE.md).

**You are free to:**
- ✅ Share — copy and redistribute the specification
- ✅ Adapt — remix, transform, and build upon the specification
- ✅ Implement — create tools and products using the specification

**Under these terms:**
- 📝 Attribution — You must give appropriate credit to AIOX

### Implementation Patent

Certain implementation methods are covered by pending patent(s). 

- **Open-source, non-commercial use:** Freely licensed
- **Commercial use:** Contact licensing@aioxsuite.com

See [LICENSE.md](LICENSE.md) for details.

### Trademark

"AIOX SUITE" and the AIOX logo are trademarks of AIOX Foundation.

## 🔗 Links

- **Website:** [aiox.io](https://aioxsuite.com)
- **Documentation:** [docs.aiox.io](https://docs.aioxsuite.com)
- **Commercial Tools:** [aioxsuite.com](https://aioxsuite.com)
- **WordPress Plugin:** [wordpress.org/plugins/aiox-publisher-suite](https://wordpress.org/plugins/aiox-suite/)
- **Validator:** [validator.aiox.io](https://validator.aioxsuite.com)

## 💡 Support

- **Documentation Issues:** Open an issue on GitHub
- **General Questions:** [GitHub Discussions](https://github.com/aiox-suite/specification/discussions)
- **Commercial Support:** support@aioxsuite.com
- **Security Issues:** security@aioxsuite.com

## 🙏 Acknowledgments

AIOX was created to solve a real problem: helping AI systems better understand web content. 

Thanks to:
- Early adopters who trusted the vision
- Contributors who improved the specification
- The open-source community for tools and feedback
- AI companies exploring support

## 📬 Contact

- **General:** support@aioxsuite.com
- **Licensing:** licensing@aioxsuite.com
- **Press:** press@aioxsuite.com
- **Partnerships:** partners@aioxsuite.com

---

**Built with ❤️ by the AIOX community**

[⭐ Star this repo](https://github.com/aiox-standard/specification) | [📖 Read the docs](https://aiox.io) | [💬 Join Discord](https://discord.gg/aiox) | [🚀 Get started](docs/getting-started.md)
