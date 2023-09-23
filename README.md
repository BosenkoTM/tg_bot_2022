# telegram-bot-in-docker 
___
Благодаря этому шаблону вы можете ближе познакомиться с установкой 
своих Telegram ботов в контейнеры.

# Инструкция
___
:information_source: **Чтобы начать вы должны быть зарегистрованы в Docker Hub.** 

Вводим команду ниже и указываем свои данные (login:password) для авторизации.
    
    docker login

Создаем образ (предварительно замените значения image в docker-compose.yml)

    docker-compose build

Загружаем наш созданный образ в Docker Hub

    docker-compose push

Чтобы стянуть наш образ на удаленный сервер вводим следующее

    docker pull your_username_docker_hub/image

Запускаем наш docker. 
Флаг -d означает, что запускаем наш контейнер в [detach режиме](https://docs.docker.com/engine/reference/run/#detached--d), благодаря этому мы сразу получаем управление после запуска этой команды. 

    docker run -d your_username_docker_hub/image

Выводим последний контейнер, который мы запустили и забираем CONTAINER ID.

    docker ps -l

Чтобы чекать логи 

    docker logs -f CONTAINER_ID

Отлично! Всё готово!

# Плюсы контейнеризации docker
___
### Абстрагирование приложение  от хоста
Задумка в контейнера – полная стандартизация. Контейнер соединяется с хостом определенным интерфейсом, контейнеризорованное приложение не зависит от архитектуры или ресурсов хоста. Для хоста же контейнер некий «черный ящик», не имеет значение что в нем.

### Масштабирование
В продолжение преимущества абстрагирования приложения от хоста, является возможность простого и линейного маштабирования. Т.е на одной машине может быть запущено несколько контейнеров. В то же время они могут быть запущены и на тестовом сервере. В продуктивной среде их также можно масштабировать.

### Управление версиями и зависимостями
Благодаря использованию контейнеров, разработчик привязывает все компоненты и зависимости к приложению, что позволяет работать как цельным объектом. На  хосте не нужны установки дополнительных компонентов или зависимостей для запуска приложения, которое находится внутри контейнера, достаточно возможности запуска докер контейнера.

### Изолирование среды
Изоляция в контейнерах не достигает такого же уровня как в виртуализации, но тем не менее обладает легкой средой выполнения и относится к изоляции на уровне процессов. При этом контейнер работает на том же самом ядре, что позвоялет ему очень быстро запускаться. Запуск сотни контейнеров на рабочей машине не будет проблемой.

### Использование слоев
Легкость контейнеров заключается в их послойности. То есть когда несколько контейнеров используют одинаковый слой, они могут им пользоваться без дублирования, это минимизирует использование дискового пространства.

### Компоновка
Возможность написания задания конкретных действий для создания нового образа. Т.е. настройки среды можно описать как код и сохранять в системе контроля версий.

# Недостатки контейнеров докер
___
### Тонкая настройка
При большой масштабируемости и нагрузке необходимо очень четкая и качественная настройка систем.

### Обратная совместимость
Докер быстро развивается и одним из минусов такого развития бывает ограниченная обратная совместимость по некоторым направлениям.

### Удаление
Процесс удаления докер контейнеров занимает большое количество времени и требует немалого количества операций ввод-вывод.

### Производительность
Дополнительные надстройки над системой в любом случае приводят к увеличению нагрузки и расходу ресурсов.

### Архитектура
Контейнеризация являет собой надстройку над ОС, тем самым усложняя реализацию задачи.

### Поддержка
Для поддержки и сопровождения докер контейнеров необходимо не только навыки системного администратора, но и хорошие знания docker.

# Источник и полезные материалы
___
+ [Полное практическое руководство по Docker: с нуля до кластера на AWS](https://habr.com/ru/post/310460/)
+ [Изучаем Docker, часть 1: основы](https://habr.com/ru/company/ruvds/blog/438796/)
+ [Изучаем Docker, часть 2: термины и концепции](https://habr.com/ru/company/ruvds/blog/439978/)
