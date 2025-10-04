BloomWatch — интерактивная карта цветения (готовый пакет)
Что внутри:
- index.html — frontend (MapLibre + Chart.js) в папке public
- server.js — простой Express сервер, отдаёт /api/dates и /api/blooms?date=
- samples/*.geojson — пример данных для трёх дат
- gee_script.js — стартовый snippet для Google Earth Engine
- package.json — зависимости

Как запустить локально:
1) Установи Node.js (v16+). 
2) В папке bloomwatch запусти:
   npm install
   npm start
3) Открой http://localhost:3000

Как подключить реальные данные:
- Рекомендую генерировать GeoJSON по дате на бэкенде (export из GEE -> S3/Cloud -> сервер отдаёт нужный файл).
- Формат Feature.properties:
  - id, date (YYYY-MM-DD), intensity (0..1), species, confidence (0..1), timeseries (array {date,value})

Дальше я могу:
- Подготовить Dockerfile и terraform-метаданные для деплоймента.
- Написать GEE-скрипт, который экспортирует агрегированные события цветения (tile/CSV) в S3.
- Добавить аутентификацию, валидацию и очередь обработки.

Если хочешь — прямо сейчас делаю Dockerfile и архив, чтобы можно было деплоить в облако.
