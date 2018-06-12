# README #

Здесь реализован полный деплой проекта состоящего из 1-го backend и 1-го frontend репозиториев. В частности идёт
- клонирование репозиториев и переключение на нужную ветку/коммит
- сборка докер образов и пуш их в репозиторий
- создание нового экземпляра приложения (создание пользователя, конфигурация самого приложения, конфигурация корневого
веб-сервера - здесь nginx и т.д.)
- запуск приожения


### quick start
* cd ansible
* make configure
* make INVENTORY=develop.ini clone-build-push-deploy


### start
* cd ansible
* make configure
* make INVENTORY=develop.ini PROJECT=my-project TAG=latest BRANCH=develop clone-build-push-deploy
