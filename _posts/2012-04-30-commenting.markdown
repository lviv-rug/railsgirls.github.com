---
layout: default
title: Функціональність роботи з коментарями для додатку Rails Girls
permalink: commenting
---
# Додавання коментарів до Rails Girls додатку
*Created by Janika Liiv, [@janikaliiv](https://twitter.com/janikaliiv)*

*Переклад українською - Bogdan Varshchuk, [@g3d](https://github.com/g3d)*

*Редагування та оновлення -  Aleksandra Klochko, [@aleksacastle](https://github.com/aleksacastle)*

Зараз ми реалізуємо можливість додавання *коментарів* до *ідей* в твоєму першому Rails додатку.

Всі інструкції з початкового налаштування середовища Rails та побудови основної функціональності додатка можна знайти [тут](/app).

## *1.* Scaffold для коментарів

Потрібно створити scaffold для сутності 'коментар', що містить: ім'я коментатора, власне коментар (текст), ну і посилання на ідею, якої стосується даний коментар (`idea_id`).
{% highlight sh %}
rails g scaffold comment user_name:string body:text idea_id:integer
{% endhighlight %}
Ця команда створить, зокрема, сценарій *міграції*, що "повідомить" базу даних про те, що створюється нова таблиця з коментарями. Цю міграцію треба виконати, запустивши в терміналі команду
{% highlight sh %}
rails db:migrate
{% endhighlight %}

## *2.* Зв'язки між моделями

Ще треба зробити так, щоб Rails додаток знав про зв'язки між моделями (ідеї та коментарів).
До однієї ідеї можна додати декілька коментарів, отже, в даному випадку буде співвідношення один-до-багатьох (одна ідея - багато коментарів).

Відкрий файл `app/models/idea.rb` та одразу після рядка
{% highlight ruby %}
class Idea < ApplicationRecord
{% endhighlight %}
додай
{% highlight ruby %}
has_many :comments
{% endhighlight %}

Моделі 'коментар' також потрібно вказати, що вона належить до 'ідеї' (звісно, що так - коментар не може існувати сам по собі). Отже, відкрий файл `app/models/comment.rb` та після рядка
{% highlight ruby %}
class Comment < ApplicationRecord
{% endhighlight %}

додай
{% highlight ruby %}
belongs_to :idea
{% endhighlight %}

## *3.* Форма для додавання нового коментаря та відображення коментарів до ідеї

Відкрий файл `app/views/ideas/show.html.erb` та після `image_tag`
{% highlight erb %}
<%= image_tag(@idea.picture_url, :width => 600) if @idea.picture.present? %>
{% endhighlight %}

додай
{% highlight erb %}
<h3>Comments</h3>
<% @comments.each do |comment| %>
  <div>
    <strong><%= comment.user_name %></strong>
    <br>
    <p><%= comment.body %></p>
    <p><%= link_to 'Delete', comment_path(comment), method: :delete, data: { confirm: 'Are you sure?' } %></p>
  </div>
<% end %>
<%= render partial: 'comments/form', locals: { comment: @comment } %>
{% endhighlight %}

У контролері `app/controllers/ideas_controller.rb` до методу 'show' додай цей фрагмент коду:
{% highlight ruby %}
@comments = @idea.comments.all
@comment = @idea.comments.build
{% endhighlight %}

Також відкрий файл `app/views/comments/_form.html.erb` та після
{% highlight erb %}
  <div class="field">
    <%= form.label :body %><br>
    <%= form.text_area :body, id: :comment_body %>
  </div>
{% endhighlight %}

додай рядок
{% highlight erb %}
<%= form.hidden_field :idea_id %>
{% endhighlight %}

і ще видали кілька зайвих рядків:
{% highlight erb %}
<div class="field">
  <%= form.label :idea_id %><br>
  <%= form.number_field :idea_id, id: :comment_idea_id %>
</div>
{% endhighlight %}

Це все. Тепер поряд з самою ідеєю можна побачити коментарі до неї, а також форму для створення нових коментарів та видалення існуючих.
Вітаю, ще один важливий крок зроблено!
