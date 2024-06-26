---
layout: post
title: Как создать блог на GitHub Pages
---

Поставил я себе задачу написать блог и разместить его в публичном доступе. После небольшого исследования всплыла одна проблема, что весь материал который я буду публиковать будет лежать где то в БД сервиса а сам блог мне придется конфигурировать на каком то генерторе сайтов. И если вы начнете копать в сторону лучшего решения для небольшого блога, то одним из вариантов будет использование GitHub Pages и Jekyll. Сегодня и поговорим о нем.

### Что такое GitHub Pages и Jekyll
[Github Pages](https://pages.github.com/) это бесплатный хостинг для статических файлов, который предоставляет GitHub. В этой статье не буду углубляться в технические детали а просто расскажу один из простейших способов запустить блог на GitHub Pages c использованием Jekyll. 

[Jekyll](https://jekyllrb.com/) это генератор статических сайтов который на вход принимает даные а на выходе получем набор HTML файлов. Jekyll поддерживает множество различных форматов входных данных, таких как Markdown, HTML, CSS, YAML, JSON, XML и другие. Автор такой идеи [Tom Preston-Werner](https://en.wikipedia.org/wiki/Tom_Preston-Werner) один из сооснователей GitHub.

### Создаем блог из шаблона Jekyll Now
Cамый быстрый и простой спосб запустить Jekyll на GitHub Pages это сделать вилку проекта. Вам не нужно будет настраивать ничего, просто форкните репозиторий и все будет работать из коробки.
1. Сделайте форк репозитория [Jekyll Now Repository](https://github.com/barryclark/jekyll-now)    
2. Переименуйте репозиторий в username.github.io
> Где username это ваш логин на GitHub. Для примера, если ваш логин на GitHub `zaitolzhas`, то название репозитория должно быть `zaitolzhas.github.io`
3. Включите Github pages в настройках репозитория
![alt text](../images/Enable-github-pages.jpg)
4. Перейдите по адресу https://zaitolzhas.github.io

### Добавляем первый посты в блог
Все, теперь готова платформа для запуска вашего блога. Для добавления новых постов просто создайте новый файл в папке `_posts` и запуште его в репозиторий. При создании нового файла нужно соблюдать правила что бы Jekyll все правильно собрал и ничего не пропустил: 
1. Посты должны быть в формате [Markdown](https://guides.github.com/features/mastering-markdown/) 
2. Имя файла должно быть в формате `год-месяц-день-название-поста.md`
3. В начале файла должен быть указан `layout` и `title`

Добавим новый пост в блог и посмотрим как это выглядит на сайте:
1. Создаем новый файл в папке `_posts`
    - Перейдите в папку `_posts`
    - Кликните на кнопку "Add file" и выберите "Create new file"
2. Введите имя файла в формате 2024-5-22-first-post.md
    ![alt text](../images/Create-new-post.jpg)
3. Вставьте следующий код в файл
{% highlight markdown %}
---
layout: post
title: Мой первый пост в блоге
---

Это тестовый пост, который я добавил в блог. Не знаю что писать, но это не важно. Главное что все рабоатает.

Можно писать булет поинты.
- Первый пункт
- Второй пункт
- Третий пункт

Markdown очень удобная штука, все ньюансы можно посмотреть [здесь](https://guides.github.com/features/mastering-markdown/)
{% endhighlight %}

4\. Нажмите на кнопку `Commit changes`
5\. Передите во вкладку `Actions` и дождитесь окончания сборки
6\. Ваш пост готов, перейдите по ссылке https://username.github.io/

Для изменения внешнего вида блога, вам нужно будет изменить файлы в папке _layouts и _includes. 
Для изменения стилей, измените файлы в папке _sass.

