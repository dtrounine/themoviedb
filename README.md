# Задание - Список фильмов

## Цель

Написать приложение, состоящее из одного экрана со списком популярных фильмов, используя The Movie DB API [https://www.themoviedb.org/](https://www.themoviedb.org/). Документация по API доступна здесь: [https://developers.themoviedb.org/3/getting-started](https://developers.themoviedb.org/3/getting-started). 

* Загрузка данных в фоновом потоке (`AsyncTaskLoader`, `Loader` и.т.п)
* Отображение данных в `RecycleView`
* Выполнение запроса при помощи `HttpURLConnection`
* Разбор ответа от API при помощи `JsonReader` или `JSONObject`
* Отображение индикатора загрузки и ошибок.

<img src="https://github.com/dtrounine/themoviedb/blob/master/demo_screenshot.png" width="360px"/>

## Задание

* Зарегистрироваться на https://www.themoviedb.org/ и получить ключ API, прописать ключ в классе `TmdbApi` вместо дефолтного.
* В методе `TmdbApi.getPopularMoviesRequest` написать код, который создает запрос популярных фильмов, как описано в документации: https://developers.themoviedb.org/3/movies/get-popular-movies (для начала можно запрашивать только первую страницу результата). В качестве параметра запроса должен передаваться язык пользователя (системный).
* Написать код парсера, который разбирает ответ от API и возвращает результат типа `List<Movie>` (класс `Movie` уже есть в коде задания).
* Написать код, отвечающий за асинхронную загрузку данных в фоновом потоке
* Написать код и верстку основного экрана в классе `PopularMoviesActivity`, который:
  * При старте показывает индикатор процесса загрузки
  * После завершения загрузки показывает список фильмов в `RecyclerView` (нужно будет написать адаптер)
  * В случае ошибки показывает сообщение об ошибке
  * В случае отсутствия соединения показывает сообщение об отсутствии соединения
* Сделать так, чтобы при прокрутке списка вниз загружались следующие страницы списка фильмов.

Для отображения изображений постеров можно использовать библиотеку Fresco (http://frescolib.org/index.html), зависимость на которую уже добавлена в код задания. Из этой библиотеки понадобится один класс `SimpleDraweeView`, описание здесь: [http://frescolib.org/docs/getting-started.html](http://frescolib.org/docs/getting-started.html). 

## Требования

* При повороте экрана НЕ должна происходить повторная загрузка данных
* Долгие операции НЕ должны выполняться в UI потоке
* Во время загрузки должен показывать индикатор процесса загрузки
* В случае ошибок или отсутсвия соединения должны показываться адекватные сообщения об ошибках
* Приложение должно нормально выдерживать поворот экрана (с сохранением контента и без лишних действий)
* Элемент списка фильмов должен содержать как минимум: изображение постера с правильными пропорциями, название и описание фильма на языке пользователя.
* При необходимости верстка должна быть адаптирована к ландшафтной ориентации экрана (например, если постер в портретной ориентации может занимать всю ширину экрана, то в ландшафтной ориентации это недопустимо)
