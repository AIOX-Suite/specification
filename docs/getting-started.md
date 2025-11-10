# Getting Started with AIOX

This guide will help you implement AIOX on your website in 5 minutes.

## What You'll Learn

- How to add AIOX to your webpage
- Required vs optional properties
- How to test your implementation
- Next steps and best practices

---

## Quick Implementation

### Step 1: Add the Script Tag

Add this to your webpage's `<head>` section:

```html
<script type="application/x-aiox+json">
{
  "@context": "https://aioxsuite.com/context/v1",
  "@type": "AIOX.Badge",
  "version": "1.0.0",
  "content": {
    "@type": "AIOX.ContentMetadata",
    "url": "https://yoursite.com/your-page/",
    "title": "Your Page Title"
  }
}
</script>
```

**That's it!** You now have basic AIOX implementation.

### Step 2: Add Optional Properties

Enhance your implementation with more context:

```html
<script type="application/x-aiox+json">
{
  "@context": "https://aioxsuite.com/context/v1",
  "@type": "AIOX.Badge",
  "version": "1.0.0",
  "content": {
    "@type": "AIOX.ContentMetadata",
    "url": "https://yoursite.com/your-page/",
    "title": "Your Page Title",
    "summary": "Brief description of your content",
    "intent": "instructional",
    "tone": "formal",
    "targetAudience": "general",
    "domain": "Technology"
  }
}
</script>
```

### Step 3: Validate

1. View your page source (right-click → View Page Source)
2. Search for "application/x-aiox+json"
3. Copy your AIOX JSON
4. Validate at: https://validator.aioxsuite.com (coming soon)

Or use this quick check:
```javascript
// Paste in browser console
JSON.parse(document.querySelector('script[type="application/x-aiox+json"]').textContent);
// Should return your AIOX object without errors
```

---

## Property Guide

### Required Properties (Minimum)

```json
{
  "@context": "https://aioxsuite.com/context/v1",  // REQUIRED: AIOX context
  "@type": "AIOX.Badge",                      // REQUIRED: Type
  "version": "1.0.0",                         // REQUIRED: Version
  "content": {                                // REQUIRED: Content object
    "@type": "AIOX.ContentMetadata",          // REQUIRED: Content type
    "url": "https://example.com/page/",       // REQUIRED: Page URL
    "title": "Page Title"                     // REQUIRED: Page title
  }
}
```

### Recommended Properties

```json
{
  "@context": "https://aioxsuite.com/context/v1",
  "@type": "AIOX.Badge",
  "version": "1.0.0",
  "content": {
    "@type": "AIOX.ContentMetadata",
    "url": "https://example.com/page/",
    "title": "Page Title",
    "summary": "Brief description",          // RECOMMENDED
    "intent": "instructional",               // RECOMMENDED
    "tone": "formal",                        // RECOMMENDED
    "targetAudience": "general"              // RECOMMENDED
  }
}
```

### All Available Properties

See [Property Reference](property-reference.md) for complete list.

---

## Platform-Specific Guides

### WordPress

**Option 1: Use Plugin (Easiest)**

1. Install [AIOX Publisher Suite](https://wordpress.org/plugins/aiox-publisher-suite/)
2. Configure in Settings → AIOX Publisher
3. Done! AIOX automatically added to all posts/pages

**Option 2: Manual Implementation**

Add to your theme's `header.php` or use Code Snippets plugin:

```php
<?php
function add_aiox_metadata() {
    if (is_singular()) {
        $aiox_data = array(
            '@context' => 'https://aioxsuite.com/context/v1',
            '@type' => 'AIOX.Badge',
            'version' => '1.0.0',
            'content' => array(
                '@type' => 'AIOX.ContentMetadata',
                'url' => get_permalink(),
                'title' => get_the_title(),
                'summary' => get_the_excerpt(),
                'intent' => 'informational',
                'tone' => 'casual',
                'targetAudience' => 'general'
            )
        );
        
        echo '<script type="application/x-aiox+json">';
        echo wp_json_encode($aiox_data, JSON_PRETTY_PRINT);
        echo '</script>';
    }
}
add_action('wp_head', 'add_aiox_metadata');
```

[View complete WordPress guide →](../integrations/wordpress/)

### Static Sites (HTML/Jekyll/Hugo)

Add to your template:

```html
<!DOCTYPE html>
<html>
<head>
    <title>{{ title }}</title>
    
    <script type="application/x-aiox+json">
    {
      "@context": "https://aioxsuite.com/context/v1",
      "@type": "AIOX.Badge",
      "version": "1.0.0",
      "content": {
        "@type": "AIOX.ContentMetadata",
        "url": "{{ url }}",
        "title": "{{ title }}",
        "summary": "{{ description }}",
        "intent": "{{ intent }}",
        "tone": "{{ tone }}"
      }
    }
    </script>
</head>
<body>
    <!-- Your content -->
</body>
</html>
```

### JavaScript/React

```javascript
import React from 'react';
import { Helmet } from 'react-helmet';

function AIOXMetadata({ content }) {
  const aiox = {
    "@context": "https://aioxsuite.com/context/v1",
    "@type": "AIOX.Badge",
    "version": "1.0.0",
    "content": {
      "@type": "AIOX.ContentMetadata",
      "url": content.url,
      "title": content.title,
      "summary": content.summary,
      "intent": content.intent,
      "tone": content.tone,
      "targetAudience": content.targetAudience
    }
  };

  return (
    <Helmet>
      <script type="application/x-aiox+json">
        {JSON.stringify(aiox, null, 2)}
      </script>
    </Helmet>
  );
}

export default AIOXMetadata;
```

[View more integrations →](../integrations/)

---

## Common Use Cases

### Blog Post

```json
{
  "@context": "https://aioxsuite.com/context/v1",
  "@type": "AIOX.Badge",
  "version": "1.0.0",
  "content": {
    "@type": "AIOX.ContentMetadata",
    "url": "https://blog.example.com/post/",
    "title": "10 Tips for Better Code",
    "summary": "Practical tips to improve your coding skills",
    "intent": "instructional",
    "tone": "casual",
    "targetAudience": "intermediate",
    "domain": "Technology",
    "utility": "how_to",
    "narrativeType": "list",
    "mediaType": "text_heavy"
  }
}
```

### Product Page

```json
{
  "@context": "https://aioxsuite.com/context/v1",
  "@type": "AIOX.Badge",
  "version": "1.0.0",
  "content": {
    "@type": "AIOX.ContentMetadata",
    "url": "https://shop.example.com/product/",
    "title": "Professional Camera Lens",
    "summary": "High-quality lens for professional photography",
    "intent": "promotional",
    "tone": "formal",
    "targetAudience": "expert",
    "domain": "Photography",
    "utility": "reference",
    "marketSegments": ["b2c", "b2b"]
  }
}
```

### News Article

```json
{
  "@context": "https://aioxsuite.com/context/v1",
  "@type": "AIOX.Badge",
  "version": "1.0.0",
  "content": {
    "@type": "AIOX.ContentMetadata",
    "url": "https://news.example.com/article/",
    "title": "Tech Industry Updates",
    "summary": "Latest developments in the tech sector",
    "intent": "informational",
    "tone": "formal",
    "targetAudience": "general",
    "domain": "Technology",
    "utility": "news",
    "narrativeType": "report",
    "geolocationSensitivity": "global"
  }
}
```

---

## Best Practices

### ✅ Do's

- **Include AIOX on every page** with unique content
- **Use accurate property values** that match your content
- **Keep it alongside Schema.org** for compatibility
- **Update when content changes** significantly
- **Test your implementation** regularly

### ❌ Don'ts

- **Don't use generic values** for every page (be specific)
- **Don't include personal data** (PII) in metadata
- **Don't manipulate intent** to game AI systems
- **Don't forget to update** version when spec changes
- **Don't use invalid JSON** (validate before publishing)

---

## Troubleshooting

### My AIOX isn't showing up

1. **Check HTML source:** View page source, search for "application/x-aiox+json"
2. **Validate JSON:** Copy JSON, paste into JSON validator
3. **Check location:** Must be in `<head>` or before `</body>`
4. **Check caching:** Clear cache, reload page

### Validation errors

**Common issues:**
- Missing required properties (`@context`, `@type`, `version`, `content.url`, `content.title`)
- Invalid JSON syntax (missing commas, quotes)
- Wrong property values (check allowed values in spec)
- Wrong script type (must be `application/x-aiox+json`)

### Still stuck?

- [Check FAQ](faq.md)
- [Ask in GitHub Discussions](https://github.com/aiox-standard/specification/discussions)
- [Join Discord](https://discord.gg/aioxsuitesuite)

---

## Next Steps

### Level Up Your Implementation

1. **Add more properties** - See [Property Reference](property-reference.md)
2. **Add Q&A data** - Help AI systems with factual questions
3. **Create manifesto** - Define your publisher policies
4. **Add processing info** - Show how content was analyzed

### Join the Community

- **Star the repo** on GitHub
- **Add your site** to [ADOPTERS.md](../community/ADOPTERS.md)
- **Share your experience** in Discussions
- **Help others** in Discord

### Advanced Topics

- [Complete Property Reference](property-reference.md)
- [Q&A Data Structure](qa-data-guide.md)
- [Publisher Manifesto](manifesto-guide.md)
- [AI Processing Integration](ai-processing-guide.md)

---

## Resources

- **Full Specification:** [SPECIFICATION.md](../SPECIFICATION.md)
- **All Examples:** [examples/](../examples/)
- **Integration Guides:** [integrations/](../integrations/)
- **Property Reference:** [property-reference.md](property-reference.md)

---

**Questions?** Open an issue or ask in [Discussions](https://github.com/aiox-standard/specification/discussions).

**Ready to go pro?** Check out [AIOX Publisher Suite Pro](https://aioxsuite.com) for automated processing with AI.
