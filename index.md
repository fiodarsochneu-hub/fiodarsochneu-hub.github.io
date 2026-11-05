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
  
  {% assign skip_count = 0 %}
  {% assign current_month = "" %}
  {% assign inside_ul = false %}

  {% for post in site.posts %}
    {% unless post.path contains "_posts/games/" %}
      {% assign skip_count = skip_count | plus: 1 %}
      
      {% if skip_count > 3 %}
        {% comment %}Определяем месяц и год для текущей записи{% endcomment %}
        {% capture post_month %}{{ post.date | date: "%m.%Y" }}{% endcapture %}
        
        {% comment %}Если месяц изменился, выводим название нового месяца{% endcomment %}
        {% if post_month != current_month %}
          {% if inside_ul %}
            </ul>
          {% endif %}
          
          {% comment %}Форматируем название месяца на русском языке{% endcomment %}
          {% assign m = post.date | date: "%m" %}
          {% case m %}
            {% when '01' %}{% assign month_name = 'Январь' %}
            {% when '02' %}{% assign month_name = 'Февраль' %}
            {% when '03' %}{% assign month_name = 'Март' %}
            {% when '04' %}{% assign month_name = 'Апрель' %}
            {% when '05' %}{% assign month_name = 'Май' %}
            {% when '06' %}{% assign month_name = 'Июнь' %}
            {% when '07' %}{% assign month_name = 'Июль' %}
            {% when '08' %}{% assign month_name = 'Август' %}
            {% when '09' %}{% assign month_name = 'Сентябрь' %}
            {% when '10' %}{% assign month_name = 'Октябрь' %}
            {% when '11' %}{% assign month_name = 'Ноябрь' %}
            {% when '12' %}{% assign month_name = 'Декабрь' %}
          {% endcase %}
          
          <h4 style="margin-top: 15px; margin-bottom: 5px; color: #333;">📅 {{ month_name }} {{ post.date | date: "%Y" }} г.</h4>
          <ul style="list-style-type: disc; padding-left: 20px; margin-top: 5px;">
          
          {% assign current_month = post_month %}
          {% assign inside_ul = true %}
        {% endif %}

        <li style="margin-bottom: 5px;">
          <strong>{{ post.date | date: "%d.%m.%Y" }}</strong> — <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
        </li>
      {% endif %}
    {% endunless %}
  {% endfor %}

  {% if inside_ul %}
    </ul>
  {% endif %}
</details>
{% endif %}
***

### Экономика Госзакупки Коррупция
{% assign has_economy = false %}
{% for post in site.posts %}
  {% if post.path contains "_posts/economy/" %}
    {% assign has_economy = true %}
* **{{ post.date | date: "%d.%m.%Y" }}** — [{{ post.title }}]({{ post.url | relative_url }})
  {% endif %}
{% endfor %}

{% if has_economy == false %}
* Пока нет записей в играх.
{% endif %}
***

### Другие тематики 
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
