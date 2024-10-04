***This Code goes to the plugin configuration tab***


---
tags:
  - "#books"
  - "#resource"
  - "Wkindle"
Area:
  - "[[Livros]]"
---

# {{title}}
## Metadata
{% trim %}
{% if authorUrl %}
* Author: [{{author}}]({{authorUrl}})
{% elif author %}
* Author: [[{{author}}]]
{% endif %}
{% if asin %}* ASIN: {{asin}}{% endif %}
{% if isbn %}* ISBN: {{isbn}}{% endif %}
{% if pages %}* Pages: {{pages}}{% endif %}
{% if publication %}* Publication: {{publication}}{% endif %}
{% if publisher %}* Publisher: {{publisher}}{% endif %}
{% if url %}* Reference: {{url}}{% endif %}
{% if appLink %}* [Kindle link]({{appLink}}){% endif %}
{% endtrim %}

## Highlights
{{highlights}}
