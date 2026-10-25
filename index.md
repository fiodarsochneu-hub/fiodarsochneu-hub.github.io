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


 ***
 ### 🃏 Архив
<ul>
  {% for post in site.categories.games %}
    <li><strong>{{ post.date | date: "%d.%m.%Y" }}</strong> — <a href="{{ post.url | relative_url }}">{{ post.title }}</a></li>
    {% else %}
    <li>Пока нет записей в играх.</li>
  {% endfor %}
</ul>
 ***
### Контакты:    [facebook](https://www.facebook.com/profile.php?id=100087457504302)

