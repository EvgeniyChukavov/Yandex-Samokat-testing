# Чек-лист тестирования API

## Создание курьера (POST /api/v1/courier)

### Login

| ID | Проверка | ОР | Статус | Баг |
| :--- | :--- | :--- | :--- | :--- |
| 1 | login qwert (5 символов) | 201, {"ok": true} | Passed | |
| 2 | login qw (2 символа) | 201 | Passed | |
| 3 | login qwertyuiop (10 символов) | 201 | Passed | |
| 4 | login QWERT (заглавные) | 201 | Passed | |
| 5 | login q (1 символ) | 400 | Failed | BUG1 |
| 6 | login qwertyuiopa (11 символов) | 400 | Failed | BUG2 |
| 7 | login существующего курьера | 409 | Passed | |
| 8 | без поля login | 400 | Passed | |
| 9 | пустой login ("") | 400 | Passed | |
| 10 | login с пробелом внутри | 400 | Failed | BUG3 |
| 11 | login с пробелом в начале | 400 | Failed | BUG3 |
| 12 | login с пробелом в конце | 400 | Failed | BUG3 |
| 13 | login со спецсимволом @ | 400 | Failed | BUG4 |
| 14 | login с кириллицей | 400 | Failed | BUG5 |
| 15 | firstName с дефисом | 400 | Failed | BUG16 |

### Password

| ID | Проверка | ОР | Статус | Баг |
| :--- | :--- | :--- | :--- | :--- |
| 16 | password 1234 (4 цифры) | 201 | Passed | |
| 17 | password 123 (3 цифры) | 400 | Failed | BUG6 |
| 18 | password 12345 (5 цифр) | 400 | Failed | BUG7 |
| 19 | пустой password | 400 | Passed | |
| 20 | password с пробелом внутри | 400 | Failed | BUG8 |
| 21 | password с пробелом в начале | 400 | Failed | BUG8 |
| 22 | password латиница | 400 | Failed | BUG9 |
| 23 | password кириллица | 400 | Failed | BUG10 |
| 24 | password спецсимволы | 400 | Failed | BUG11 |
| 25 | без поля password | 400 | Passed | |

### firstName

| ID | Проверка | ОР | Статус | Баг |
| :--- | :--- | :--- | :--- | :--- |
| 26 | firstName Qweнг (5 символов) | 201 | Passed | |
| 27 | firstName qц (2 символа) | 201 | Passed | |
| 28 | firstName 10 символов | 201 | Passed | |
| 29 | firstName q (1 символ) | 400 | Failed | BUG12 |
| 30 | firstName 11 символов | 400 | Failed | BUG13 |
| 31 | пустой firstName | 201 | Passed | |
| 32 | firstName с цифрами и спецсимволами | 201 | Passed | |
| 33 | без поля firstName | 201 | Passed | |
| 34 | firstName с пробелом внутри | 201 | Passed | |
| 35 | firstName с пробелом в начале | 201 | Passed | |
| 36 | firstName с дефисом | 201 | Passed | |

### БД

| ID | Проверка | ОР | Статус |
| :--- | :--- | :--- | :--- |
| 37 | Запись создалась в Couriers | Запись есть | Passed |
| 38 | passwordHash содержит хэш | Хэш | Passed |

## Удаление курьера (DELETE /api/v1/courier/:id)

| ID | Проверка | ОР | Статус | Баг |
| :--- | :--- | :--- | :--- | :--- |
| 39 | Существующий id | 200, {"ok": true} | Passed | |
| 40 | Несуществующий id | 404, «Курьера с таким id нет» | Passed | |
| 41 | Без id | 400, «Недостаточно данных» | Failed | BUG14 |
| 42 | Проверка БД после удаления | Запись удалена | Passed | |
| 43 | Связанные заказы в Orders | Заказы удалены | Failed | BUG15 |

## Получение заказа по номеру (GET /api/v1/orders/track)

| ID | Проверка | ОР | Статус |
| :--- | :--- | :--- | :--- |
| 44 | Существующий track | 200, данные заказа | Passed |
| 45 | Без параметра t | 400, «Недостаточно данных» | Passed |
| 46 | Несуществующий track | 404, «Заказ не найден» | Passed |
| 47 | Проверка поля status | Корректно | Passed |
| 48 | Все поля соответствуют БД | Соответствуют | Passed |
