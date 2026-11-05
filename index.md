---
layout: default
title: Economy
---

<!-- Основной контейнер Flexbox, разделяющий страницу на две колонки -->
<div style="display: flex; flex-wrap: wrap; gap: 30px; align-items: flex-start; font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;">

  <!-- ========================================== -->
  <!-- ЛЕВАЯ КОЛОНКА: ЛЕНТА И ПУБЛИКАЦИИ (70%)    -->
  <!-- ========================================== -->
  <div style="flex: 3; min-width: 320px;">
    
    ## [КАК НАМ ОБУСТРОИТЬ ЭКОНОМИКУ — ретро](docs/how-arrange-our-economy.html)

    ### [КАК РАЗРУШИТЬ ЭКОНОМИКУ?](docs/how-to-destroy-an-economy.html)

    #### [Тринадцать лет спустя](docs/thirteen-years-later.html)

    ## [Разделить чистые и грязные деньги](docs/separate-clean-money-from-dirty-money.html)

    ## [КАК ОБУСТРОИТЬ ГОСУДАРСТВЕННЫЕ ЗАКУПКИ](docs/how-to-organize-public-procurement.html)

    <blockquote style="margin: 20px 0; padding: 10px 20px; background: #f0f7ff; border-left: 5px solid #0066cc; font-style: italic; color: #444;">
      В государственных закупках ПРОЦЕДУРА — ничто, ЦЕНА и КАЧЕСТВО — всё.
    </blockquote>

    <hr style="border: 0; border-top: 1px solid #eee; margin: 30px 0;">

    <h3 style="color: #222;">✍️ Новые записи в блоге (Общие)</h3>

    {% assign count = 0 %}
    {% for post in site.posts %}
      {% unless post.path contains "_posts/games/" %}
        <div style="margin-bottom: 15px; line-height: 1.5;">
          <strong>{{ post.date | date: "%d.%m.%Y" }}</strong> — <a href="{{ post.url | relative_url }}" style="font-weight: bold; color: #0066cc; text-decoration: none;">{{ post.title }}</a>
          <div style="font-size: 14px; color: #555; margin-top: 2px; padding-left: 20px;">{{ post.excerpt }}</div>
        </div>
        {% assign count = count | plus: 1 %}
        {% if count == 3 %}{% break %}{% endif %}
      {% endunless %}
    {% endfor %}

    <!-- ========================================== -->
    <!-- АРХИВ ПО МЕСЯЦАМ С АВТО-РАСКРЫТИЕМ НОЯБРЯ -->
    <!-- ========================================== -->
    {% if site.posts.size > 3 %}
    <details style="margin-top: 20px; cursor: pointer; background: #fafafa; padding: 15px; border-radius: 6px; border: 1px solid #e5e5e5;">
      <summary style="font-weight: bold; color: #0066cc; font-size: 16px;">📂 Показать более старые общие записи...</summary>
      
      {% assign skip_count = 0 %}
      {% assign current_month = "" %}
      {% assign inside_details = false %}
      {% capture real_current_month %}{{ "now" | date: "%m.%Y" }}{% endcapture %}

      {% for post in site.posts %}
        {% unless post.path contains "_posts/games/" %}
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
              
              <details {{ open_attribute }} style="margin-left: 10px; margin-top: 12px; cursor: pointer;">
                <summary style="font-weight: bold; color: #333; font-size: 15px; margin-bottom: 8px;">📅 {{ month_name }} {{ post.date | date: "%Y" }} г.</summary>
                <ul style="list-style-type: disc; padding-left: 20px; margin-top: 5px; line-height: 1.6;">
              
              {% assign current_month = post_month %}
              {% assign inside_details = true %}
            {% endif %}

            <li style="margin-bottom: 6px;">
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

    <hr style="border: 0; border-top: 1px solid #eee; margin: 40px 0;">

    <!-- ТЕМАТИЧЕСКИЕ СЕКЦИИ ПОД ЛЕНТОЙ -->
    <h3 id="economy-section" style="color: #222;">Экономика Госзакупки Коррупция</h3>
    <ul style="list-style-type: disc; padding-left: 20px; line-height: 1.6;">
    {% assign has_economy = false %}
    {% for post in site.posts %}
      {% if post.path contains "_posts/economy/" %}
        {% assign has_economy = true %}
        <li><strong>{{ post.date | date: "%d.%m.%Y" }}</strong> — <a href="{{ post.url | relative_url }}">{{ post.title }}</a></li>
      {% endif %}
    {% endfor %}
    {% if has_economy == false %}
      <li style="color: #777;">Пока нет записей в этом разделе.</li>
    {% endif %}
    </ul>

    <h3 id="games-section" style="color: #222; margin-top: 30px;">Другие тематики</h3>
    <ul style="list-style-type: disc; padding-left: 20px; line-height: 1.6;">
    {% assign has_games = false %}
    {% for post in site.posts %}
      {% if post.path contains "_posts/games/" %}
        {% assign has_games = true %}
        <li><strong>{{ post.date | date: "%d.%m.%Y" }}</strong> — <a href="{{ post.url | relative_url }}">{{ post.title }}</a></li>
      {% endif %}
    {% endfor %}
    {% if has_games == false %}
      <li style="color: #777;">Пока нет записей в играх.</li>
    {% endif %}
    </ul>

  </div>

  <!-- ========================================== -->
  <!-- ПРАВАЯ КОЛОНКА: САЙДБАР (30%)              -->
  <!-- ========================================== -->
  <div style="flex: 1; min-width: 260px; background: #fdfdfd; padding: 22px; border-radius: 8px; border: 1px solid #eef0f2; box-shadow: 0 1px 3px rgba(0,0,0,0.02);">
    
    <!-- Визитка автора -->
    <div style="text-align: center; margin-bottom: 25px;">
      <div style="width: 70px; height: 70px; background: #0066cc; color: #fff; border-radius: 50%; display: flex; align-items: center; justify-content: center; margin: 0 auto 12px; font-size: 22px; font-weight: bold; letter-spacing: 1px;">ФС</div>
      <h3 style="margin: 0 0 6px 0; font-size: 18px; color: #222;">Фёдор Сочнев</h3>
      <p style="font-size: 13.5px; color: #666; margin: 0; line-height: 1.4;">Создаю цифровое «Я». Блог о ретроспективе экономики, механизмах госзакупок и стратегиях в покере.</p>
    </div>

    <hr style="border: 0; border-top: 1px solid #edf0f2; margin: 20px 0;">

    <!-- Быстрая навигация по темам -->
    <div style="margin-bottom: 25px;">
      <h4 style="margin: 0 0 12px 0; color: #333; font-size: 14px; text-transform: uppercase; letter-spacing: 0.5px;">📂 Категории</h4>
      <ul style="list-style: none; padding: 0; margin: 0; font-size: 14px; line-height: 1.8;">
        <li><a href="#economy-section" style="color: #0066cc; text-decoration: none;">📈 Экономика и законы</a></li>
        <li><a href="#economy-section" style="color: #0066cc; text-decoration: none;">📋 Государственные закупки</a></li>
        <li><a href="#games-section" style="color: #0066cc; text-decoration: none;">🃏 Покер и психология</a></li>
      </ul>
    </div>

    <hr style="border: 0; border-top: 1px solid #edf0f2; margin: 20px 0;">

    <!-- Статистика блога -->
    <div style="margin-bottom: 25px; background: #f7f9fa; padding: 12px; border-radius: 6px;">
      <h4 style="margin: 0 0 8px 0; color: #333; font-size: 14px; text-transform: uppercase; letter-spacing: 0.5px;">📊 Цифры</h4>
      <div style="font-size: 13px; color: #555;">
        Всего публикаций: <strong style="color: #222;">{{ site.posts.size }}</strong>
      </div>
    </div>

    <hr style="border: 0; border-top: 1px solid #edf0f2; margin: 20px 0;">

    <!-- Контакты -->
    <div>
      <h4 style="margin: 0 0 12px 0; color: #333; font-size: 14px; text-transform: uppercase; letter-spacing: 0.5px;">🤝 Контакты</h4>
      <div style="display: flex; gap: 12px; font-size: 14px;">
        <a href="https://github.com" target="_blank" style="color: #333; text-decoration: none; font-weight: 600; border-bottom: 1px dashed #333;">GitHub</a>
        <span style="color: #ccc;">|</span>
        <a href="https://facebook.com" target="_blank" style="color: #0066cc; text-decoration: none; font-weight: 600; border-bottom: 1px dashed #0066cc;">Facebook</a>
      </div>
    </div>

  </div>

</div>
