# Dostaffkin

Приложение для расчёта стоимости доставки и оформления/отслеживания заявок на курьерскую доставку с маршрутизацией через Яндекс.Карты.

## 1. О проекте
- Название: dostaffkin`
- Цель: заявка на доставку посылок между городами/странами, расчет стоимости, создание заявки и трекинг по ID.

## 2. Ключевой функционал
- Страницы:
  - `/` — домашняя
  - `/order` — расчет и создание заказа
  - `/track` — отслеживание по номеру отправления
- `order`:
  - ввод `from`, `to`, `размер отправления`, `скорость`доставки
  - прокладка маршрута через `ymaps.multiRouter.MultiRoute`
  - расчет `distance`, `duration`, `total` на основе `order.config` (size/rate/min)
  - отправка POST в `https://testologia.ru/delivery/create`
- `track`:
  - ввод номера, валидация
  - GET `https://testologia.ru/delivery/info?id=<id>`
- Сервис `DeliveryApi` с обработкой ошибок `catchError`.

## 3. Стек
- Angular 21 (standalone components)
- TypeScript 5.9
- RxJS 7.8
- Angular HTTPClient
- Yandex Maps API (пользовательские подсказки + маршруты)
  ngx-toastr (для UI-уведомлений)
- Vitest для тестов (в devDependencies)

## 4. Установка и запуск
1. `npm ci` (или `npm install`)
2. `npm run start` — запуск dev-сервера
3. `npm run build` — сборка
4. `npm run watch` — сборка в режиме наблюдения
5. `npm run test` — тесты

## 5. Структура
- `src/app/app.routes.ts` — маршруты
- `src/app/pages/order` — логика заказа, формы
- `src/app/pages/track` — логика трекинга
- `src/app/services/delivery-api.ts` — API-запросы
- `src/index.html` — подключение Yandex Maps
