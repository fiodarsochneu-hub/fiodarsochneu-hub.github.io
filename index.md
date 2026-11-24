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

{% comment %} Получаем текущий месяц и год для автоматического открытия спойлеров {% endcomment %}
{% capture real_current_month %}{{ "now" | date: "%m.%Y" }}{% endcapture %}

### ✍️ Новые записи в блоге (Общие)

{% assign count = 0 %}
{% for post in site.posts %}
  {% unless post.path contains "_posts/other-topics/" or post.path contains "_posts/economy/" %}
* **{{ post.date | date: "%d.%m.%Y" }}** — [{{ post.title }}]({{ post.url | relative_url }})
  {{ post.excerpt }}
    {% assign count = count | plus: 1 %}
    {% if count == 3 %}{% break %}{% endif %}
  {% endunless %}
{% endfor %}

{% assign total_general = 0 %}
{% for post in site.posts %}
  {% unless post.path contains "_posts/games/" or post.path contains "_posts/economy/" %}
    {% assign total_general = total_general | plus: 1 %}
  {% endunless %}
{% endfor %}

{% if total_general > 3 %}
<details style="margin-top: 15px; cursor: pointer;">
  <summary style="font-weight: bold; color: #0066cc;">📂 Показать более старые общие записи...</summary>
  
  {% assign skip_count = 0 %}
  {% assign current_month = "" %}
  {% assign inside_details = false %}

  {% for post in site.posts %}
    {% unless post.path contains "_posts/other-topics/" or post.path contains "_posts/economy/" %}
      {% assign skip_count = skip_count | plus: 1 %}
      
      {% if skip_count > 3 %}
        {% capture post_month %}{{ post.date | date: "%m.%Y" }}{% endcapture %}
        
        {% if post_month != current_month %}
          {% if inside_details %}
            </ul>
            </details>
          {% endif %}
          
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
          
          {% if post_month == real_current_month %}
            {% assign open_attribute = "open" %}
          {% else %}
            {% assign open_attribute = "" %}
          {% endif %}
          
          <details {{ open_attribute }} style="margin-left: 15px; margin-top: 10px; cursor: pointer;">
            <summary style="font-weight: bold; color: #333333; margin-bottom: 5px;">📅 {{ month_name }} {{ post.date | date: "%Y" }} г.</summary>
            <ul style="list-style-type: disc; padding-left: 20px; margin-top: 5px;">
          
          {% assign current_month = post_month %}
          {% assign inside_details = true %}
        {% endif %}

        <li style="margin-bottom: 5px;">
          <strong>{{ post.date | date: "%d.%m.%Y" }}</strong> — <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
        </li>
      {% endif %}
    {% endunless %}
  {% endfor %}

  {% if inside_details %}
    </ul>
    </details>
  {% endif %}
</details>
{% endif %}
***

### Экономика Госзакупки Коррупция
{% assign has_economy = false %}
{% assign current_month = "" %}
{% assign inside_details = false %}

{% for post in site.posts %}
  {% if post.path contains "_posts/economy/" %}
    {% assign has_economy = true %}
    {% capture post_month %}{{ post.date | date: "%m.%Y" }}{% endcapture %}
    
    {% if post_month != current_month %}
      {% if inside_details %}
        </ul>
        </details>
      {% endif %}
      
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
      
      {% if post_month == real_current_month %}
        {% assign open_attribute = "open" %}
      {% else %}
        {% assign open_attribute = "" %}
      {% endif %}
      
<details {{ open_attribute }} style="margin-left: 15px; margin-top: 10px; cursor: pointer;">
<summary style="font-weight: bold; color: #333333; margin-bottom: 5px;">📅 {{ month_name }} {{ post.date | date: "%Y" }} г.</summary>
<ul style="list-style-type: disc; padding-left: 20px; margin-top: 5px;">
      
      {% assign current_month = post_month %}
      {% assign inside_details = true %}
    {% endif %}

    <li style="margin-bottom: 5px;">
      <strong>{{ post.date | date: "%d.%m.%Y" }}</strong> — <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
    </li>
  {% endif %}
{% endfor %}

{% if inside_details %}
  </ul>
</details>
{% endif %}

{% if has_economy == false %}
* Пока нет записей в экономике.
{% endif %}
***

### Другие тематики 
{% assign has_games = false %}
{% assign current_month = "" %}
{% assign inside_details = false %}

{% for post in site.posts %}
  {% if post.path contains "_posts/other-topics/" %}
    {% assign has_games = true %}
    {% capture post_month %}{{ post.date | date: "%m.%Y" }}{% endcapture %}
    
    {% if post_month != current_month %}
      {% if inside_details %}
</ul>
</details>
      {% endif %}
      
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
      
      {% if post_month == real_current_month %}
        {% assign open_attribute = "open" %}
      {% else %}
        {% assign open_attribute = "" %}
      {% endif %}
      
 <details {{ open_attribute }} style="margin-left: 15px; margin-top: 10px; cursor: pointer;">
 <summary style="font-weight: bold; color: #333333; margin-bottom: 5px;">📅 {{ month_name }} {{ post.date | date: "%Y" }} г.</summary>
 <ul style="list-style-type: disc; padding-left: 20px; margin-top: 5px;">
      
      {% assign current_month = post_month %}
      {% assign inside_details = true %}
    {% endif %}

    <li style="margin-bottom: 5px;">
      <strong>{{ post.date | date: "%d.%m.%Y" }}</strong> — <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
    </li>
  {% endif %}
{% endfor %}

{% if inside_details %}
</ul>
</details>
{% endif %}

{% if has_games == false %}
* Пока нет записей в играх.
{% endif %}
***


### Контакты: [facebook](https://facebook.com)
