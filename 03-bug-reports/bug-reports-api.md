# Баг-репорты — API тестирование

| ID | Название | Приоритет | Запрос | ОР | ФР |
| :--- | :--- | :--- | :--- | :--- | :--- |
| BUG1 | login 1 символ — 201 вместо 400 | Стандартный | POST /api/v1/courier | 400 | 201 |
| BUG2 | login 11 символов — 201 вместо 400 | Стандартный | POST /api/v1/courier | 400 | 201 |
| BUG3 | login с пробелом — 201 вместо 400 | Стандартный | POST /api/v1/courier | 400 | 201 |
| BUG4 | login со спецсимволом @ — 201 | Стандартный | POST /api/v1/courier | 400 | 201 |
| BUG5 | login с кириллицей — 201 | Стандартный | POST /api/v1/courier | 400 | 201 |
| BUG6 | password 3 цифры — 201 | Стандартный | POST /api/v1/courier | 400 | 201 |
| BUG7 | password 5 цифр — 201 | Стандартный | POST /api/v1/courier | 400 | 201 |
| BUG8 | password с пробелом — 201 | Стандартный | POST /api/v1/courier | 400 | 201 |
| BUG9 | password латиница — 201 | Стандартный | POST /api/v1/courier | 400 | 201 |
| BUG10 | password кириллица — 201 | Стандартный | POST /api/v1/courier | 400 | 201 |
| BUG11 | password спецсимволы — 201 | Стандартный | POST /api/v1/courier | 400 | 201 |
| BUG12 | firstName 1 символ — 201 | Стандартный | POST /api/v1/courier | 400 | 201 |
| BUG13 | firstName 11 символов — 201 | Стандартный | POST /api/v1/courier | 400 | 201 |
| BUG14 | DELETE без id — 404 вместо 400 | Желательный | DELETE /api/v1/courier/ | 400 | 404 |
| BUG15 | Связанные заказы не удаляются | Критический | DELETE /api/v1/courier/:id | Заказы удалены | Остаются |
| BUG16 | Дефис в firstName не разрешён в требованиях | Желательный | POST /api/v1/courier | Дефис разрешён | Не указан |
