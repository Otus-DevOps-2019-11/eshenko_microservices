# eshenko_microservices
eshenko microservices repository

Домашнее задание 17
===================

- настроен мониторинг docker контейнеров с помощью cAdvisor
- настроено отображение метрик с помощью Grafana
- настроены дашбоарды и графики в Grafana
- настроен алертинг через Alertmanager в Slack

Ссылки на образы:
https://hub.docker.com/repository/docker/eshenkoao/prometheus
https://hub.docker.com/repository/docker/eshenkoao/post
https://hub.docker.com/repository/docker/eshenkoao/comment
https://hub.docker.com/repository/docker/eshenkoao/ui
https://hub.docker.com/repository/docker/eshenkoao/alertmanager

Домашнее задание 16
===================

- Запущены микросервисы и Prometheus на новом инстансе GCP
- Настроен мониторинг микросервисов
- Настроен мониторинг сервера с использованием prom/node-exporter

Ссылки на образы:
https://hub.docker.com/repository/docker/eshenkoao/prometheus
https://hub.docker.com/repository/docker/eshenkoao/post
https://hub.docker.com/repository/docker/eshenkoao/comment
https://hub.docker.com/repository/docker/eshenkoao/ui

Домашнее задание 15
===================

- Создан новый инстанс в GCP
- Установлен Gitlab
- Созданы группа и проект
- Создан файл .gitlab-ci.yml с описание окружений
- Создан и зарегистрирован runner
- Протестирована работа пайплайна


Домашнее задание 14
===================

- Изучена работа с сетью в Docker
- Изучена работа с docker-compose
- Создан файл docker-compose
- docker-compose параметризован, создан файл .env и .env.example
- Задано базовое имя проекта
- Создан override файл, через который puma запускается в дебаг режиме, а также подключен volume для изменения кодовой базы без пересборки образа


Домашнее задание 13
===================

- Созданы файлы сборки Dockerfile для микросервисов
- Создана сеть reddit
- Запущены контейнеры с алиасами и проверена работоспособность контейнеров
- Запущены контейнеры с другими алиасами без пересборки образов

docker run -d --network=reddit --network-alias=post_db_1 --network-alias=comment_db_1 mongo:latest
docker run -d --network=reddit --network-alias=post_1 --env POST_DATABASE_HOST=post_db_1 eshenkoao/post:1.0
docker run -d --network=reddit --network-alias=comment_1 --env COMMENT_DATABASE_HOST=comment_db_1 eshenkoao/comment:1.0
docker run -d --network=reddit -p 9292:9292 --env POST_SERVICE_HOST=post_1 --env COMMENT_SERVICE_HOST=comment_1 eshenkoao/ui:2.0

- Созданы файлы сборки Dockerfile.1 для сборки на базе alpine микросервисов comment и ui



Домашнее задание 12
===================

- Установлены docker и docker-machine
- Создан новый проект docker в GCP
- Создан инстанс docker-host в GCP и спользованием docker-machine
- Создан свой образ
- Загружен свой образ на Docker Hub (docker push eshenkoao/otus-reddit:tagname)
