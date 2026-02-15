```markdown
---
type: manifest
subtype: assets
title: Asset Manifest
---

## Image Manifest

**Summary:** {{p08_extract_images.summary}}
**Total Images Found:** {{p08_extract_images.totalFound}} ({{p08_extract_images.highPriority}} high priority)

### Logos

{% for image in p08_extract_images.images if image.purpose == "logo" %}
- Name: {{image.name}} (derived from URL)
  Source URL: {{image.url}}
  Purpose: Logo
  Priority: {{image.priority}}
  Status: pending
{% endfor %}

### Heroes

{% for image in p08_extract_images.images if image.purpose == "hero" %}
- Name: {{image.name}} (derived from URL)
  Source URL: {{image.url}}
  Purpose: Hero
  Priority: {{image.priority}}
  Status: pending
{% endfor %}

### Products

{% for image in p08_extract_images.images if image.purpose == "product" %}
- Name: {{image.name}} (derived from URL)
  Source URL: {{image.url}}
  Purpose: Product
  Priority: {{image.priority}}
  Status: pending
{% endfor %}

### Icons

{% for image in p08_extract_images.images if image.purpose == "icon" %}
- Name: {{image.name}} (derived from URL)
  Source URL: {{image.url}}
  Purpose: Icon
  Priority: {{image.priority}}
  Status: pending
{% endfor %}

### Other

{% for image in p08_extract_images.images if image.purpose not in ["logo", "hero", "product", "icon"] %}
- Name: {{image.name}} (derived from URL)
  Source URL: {{image.url}}
  Purpose: {{image.purpose}}
  Priority: {{image.priority}}
  Status: pending
{% endfor %}
```
