# AIOX Specification v1.0.0

**Status:** Stable  
**Published:** November 10, 2025  
**Authors:** AIOX team  
**License:** CC BY 4.0

---

## Abstract

AIOX (AI-Optimized Content Exchange) is a structured data format designed to provide AI systems with rich metadata about web content. This specification defines the data model, properties, and implementation requirements for AIOX.

## Table of Contents

1. [Introduction](#introduction)
2. [Design Goals](#design-goals)
3. [Data Model](#data-model)
4. [Core Types](#core-types)
5. [Properties Reference](#properties-reference)
6. [Implementation Requirements](#implementation-requirements)
7. [Examples](#examples)
8. [Versioning](#versioning)
9. [Security Considerations](#security-considerations)
10. [Privacy Considerations](#privacy-considerations)

---

## 1. Introduction

### 1.1 Purpose

AIOX provides structured metadata that enables AI systems to:
- Understand content intent and purpose
- Determine appropriate target audience
- Match tone and style in responses
- Assess confidence levels for factual claims
- Track content provenance and processing

### 1.2 Scope

This specification covers:
- Content metadata properties
- Q&A data structures
- Processing transparency
- Publisher manifesto references

This specification does NOT cover:
- AI processing algorithms (implementation-specific)
- Content extraction methods (implementation-specific)
- UI/UX for displaying AIOX data

### 1.3 Conformance

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED", "MAY", and "OPTIONAL" in this document are to be interpreted as described in RFC 2119.

---

## 2. Design Goals

AIOX is designed to be:

1. **AI-First:** Optimized for machine understanding, not just search engines
2. **Compatible:** Works alongside existing standards (Schema.org)
3. **Extensible:** Easy to add new properties as needs evolve
4. **Transparent:** Shows how content was processed
5. **Publisher-Controlled:** Publishers define their metadata
6. **Open:** Free to implement, no licensing restrictions on specification

---

## 3. Data Model

### 3.1 Format

AIOX data MUST be encoded as JSON-LD and embedded in HTML using a `<script>` tag with type `application/x-aiox+json`.

```html
<script type="application/x-aiox+json">
{
  "@context": "https://aioxsuite.com/context/v1",
  "@type": "AIOX.Badge",
  ...
}
</script>
```

### 3.2 Context

The `@context` property MUST be set to `https://aioxsuite.com/context/v1` for version 1.x of this specification.

### 3.3 Identifier

The `@id` property SHOULD be set to a unique identifier for the AIOX badge, typically the page URL with a fragment identifier:

```json
"@id": "https://example.com/page/#aiox-badge"
```

---

## 4. Core Types

### 4.1 AIOX.Badge

The root type for AIOX data.

**Required Properties:**
- `@context` (string): Must be "https://aioxsuite.com/context/v1"
- `@type` (string): Must be "AIOX.Badge"
- `version` (string): AIOX specification version (e.g., "1.0.0")
- `content` (AIOX.ContentMetadata): Content metadata object

**Optional Properties:**
- `@id` (string): Unique identifier for this badge
- `processingMethod` (string): How content was processed
- `processedAt` (string): ISO 8601 datetime of processing
- `qaData` (AIOX.QuestionAnswerSet): Q&A data
- `manifesto` (AIOX.ManifestoReference): Link to publisher manifesto

**Example:**
```json
{
  "@context": "https://aioxsuite.com/context/v1",
  "@type": "AIOX.Badge",
  "@id": "https://example.com/article/#aiox-badge",
  "version": "1.0.0",
  "processingMethod": "openai-gpt4",
  "processedAt": "2025-11-10T14:19:31+00:00",
  "content": { ... },
  "qaData": { ... },
  "manifesto": { ... }
}
```

### 4.2 AIOX.ContentMetadata

Describes the content's metadata.

**Required Properties:**
- `@type` (string): Must be "AIOX.ContentMetadata"
- `url` (string): Canonical URL of the content
- `title` (string): Content title

**Optional Properties:**
- `summary` (string): Brief summary of content
- `intent` (string): Primary intent (see [Intent Values](#intent-values))
- `tone` (string): Writing tone (see [Tone Values](#tone-values))
- `orientation` (string): Narrative perspective (see [Orientation Values](#orientation-values))
- `domain` (string): Subject matter domain
- `utility` (string): Content function (see [Utility Values](#utility-values))
- `targetAudience` (string): Intended audience (see [Audience Values](#audience-values))
- `narrativeType` (string): Content structure (see [Narrative Types](#narrative-types))
- `mediaType` (string): Format emphasis (see [Media Types](#media-types))
- `geolocationSensitivity` (string): Geographic relevance (see [Geolocation Values](#geolocation-values))
- `marketSegments` (array of strings): Business categories

### 4.3 AIOX.QuestionAnswerSet

Container for Q&A data.

**Required Properties:**
- `@type` (string): Must be "AIOX.QuestionAnswerSet"
- `totalPairs` (integer): Number of Q&A pairs
- `pairs` (array of AIOX.QAPair): The Q&A pairs

**Example:**
```json
{
  "@type": "AIOX.QuestionAnswerSet",
  "totalPairs": 2,
  "pairs": [...]
}
```

### 4.4 AIOX.QAPair

Individual question-answer pair.

**Required Properties:**
- `@type` (string): Must be "AIOX.QAPair"
- `id` (string): Unique identifier for this pair
- `question` (string): The question
- `answer` (string): The answer

**Optional Properties:**
- `confidence` (number): Confidence score (0.0 to 1.0)
- `source` (string): How this pair was created

**Example:**
```json
{
  "@type": "AIOX.QAPair",
  "id": "qa-1",
  "question": "What is AIOX?",
  "answer": "AIOX is an open standard for AI-optimized content metadata.",
  "confidence": 0.95,
  "source": "ai_extraction"
}
```

### 4.5 AIOX.ManifestoReference

Reference to publisher's manifesto.

**Required Properties:**
- `@type` (string): Must be "AIOX.ManifestoReference"
- `url` (string): URL to manifesto (typically `/.well-known/aiox.jsonc`)

**Optional Properties:**
- `version` (string): Manifesto version
- `description` (string): Brief description

**Example:**
```json
{
  "@type": "AIOX.ManifestoReference",
  "url": "https://example.com/.well-known/aiox.jsonc",
  "version": "1.0",
  "description": "Publisher policies and content structure"
}
```

---

## 5. Properties Reference

### 5.1 Intent Values

Describes the primary purpose of the content.

**Allowed Values:**
- `informational` - Provides factual information
- `instructional` - Teaches how to do something
- `persuasive` - Attempts to convince or influence
- `entertaining` - Primarily for entertainment
- `promotional` - Promotes a product or service
- `analytical` - Analyzes data or situations
- `editorial` - Opinion or commentary
- `transactional` - Facilitates a transaction

**Example:**
```json
"intent": "instructional"
```

### 5.2 Tone Values

Describes the writing style and formality.

**Allowed Values:**
- `formal` - Professional, formal language
- `casual` - Conversational, informal
- `technical` - Technical jargon, expert-level
- `conversational` - Like a friendly conversation
- `academic` - Scholarly, research-oriented
- `humorous` - Light-hearted, funny
- `authoritative` - Confident, expert
- `empathetic` - Understanding, supportive

**Example:**
```json
"tone": "formal"
```

### 5.3 Orientation Values

Describes narrative perspective.

**Allowed Values:**
- `first_person` - Uses "I", "we", "my", "our"
- `second_person` - Uses "you", "your"
- `third_person` - Uses "he", "she", "they", "it"
- `mixed` - Combination of perspectives

**Example:**
```json
"orientation": "second_person"
```

### 5.4 Utility Values

Describes content function.

**Allowed Values:**
- `how_to` - Step-by-step instructions
- `reference` - Reference material, documentation
- `tutorial` - Educational tutorial
- `analysis` - Analysis of data or situation
- `comparison` - Comparison of options
- `review` - Review of product/service
- `news` - News or announcement
- `opinion` - Opinion piece or editorial

**Example:**
```json
"utility": "how_to"
```

### 5.5 Audience Values

Describes intended audience expertise level.

**Allowed Values:**
- `general` - General public, no expertise assumed
- `beginner` - Beginners in the topic
- `intermediate` - Some knowledge assumed
- `advanced` - Significant expertise assumed
- `expert` - Expert-level knowledge required
- `technical` - Technical professionals
- `executive` - Business executives
- `academic` - Academic/research audience

**Example:**
```json
"targetAudience": "general"
```

### 5.6 Narrative Types

Describes content structure.

**Allowed Values:**
- `guide` - Comprehensive guide
- `story` - Narrative story
- `report` - Formal report
- `discussion` - Discussion or debate
- `list` - List or compilation
- `case_study` - Case study analysis
- `documentation` - Technical documentation
- `faq` - Frequently asked questions

**Example:**
```json
"narrativeType": "guide"
```

### 5.7 Media Types

Describes format emphasis.

**Allowed Values:**
- `text_heavy` - Primarily text content
- `visual` - Heavy use of images/graphics
- `interactive` - Interactive elements
- `video` - Video content
- `audio` - Audio content
- `mixed` - Mix of formats

**Example:**
```json
"mediaType": "text_heavy"
```

### 5.8 Geolocation Values

Describes geographic relevance.

**Allowed Values:**
- `global` - Globally relevant
- `regional` - Region-specific (e.g., Europe)
- `national` - Country-specific
- `local` - City or local area specific
- `country_specific` - Specific country mentioned

**Example:**
```json
"geolocationSensitivity": "global"
```

### 5.9 Market Segments

Business categories (array of strings).

**Allowed Values:**
- `b2c` - Business to consumer
- `b2b` - Business to business
- `education` - Educational content
- `entertainment` - Entertainment industry
- `healthcare` - Healthcare industry
- `finance` - Financial services
- `technology` - Technology industry
- `government` - Government/public sector
- `nonprofit` - Nonprofit organizations

**Example:**
```json
"marketSegments": ["b2c", "education", "entertainment"]
```

### 5.10 Processing Method

How content was analyzed (string).

**Common Values:**
- `openai-gpt4` - OpenAI GPT-4
- `openai-gpt4-turbo` - OpenAI GPT-4 Turbo
- `google-gemini` - Google Gemini
- `anthropic-claude` - Anthropic Claude
- `custom` - Custom processing
- `manual` - Manual curation
- `basic` - Basic extraction

**Example:**
```json
"processingMethod": "openai-gpt4"
```

---

## 6. Implementation Requirements

### 6.1 Required Elements

A conforming AIOX implementation MUST:
1. Use valid JSON-LD syntax
2. Include `@context`, `@type`, and `version` in the root object
3. Include a `content` object with at least `url` and `title`
4. Use allowed values for enumerated properties
5. Embed in HTML using `<script type="application/x-aiox+json">`

### 6.2 Optional Elements

A conforming implementation MAY:
1. Include any or all optional properties
2. Include custom properties (using namespaces)
3. Provide multiple AIOX blocks per page (different content sections)

### 6.3 Validation

Implementations SHOULD validate against the [JSON Schema](../schema/aiox-v1.0.json).

### 6.4 Compatibility with Schema.org

AIOX is designed to work alongside Schema.org. Implementations SHOULD:
1. Include both AIOX and Schema.org markup
2. Place AIOX first (primary format)
3. Use Schema.org as compatibility layer

**Example:**
```html
<!-- AIOX (Primary) -->
<script type="application/x-aiox+json">
{ AIOX data }
</script>

<!-- Schema.org (Compatibility) -->
<script type="application/ld+json">
{ Schema.org data }
</script>
```

---

## 7. Examples

### 7.1 Minimal Example

```json
{
  "@context": "https://aioxsuite.com/context/v1",
  "@type": "AIOX.Badge",
  "version": "1.0.0",
  "content": {
    "@type": "AIOX.ContentMetadata",
    "url": "https://example.com/article/",
    "title": "My Article"
  }
}
```

### 7.2 Complete Example

See [examples/blog-post.json](../examples/blog-post.json) for a complete implementation.

### 7.3 WordPress Example

See [examples/wordpress-implementation.php](../examples/wordpress-implementation.php) for WordPress integration.

---

## 8. Versioning

AIOX uses Semantic Versioning (semver):
- **Major version** (X.0.0): Breaking changes
- **Minor version** (1.X.0): New features, backward compatible
- **Patch version** (1.0.X): Bug fixes, backward compatible

Current version: **1.0.0**

### 8.1 Compatibility

AI systems SHOULD:
- Support all 1.x versions
- Gracefully degrade for unknown properties
- Fall back to Schema.org if AIOX version unsupported

---

## 9. Security Considerations

### 9.1 Content Injection

Implementations MUST sanitize all user-provided content before including in AIOX data to prevent:
- XSS attacks
- Script injection
- HTML injection

### 9.2 Data Integrity

Implementations SHOULD:
- Validate data against JSON Schema
- Verify URLs are properly formatted
- Check for malformed JSON

### 9.3 Privacy

See [Privacy Considerations](#10-privacy-considerations).

---

## 10. Privacy Considerations

### 10.1 Personal Data

AIOX data MUST NOT include:
- Personal identifiable information (PII)
- Private user data
- Sensitive information

### 10.2 Tracking

Processing methods SHOULD NOT:
- Track individual users
- Store personal browsing history
- Share data with third parties without consent

### 10.3 Transparency

Publishers SHOULD:
- Clearly state in their manifesto what data is collected
- Provide opt-out mechanisms if applicable
- Follow GDPR/CCPA requirements

---

## 11. Conformance Criteria

An implementation conforms to this specification if:

1. ✅ Uses valid JSON-LD syntax
2. ✅ Includes required properties (@context, @type, version, content.url, content.title)
3. ✅ Uses correct @context URL (https://aioxsuite.com/context/v1)
4. ✅ Uses allowed values for enumerated properties
5. ✅ Validates against JSON Schema
6. ✅ Embeds in HTML using correct script type

---

## 12. References

- **JSON-LD:** https://json-ld.org/
- **RFC 2119:** https://www.rfc-editor.org/rfc/rfc2119
- **Schema.org:** https://schema.org/
- **Semantic Versioning:** https://semver.org/

---

## Appendix A: Change Log

See [CHANGELOG.md](../CHANGELOG.md) for version history.

---

## Appendix B: Contributors

See [CONTRIBUTORS.md](../CONTRIBUTORS.md) for list of contributors.

---

**Document Version:** 1.0.0  
**Last Updated:** November 10, 2025  
**Status:** Stable  
**License:** CC BY 4.0
