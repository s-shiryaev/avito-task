# Создать JSON API для сайта объявлений
Необходимо создать сервис для хранения и подачи объявлений. Объявления должны храниться в базе данных. Сервис должен предоставлять API, работающее поверх HTTP в формате JSON.

Реализованные методы:
* POST /item/create/ - создание объявления
* GET /item/[id] - получение конкретного объявления
* GET /items - получение списка объявлений

### Метод получения списка объявлений
* Реализована пагинация, количество объявлений на странице задается параметром `resultsOnPage` (по умолчанию 10)
* Присутсвует возможность сортировки с помощью параметра `orderBy`. Возможна сортировка по нескольким полям (например `-price+created`, `asc_price,desc_name` и т.д.)

### Метод получения конкретного объявления
* Возвращаемые поля: `name`, `price`, `mainImgLink`, `id`
* Опциональные поля (можно запросить, передав их названия в параметре `fields`): `description`, `imgLinks`, `imgLinksArr`, `created`

### Метод создания объявления
* Принимает поля: название, описание, несколько ссылок на фотографии(в виде строки), цена. 
Реализована валидация полей с возвращением ошибок.
* Возвращает ID созданного объявления и код результата (ошибка или успех)

### Усложнения
Выполненные усложнения
* Написаны юнит тесты
* Контейнеризация – возможность поднять проект с помощью `docker-compose up`
* кеширование – для увеличения скорости ответа от сервера добавлено кеширование (Redis)
