**Available methods**:

* Table of Contens will be here...
{: .toc}
{:toc}


{% if page.see_also %}
**See also:**

<ul class="toc" id="see-also-toc">
  {% for crosslink in page.see_also %}
    {% comment %}
      This is a somewhat hacky hack to assign the target url and title... One
      could use a custom filter here, but since this hack will build on Github
      Pages, we'll keep it for now.
    {% endcomment %}
    {% assign check_path = "_routes/" | append: crosslink | append: ".md" %}
    {% for route in site.routes %}
      {% if route.relative_path == check_path %}
        {% assign crosslink_title = route.title %}
        {% assign crosslink_url = route.url %}
      {% endif %}
    {% endfor %}

    <li>
      <a href="{{ site.baseurl }}{{ crosslink_url }}">
        {{ crosslink_title }}
      </a>
    </li>
  {% endfor %}
</ul>
{% endif %}
