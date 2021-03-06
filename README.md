# Задание 1 — найди ошибки

В этом репозитории находятся материалы тестового задания "Найди ошибки" для [14-й Школы разработки интерфейсов](https://academy.yandex.ru/events/frontend/shri_msk-2018-2) (осень 2018, Москва, Санкт-Петербург, Симферополь).

Для работы тестового приложения нужен Node.JS v9. В проекте используются [Yandex Maps API](https://tech.yandex.ru/maps/doc/jsapi/2.1/quick-start/index-docpage/) и [ChartJS](http://www.chartjs.org).

## Задание

Код содержит ошибки разной степени критичности. Некоторые из них — стилистические, а другие — даже не позволят вам запустить приложение. Вам нужно найти все ошибки и исправить их.

Пункты для самопроверки:

1. Приложение должно успешно запускаться.
1. По адресу http://localhost:9000 должна открываться карта с метками.
1. Должна правильно работать вся функциональность, перечисленная в условиях задания.
1. Не должно быть лишнего кода.
1. Все должно быть в едином codestyle.

## Запуск

```
npm i
npm start
```

При каждом запуске тестовые данные генерируются заново случайным образом.

## Ошибки (мог что-то упустить, но вся функциональность работает):

1. в стилях прописать html, body прописать высоту и ширину 100% и инлайн прописать диву #map ширину и высоту (появилась карта)
1. myMap.geoObjects.add(objectManager) для добавления станций (добавились, но находились они где-то около Ирана)
1. оказалось, перепутаны координаты в файле генерации (метки появились на территории Москвы)
1. попуп открывался, но после повторного открытия все глючило, проверка на открытость попупы- добавил objectManager.objects.balloon.open(objectId); перенес в условие if (!obj.properties.details) (попуп стал открываться, но был пустой)
1. objectManager.objects.getById(objectId).properties = data; добавил правильную передачу информации
1. в функции getDetailsContentLayout, поправил шаблон попупа на нужные переменые, передачу обьекта правильно скорректировал (стали появляться попупы, но не было графиков)
1. в файле chart.js настройки  borderColor backgroundColor при создания графика должны передавться как массив, и подправил настройки, чтобы графики отображались
1. была строчка objectManager.clusters.options.set('preset', 'islands#greenClusterIcons'); с ошибкой, надо передавать обьект, но выяснилось что она не нужна,  и я настроил в инициализации objectManager, что цвет должен браться от меток в виде круговой диаграммы 
1. удалил не нужный файл popup.js 