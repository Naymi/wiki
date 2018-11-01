---
title: Лог Изменений
permalink: /changelog/
---

<p>Подпишись на <a href="{{ site.baseurl }}/feed.xml">RSS</a>, чтобы быть в курсе последних обновлений.</p>

<div class="changelog">
	{% for change in site.posts %}
		<div class="changelog-item">
			<h3>{{ change.title }}</h3>
			<p><span class="date">{{ change.date | date: "%B %d, %Y" }}</span> <span class="badge {{ change.type }}">{{ change.type }}</span></p>
			{{ change.content }}
		</div>
	{% endfor %}
</div>
