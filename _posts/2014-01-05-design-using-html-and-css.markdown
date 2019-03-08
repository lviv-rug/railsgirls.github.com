---
layout: default
title: Add design to your App with HTML and CSS
permalink: design-html-css
---

# Дизайн з Bootstrap
*Переклад українською - Anastasia, [@mrsOwl](https://github.com/mrsOwl)*

*Редагування та оновлення -  Aleksandra Klochko, [@aleksacastle](https://github.com/aleksacastle)*

## *1.*Дизайн заголовку

Додайте рядки в кінець файлу `app/assets/stylesheets/application.css`:

{% highlight css %}
.navbar {
  min-height: 38px;
  background-color: #f55e55;
}
{% endhighlight %}


Оновiть сторінку та перевірте зміни. Ви можете змінити колір і шрифт заголовка на свій смак. Посилання на коди кольору [http://color.uisdc.com/](http://color.uisdc.com/).

Після цього, помістіть наступні рядки внизу файлу:

{% highlight css %}
.navbar a.brand { font-size: 18px; }
.navbar a.brand:hover {
 color: #fff;
 background-color: transparent;
 text-decoration: none;
}
{% endhighlight %}


**Ментор:** Розкажи про чотири стани посилання

## *2.*Дизайн таблиці

Ми використовуємо twitter [Bootstrap](http://getbootstrap.com/) для дизайну нашої таблиці. Знайдіть ці рядки в файлі `app/views/ideas/index.html.erb`

{% highlight html %}
<table>
{% endhighlight %}
та замініть на
{% highlight html %}
<table class="table">
{% endhighlight %}

Змініть розмір зображення, додавши код між рядків

{% highlight erb %}
<%= image_tag(idea.picture_url, :width => 600) if idea.picture.present? %>
{% endhighlight %}


спробуйте змінити значення :width.

Додайте рядки в кінець файлу `app/assets/stylesheets/ideas.css.scss`:

{% highlight css %}
.container a:hover {
  color: #f55e55;
  text-decoration: none;
  background-color: rgba(255, 255, 255, 0);
}
{% endhighlight %}


Спробуйте додати фоновий стиль, використовуючи `background-image`, посилання на патерни [http://subtlepatterns.com/](http://subtlepatterns.com/).

## *3.*Додавання стилів до футеру

Додайте рядки в кінець файлу `app/assets/stylesheets/application.css`:


{% highlight css %}
footer {
  background-color: #ebebeb;
  padding: 30px 0;
}
{% endhighlight %}

спробуйте додати більше різних стилів до футеру.

## *4.*Додавання стилів до кнопки

Відкрийте [http://localhost:3000/ideas/new](http://localhost:3000/ideas/new) і знайдіть кнопку Create Idea.

Додайте рядки в кінець файлу `app/assets/stylesheets/ideas.css.scss`


{% highlight css %}
.container input[type="submit"] {
  height: 30px;
  font-size: 13px;
  background-color: #f55e55;
  border: none;
  color: #fff;
}
{% endhighlight %}


**Ментор:** поясни, як використовувати рамки в css, спробуйте змінити стиль кнопки - закруглити, додати тінь або колір і т.д.
