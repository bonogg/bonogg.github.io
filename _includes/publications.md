<div class="publication-list">
  {% for publication in site.data.publications.main %}
    <article class="publication-card" id="{{ publication.title | slugify }}">
      <div class="publication-card__heading">
        <p class="eyebrow">{{ publication.conference | default: "Working paper" }}</p>
        <h3>{{ publication.title }}</h3>
      </div>
      <p class="publication-authors">{{ publication.authors }}</p>
      {% if publication.notes %}
        <p class="publication-notes">{{ publication.notes }}</p>
      {% endif %}
      {% if publication.others %}
        <div class="publication-abstract">{{ publication.others }}</div>
      {% endif %}
      <div class="publication-actions">
        {% if publication.pdf %}<a class="text-link" href="{{ publication.pdf | relative_url }}" target="_blank" rel="noopener">Read paper <span aria-hidden="true">↗</span></a>{% endif %}
        {% if publication.code %}<a class="text-link" href="{{ publication.code }}" target="_blank" rel="noopener">Code <span aria-hidden="true">↗</span></a>{% endif %}
      </div>
    </article>
  {% endfor %}
</div>
