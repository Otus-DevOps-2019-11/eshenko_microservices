# eshenko_microservices
eshenko microservices repository

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
