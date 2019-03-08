---
layout: default
title: Мініатюри для списку ідей
permalink: thumbnails
---

# Зменшення зображень з Carrierwave

*Created by Miha Filej, [@mfilej](https://twitter.com/mfilej)*
*Переклад українською - Nastia, [@aladan](https://github.com/aladan)*
*Редагування та оновлення -  Aleksandra Klochko, [@aleksacastle](https://github.com/aleksacastle)*
## *1.*Встановлення ImageMagick

* OS X: виконай команду `brew install imagemagick`. Якщо в тебе немає команди `brew` - [встанови Homebrew тут][in-homebrew].
* Windows: завантаж та запусти [ImageMagick встановлювач][im-win] (використай перший лінк для завантаження).
Пiд час встановлення, вибери пункт legacy binaries.
* Linux: На Ubuntu чи Debian, виконай `sudo apt-get install imagemagick`.
Для інших дистрибутивів, замість `apt-get`, використовуй відповідний менеджер пакетів.

  [im-win]: http://www.imagemagick.org/script/download.php#windows
  [in-homebrew]: http://mxcl.github.io/homebrew/

**Ментор:** Що таке ImageMagick та як він відрізняється від бібліотек(gems), котрі ми використовували раніше?

Відкрий `Gemfile` в проекті та додай

{% highlight ruby %}
gem 'mini_magick', '3.8.0'
{% endhighlight %}

під стрічкою

{% highlight ruby %}
gem 'carrierwave'
{% endhighlight %}

У терміналі виконай:

{% highlight sh %}
bundle install
{% endhighlight %}

## *2.*Створюємо мініатюри при завантаженнi зображення

Відкрий `app/uploaders/picture_uploader.rb` та знайди таку стрічку:

{% highlight ruby %}
  # include CarrierWave::MiniMagick
{% endhighlight %}

Видали знак `#`.

**Ментор:** Поясни ідею коментарів у коді.

Під стрічкою, яку щойно змінили, додай:

{% highlight ruby %}
version :thumb do
  process :resize_to_fill => [50, 50]
end
{% endhighlight %}

Відтепер завантажені зображення змінюватимуть свій розмір. Aле ті, які ми вже додали не зміняться.
Тож відредагуй якусь ідею, ще раз додавши зображення.

## *3.*Відображення мініатюр

Щоб перевірити, чи завантажене зображення змінило свій розмір, відкрий
`app/views/ideas/index.html.erb`. Заміни стрічку

{% highlight erb %}
<%= image_tag idea.picture_url, width: '100%' if idea.picture.present? %>
{% endhighlight %}

на

{% highlight erb %}
<%= image_tag idea.picture_url(:thumb) if idea.picture.present? %>
{% endhighlight %}

Подивися на список ідей d браузері, щоб побачити чи є там мініатюри.

**Ментор:** Поясни, що робить визначення ширини картинки в HTML вкінці 3 пункту,
та чим воно відрізняється від зміни розміру картинок на сервері.
