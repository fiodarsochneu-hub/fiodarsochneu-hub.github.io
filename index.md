---
layout: default
title: Экономика
---

* ## [КАК НАМ ОБУСТРОИТЬ ЭКОНОМИКУ — ретро](docs/how-arrange-our-economy.html)
* ### [КАК РАЗРУШИТЬ ЭКОНОМИКУ?](docs/how-to-destroy-an-economy.html)
  *  #### [Тринадцать лет спустя](docs/thirteen-years-later.html)
* ## [Разделить чистые и грязные деньги](docs/separate-clean-money-from-dirty-money.html)

* ## [КАК ОБУСТРОИТЬ ГОСУДАРСТВЕННЫЕ ЗАКУПКИ](docs/how-to-organize-public-procurement.html)

***

### ✍️ Новые записи в блоге (Общие)
<ul>
   {% assign count = 0 %}
    {% for post in site.posts %}
    {% if post.categories.size == 0 %}
      <li>
       <strong>{{ post.date | date: "%d.%m.%Y" }}</strong> — <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
      <p>{{ post.excerpt }}</p>   
      </li>
     {% assign count = count | plus: 1 %}
      {% if count == 3 %}{% break %}{% endif %}
        {% endif %}
       {% endfor %}
</ul>

{% if site.posts.size > 3 %}
<details style="margin-top: 15px; cursor: pointer;">
  <summary style="font-weight: bold; color: #0066cc;">📂 Показать более старые записи...</summary>
  <ul style="margin-top: 10px;">
    {% assign skip_count = 0 %}
    {% for post in site.posts %}
      {% if post.categories.size == 0 %}
        {% assign skip_count = skip_count | plus: 1 %}
        {% if skip_count > 3 %}
          <li>
            <strong>{{ post.date | date: "%d.%m.%Y" }}</strong> — <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
          </li>
        {% endif %}
      {% endif %}
    {% endfor %}
  </ul>
</details>
{% endif %}


 ***
 ## 🃏 Архив (Игры)
<ul>
  {% assign has_games = false %}
  {% for post in site.posts %}
    {% if post.path contains "_posts/games/" %}
      {% assign has_games = true %}
      <li>
        <strong>{{ post.date | date: "%d.%m.%Y" }}</strong> — <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
      </li>
    {% endif %}
  {% endfor %}
  
  {% if has_games == false %}
    <li>Пока нет записей в играх.</li>
  {% endif %}
</ul>
 ***
### Контакты:    [facebook](https://www.facebook.com/profile.php?id=100087457504302)

