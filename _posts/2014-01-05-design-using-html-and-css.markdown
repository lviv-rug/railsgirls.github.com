---
layout: default
title: Add design to your App with HTML and CSS
permalink: design-html-css
---

## *1.* Дизайн заголовка

Добавить строки в конец файла `app/assets/stylesheets/application.css`:

{% highlight css %}
.navbar {
  min-height: 38px;
  background-color: #f55e55;
}
{% endhighlight %}


Обновите страницу и проверьте изменения. Вы можете изменить цвет и шрифт заголовка по своему вкусу. Ссылка на коды цвета [http://color.uisdc.com/](http://color.uisdc.com/).

После этого, поместите эти строки внизу файла:

{% highlight css %}
.navbar a.brand { font-size: 18px; }
.navbar a.brand:hover {
 color: #fff;
 background-color: transparent;
 text-decoration: none;
}
{% endhighlight %}


**Тренер:** объясните про 4-е состояния ссылки


## *2.* Дизайн таблицы

Мы используем twitter [Bootstrap](http://getbootstrap.com/) для дизайна нашей таблицы. Найдите эти строки в файле `app/views/ideas/index.html.erb` и замените:

{% highlight html %}
<table>
{% endhighlight %}
с
{% highlight html %}
<table class="table">
{% endhighlight %}

Измените размер изображения, дополнив код между строк

{% highlight erb %}
<%= image_tag(idea.picture_url, :width => 600) if idea.picture.present? %>
{% endhighlight %}


попробуйте изменить ширину и посмотрите, что произойдет

Добавьте строки в конец файла `app/assets/stylesheets/ideas.css.scss`:

{% highlight css %}
.container a:hover {
  color: #f55e55;
  text-decoration: none;
  background-color: rgba(255, 255, 255, 0);
}
{% endhighlight %}


Попробуйте добавить фоновый стиль используя  `background-image`, ссылка на паттерны [http://subtlepatterns.com/](http://subtlepatterns.com/)

## *3.*Добавление стилей для подвала

Добавьте строки в конец файла `app/assets/stylesheets/application.css`:

{% highlight css %}
footer {
  background-color: #ebebeb;
  padding: 30px 0;
}
{% endhighlight %}

попробуйте добавить больше разных стилей в подвал.


## *4.* Добавление стилей для кнопки

Откройте [http://localhost:3000/ideas/new](http://localhost:3000/ideas/new) и найдите кнопку Create Idea.

Добавьте строки в конец файла `app/assets/stylesheets/ideas.css.scss`


{% highlight css %}
.container input[type="submit"] {
  height: 30px;
  font-size: 13px;
  background-color: #f55e55;
  border: none;
  color: #fff;
}
{% endhighlight %}


**Тренер:** объясните, как использовать рамки в css, попробуйте изменить стиль кнопки, например закруглить края, добавить тень или цвет и т.д.
