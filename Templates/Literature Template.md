---
category: literaturenote
tags: {% if allTags %}{{allTags}}{% endif %}
citekey: {{citekey}}
status: unread
aliases:
 - "{{title}}"
dateread:
Area:
---

>[!Cite]
 {{bibliography}}


>[!info] Properties
{% for type, creators in creators | groupby("creatorType") -%}
{%- for creator in creators -%}
 >**{{"First" if loop.first}}{{type | capitalize}}**::
>{%- if creator.name %} {{creator.name}}  
>{%- else %} {{creator.lastName}}, {{creator.firstName}}  
>{%- endif %}  
>{% endfor %}~ 
>{%- endfor %}    
>**Title**:: {{title}}  
>**Year**:: {{date | format("YYYY")}}   
>**Citekey**:: {{citekey}} {%- if itemType %}  
>**itemType**:: {{itemType}}{%- endif %}{%- if itemType == "journalArticle" %}  
>**Journal**:: *{{publicationTitle}}* {%- endif %}{%- if volume %}  
>**Volume**:: {{volume}} {%- endif %}{%- if issue %}  
>**Issue**:: {{issue}} {%- endif %}{%- if itemType == "bookSection" %}  
>**Book**:: {{publicationTitle}} {%- endif %}{%- if publisher %}  
>**Publisher**:: {{publisher}} {%- endif %}{%- if place %}  
>**Location**:: {{place}} {%- endif %}{%- if pages %}   
>**Pages**:: {{pages}} {%- endif %}{%- if DOI %}  
>**DOI**:: {{DOI}} {%- endif %}{%- if ISBN %}  
>**ISBN**:: {{ISBN}} {%- endif %} 
>   

>[!LINK] File
{%- for attachment in attachments | filterby("path", "endswith", ".pdf") %}
[{{attachment.title}}](file://{{attachment.path | replace(" ", "%20")}})  {%- endfor -%}.


>[!note] 
>**Contribution**:: 
>**Related**:: {% for relation in relations | selectattr("citekey") %} [[@{{relation.citekey}}]]{% if not loop.last %}, {% endif%} {% endfor %}


> [!Abstract]
 >{%- if abstractNote %}
{{abstractNote}}
 {%- endif -%}
 >

# Notes

## Highlights
{%- macro calloutHeader(type, color) -%}  
{%- if type == "highlight" -%}
<mark style="background-color: {{color}}">Quote</mark>. 
{%- endif -%}
{%- if type == "note" -%}

{%- endif -%}
{%- endmacro -%}

{# Display highlights #}
{% for annotation in annotations -%}

{%- if annotation.type == "highlight" -%}
> [!Quote] {{ calloutHeader(annotation.type, annotation.color) }}
>{%- if annotation.annotatedText -%}{{annotation.annotatedText}} ([{{annotation.page}}](zotero://open-pdf/library/items/{{annotation.attachment.itemKey}}?page={{annotation.page}}&annotation={{annotation.id}}))
> {% endif %}
>
>{% if annotation.comment %}_{{annotation.comment}}_{%- endif %}

---

{% if not loop.last %}{% endif %}
{%- endif -%}
{% endfor %}

## Notes
{# Display notes #}
{% for annotation in annotations -%}

{%- if annotation.annotatedText -%}
>[!Quote] {{ calloutHeader(annotation.type, annotation.color) }}
{%- if annotation.type == "note" -%}
>{{annotation.annotatedText}}([{{annotation.page}}](zotero://open-pdf/library/items/{{annotation.attachment.itemKey}}?page={{annotation.page}}&annotation={{annotation.id}})){% endif %}
>_{% if annotation.comment %}{{annotation.comment}}{%- endif %}_

---
{% if not loop.last %}{% endif %}
{%- endif -%}
{% endfor %}

## Images
{# Display images #}
{% for annotation in annotations -%}
{%- if annotation.imageRelativePath -%}
![[{{annotation.imageRelativePath}}]]
_{% if annotation.comment %}{{annotation.comment}}{%- endif %}_

---
{%- endif -%}
{% endfor %}

