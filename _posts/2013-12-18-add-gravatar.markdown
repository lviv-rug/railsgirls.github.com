---
layout: default
title: Використання Gravatar
permalink: gravatar
---

# Використання Gravatar

*Created by Catherine Jones*

*Переклад українською - Bogdan Varshchuk, [@g3d](https://github.com/g3d)*

*Редагування та оновлення -  Aleksandra Klochko, [@aleksacastle](https://github.com/aleksacastle)*

Ця iнструкцiя передбачає, що у вас вже [створений додаток Ideas](http://guides.railsgirls.com/app/) та додана аутентифікація користувачів через [Devise](http://guides.railsgirls.com/devise/).

### Важливо!

Необхідно бути зареєстрованим на Gravatar та мати доступ до мейлу, який використовувався при реєстрації. Якщо у вас немає аккаунту - перейдіть на [gravatar.com](http://en.gravatar.com/) та зареєструйтеся.

## *1.* Додамо Gravtastic gem

Відкриваємо gemfile та під `devise` gem додамо

{% highlight ruby %}
gem 'gravtastic'
{% endhighlight %}

у терміналі виконуємо:

{% highlight sh %}
bundle install
{% endhighlight %}

Ми встановили gravtastic gem. Не забудь перезапустити rails сервер.

## *2.* Встановлення Gravatar

Відкриваємо `app/models/user.rb`, та додаємо

{% highlight ruby %}
include Gravtastic
gravtastic
{% endhighlight %}

одразу ж після першого рядку.

## *3.* Налаштування Gravatar

Відкриємо `app/views/layouts/application.html.erb` та в секції

{% highlight erb %}
<% if user_signed_in? %>
{% endhighlight %}

але перед

{% highlight erb %}
<% else %>
{% endhighlight %}

додамо

{% highlight erb %}
<%= image_tag current_user.gravatar_url %>
{% endhighlight %}

Тепер відкрий у браузері додаток та увійди в свій профайл використовуючи той мейл, який пов'язаний із Gravatar. Ти побачиш свій Gravatar.
