## Common place to Russian translators

This page has been made to correct terms of translating, and synchronize
our work.

Working languages: Russian, English.

------------------------------------------------------------------------

Эта страница предназначена для обсуждения терминов и корректировки
работы переводчиков.

Рабочие языки: русский, английский.

## Советы по переводу

Внимательно прочитайте [общие советы
переводчикам](Translating "wikilink").

- Перевод производится здесь, в вики, а также редактированием po-файла.
  Программа для редактирования этих файлов называется Poedit, и доступна
  . Прямое редактирование файла крайне нежелательно, ибо способно
  нарушить целостность файла.
- В вики редактируются большие тексты, на которые в исходниках игры
  проставлены ссылки (txt_something). Редактирование этих текстов в
  po-файле запрещено!
- При переводах/правках используйте кошерные знаки препинания:

«, », —, „, ”, …

- Поставьте себе спеллчекеры!
- В текстах переводов **не используйте** вики-форматирования! Особенно
  списки — синхронизатор не понимает этого синтаксиса, и обрывает текст.
- Обращение «вы» в середине предложения пишется с маленькой буквы.
  - Местоимения Вы и Ваш пишутся с прописной (большой) буквы при
    обращении к одному лицу; при обращении к нескольким лицам следует
    писать вы и ваш со строчной буквы. - несколько словарей и ГОСТов
    указывают обратное. Рекомендую
    прислушаться--[Sotnikov123](User:Sotnikov123 "wikilink") 08:12, 16
    February 2011 (CET)
  - Ну и, чтоб не погрязать в переделывании Вы-\>вы-\>Вы, на сегодня это
    слово выкидываю из текста отовсюду. Тексты становятся менее
    канцелярскими надо сказать, за сухими отчётами чувствуется коллектив
    :)
- Авторы писем обращаются друг к другу однообразно. Я сделал так:
  - Командующий, (дальше текст через пробел)
  - С уважением, ком. Наварре.
  - Командующий, (+2 перевода строки)
  - Д-р Коннор.
  - Доброе утро, командующий. (+2 перевода строки, не забываем, что
    она - ЖЕНЩИНА)
  - Всего хорошего, полковник Фалькланд. (в две строки, перенос после
    запятой)

## Советы по компиляции

Компиляция под **Fedora13 (RFRemix)** Переставил ОС и столкнулся с
необходимостью докачивать пакеты для компиляции игры. Процесс простой,
но весьма нудный - необходимо запускать ./compile и смотреть на что он
ругается. Ставил систему с live-cd, так что она практически голая,
потребовались следующие пакеты:

Раз уж начал - надо доводить до логического конца (скопипастено из
SuSe):

**Fedora**

### Prerequisites

Note that where there are packages that depend on the devel packages,
they are not mentioned here, as *yum* will select them for install
automatically. Use *yum* to install (if you haven't already):

    # yum install make svn gcc zlib-devel libcurl-devel libjpeg-devel libpng-devel \
    SDL-devel SDL_image-devel SDL_mixer-devel SDL_ttf-devel SDL_Pango-devel libtheora-devel \
    gtk2-devel gtkglext-devel gtksourceview2-devel glib2-devel libxml-devel gcc-c++ openal-soft-devel gettext

### Download the latest SVN version

    # mkdir ufoai
    # cd ufoai
    # svn co {{https|ufoai.svn.sourceforge.net/svnroot/ufoai/ufoai/trunk}}
    # cd trunk

### Compile

    # ./configure
    # make
    # make lang

Now compile the maps:

    # make maps

WARNING: This process might take some time (**even a couple of hours**
or so!)(Or All Day!).


Здесь хотелось бы добавить, что раз процесс долгий, то можно и одним
махом ввести:

<!-- -->

    # ./configure
    # make
    # make lang pk3 maps install

### Running

Run the game

    # ./ufo

See [debugging](debugging "wikilink") if you happen to find a bug.

### Конец

Про автоупдейт не разбирался - надо ли оно? Я всё сносил и заливал
заново :) И не до конца понял что такое pk3 файлы и необходимость *make
install*

yum install git gcc make git remote add -t master origin
<git://ufoai.git.sourceforge.net/gitroot/ufoai/ufoai> git fetch --depth
1 git checkout -t origin/master

yum install xvidcore-devel yum install libtheora-devel yum install
binutils-devel yum install CUnit-devel yum install libcurl-devel yum
install SDL-devel yum install libvorbis-devel yum install
SDL_mixer-devel yum install SDL_ttf-devel yum install SDL_image-devel
yum install libjpeg-turbo-devel yum install libpng-devel yum install
gettext-devel?

yum install xvidcore-devel libtheora-devel binutils-devel CUnit-devel
libcurl-devel SDL-devel libvorbis-devel SDL_mixer-devel SDL_ttf-devel
SDL_image-devel libjpeg-turbo-devel libpng-devel gettext -devel?

make make lang make maps make install

pust' poka zdes' polejit. --[Sotnikov123](User:Sotnikov123 "wikilink")
06:22, 19 February 2011 (CET)

[Category:Translating](Category:Translating "wikilink")