---
layout: default
title: Economy
---

* ## [КАК НАМ ОБУСТРОИТЬ ЭКОНОМИКУ — ретро](docs/how-arrange-our-economy.html)
* ### [КАК РАЗРУШИТЬ ЭКОНОМИКУ?](docs/how-to-destroy-an-economy.html)
  *  #### [Тринадцать лет спустя](docs/thirteen-years-later.html)
* ## [Разделить чистые и грязные деньги](docs/separate-clean-money-from-dirty-money.html)

* ## [КАК ОБУСТРОИТЬ ГОСУДАРСТВЕННЫЕ ЗАКУПКИ](docs/how-to-organize-public-procurement.html)

***

### ✍️ Новые записи в блоге (Общие)

{% assign count = 0 %}
{% for post in site.posts %}
  {% unless post.path contains "_posts/games/" %}
* **{{ post.date | date: "%d.%m.%Y" }}** — [{{ post.title }}]({{ post.url | relative_url }})
  {{ post.excerpt }}
    {% assign count = count | plus: 1 %}
    {% if count == 3 %}{% break %}{% endif %}
  {% endunless %}
{% endfor %}

{% if site.posts.size > 3 %}
<details style="margin-top: 15px; cursor: pointer;">
  <summary style="font-weight: bold; color: #0066cc;">📂 Показать более старые общие записи...</summary>
  <ul style="margin-top: 10px; list-style-type: disc; padding-left: 20px;">
{% assign skip_count = 0 %}
{% for post in site.posts %}
  {% unless post.path contains "_posts/games/" %}
    {% assign skip_count = skip_count | plus: 1 %}
    {% if skip_count > 3 %}
    <li style="margin-bottom: 5px;">
      <strong>{{ post.date | date: "%d.%m.%Y" }}</strong> — <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
    </li>
    {% endif %}
  {% endunless %}
{% endfor %}
  </ul>
</details>
{% endif %}

***

### 🃏 Архив (Игры)

{% assign has_games = false %}
{% for post in site.posts %}
  {% if post.path contains "_posts/games/" %}
    {% assign has_games = true %}
* **{{ post.date | date: "%d.%m.%Y" }}** — [{{ post.title }}]({{ post.url | relative_url }})
  {% endif %}
{% endfor %}

{% if has_games == false %}
* Пока нет записей в играх.
{% endif %}

***

### Контакты: [facebook](https://facebook.com)
