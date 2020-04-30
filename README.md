# eshenko_microservices
eshenko microservices repository

Домашнее задание 22
===================

- установлен helm
- установлен tiller
- созданы chart'ы
- добавлен новый пул в кластер
- установлен Gitlab в Kubernetes
- настроены пайплайны для билда, создания окружений фича бранчей, созданы окружения production и staging

Домашнее задание 21
===================

- создан LoadBalancer в GCE
- создан Ingress и настроено взаимодействие по 80му порту
- созданы сертификаты
- настроен Ingress для работы по https
- настроено сетевое взаимодействие между базой и сервисами post и comment
- создан отдельный диск для хранения данных БД и настроено взаимодействие с ним
- создано отдельное хранилище и настроено взаимодействие с ним
- настроена работа с динамическим хранилищем

Домашнее задание 20
===================

- установлен Minikube (c VirtualBox)
- созданы конфигурационный файла деплоя, сервисов и неймспеса
- запущен и проверен локальный кластер Kubernetes
- создан и настроен класстер Kubernetes в GCP
- развернуто приложение с использованием GKE

Домашнее задание 19
===================

- выполнена установка и настройка kubernetes по мануалу The Hard Way
- проверен запуск с помощью файлов *-deployment.yml (kubectl apply -f <filename>)

Домашнее задание 18
===================

- установлен и настроен стек EFK
- настроен сбор и отображение структурированных логов
- настроен сбор и отображение неструктурированных логов
- настроен сервис трейсинга Zipkin

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
