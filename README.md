## Дипломный проект. Задание 2: Тестирование API

### Автотесты для проверки API сервиса Stellar Burgers

### Структура проекта

- `tests` - пакет, содержащий тесты, разделенные по направленности: `test_user.py`, `test_order.py`
- `conftest.py` - фикстуры для тестов
- `data.py` - константы и данные для тестов
- `generator.py` - генератор создания нового пользователя
- `allure_results` - пакет, содержащий json-файлы для Allure-отчета

### Реализованные сценарии

Созданы API-тесты, покрывающие ручки `Создание пользователя`, `Логин пользователя`, `Изменение данных пользователя`,
`Создание заказа`, `Получение заказов конкретного пользователя`

### TestRegistrationUser:

- `test_registration_user_unique_user_data_true` - Проверка регистрации уникального пользователя
- `test_registration_user_user_already_exists_error_message` - Проверка регистрации пользователя, который уже был зарегистрирован
- `test_registration_user_without_required_field_error_message` - Проверка регистрации пользователя, при передачи в ручку не всех обязательных полей

### TestLoginUser:

- `test_login_user_registered_user_data_true` - Проверка авторизации пользователя
- `test_login_user_wrong_email_error_message` - Проверка авторизации пользователя с неправильно указанным логином
- `test_login_user_wrong_pass_error_message` - Проверка авторизации пользователя с неправильно указанным паролем

### TestChangingUserData:

- `test_changing_user_data_authorized_user_new_email_true` - Проверка изменения данных авторизованного пользователя, email можно изменить
- `test_changing_user_data_authorized_user_new_password_true` - Проверка изменения данных авторизованного пользователя, password можно изменить
- `test_changing_user_data_authorized_user_new_name_true` - Проверка изменения данных авторизованного пользователя, name можно изменить
- `test_chang_user_data_not_auth_user_new_data_error_message` - Проверка изменения данных неавторизованного пользователя

### TestCreatingOrder:

- `test_creating_order_auth_user_valid_ingredients_true` - Проверка создания заказа авторизованного пользователя с ингредиентами
- `test_creating_order_not_auth_user_valid_ingredients_true` - Проверка создания заказа неавторизованного пользователя с ингредиентами
- `test_creating_order_auth_user_no_ingredients_error_message` - Проверка создания заказа авторизованного пользователя без ингредиентов
- `test_creating_order_not_auth_user_no_ingredients_error_message` - Проверка создания заказа неавторизованного пользователя без ингредиентов
- `test_creating_order_auth_user_invalid_hash_error_message` - Проверка создания заказа авторизованного пользователя c неверным хешем ингредиентов
- `test_creating_order_not_auth_user_invalid_hash_error_message` - Проверка создания заказа неавторизованного пользователя c неверным хешем ингредиентов

### TestReceivingUserOrders:

- `test_receiving_user_orders_auth_user_true` - Проверка получения заказа конкретного авторизованного пользователя
- `test_receiving_user_orders_not_auth_user_error_message` - Проверка получения заказа конкретного неавторизованного пользователя

### Запуск автотестов

**Установка зависимостей**

> `$ pip install -r requirements.txt`

**Запуск автотестов**

>  `$ pytest -v tests/`

**Генерация Allure-отчета**

>  `$ pytest tests/ --alluredir=allure_results`

**Создание HTML-отчета**

>  `$ allure serve allure_results`