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
    {% assign check_path = "_routes/" | append: crosslink.target | append: ".md" %}
    {% for route in site.routes %}
      {% if route.relative_path == check_path %}
        {% assign crosslink_title = route.title %}
        {% assign crosslink_url = route.url %}
        {% assign crosslink_descripton = crosslink.description %}


        {% if crosslink.hash %}
          {% assign crosslink_hash = crosslink.hash | prepend: "#" %}
        {% endif %}
      {% endif %}
    {% endfor %}

    <li>
      <a href="{{ site.baseurl }}{{ crosslink_url }}{{ crosslink_hash }}">
        {{ crosslink_title }}
      </a>
      {{ crosslink_descripton }}
    </li>
  {% endfor %}
</ul>
{% endif %}
