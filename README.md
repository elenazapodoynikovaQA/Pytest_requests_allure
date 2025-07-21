# Pytest_requests_allure
Пример автотестов на pytest + requests с отчетом Allure

<img width="2256" height="1504" alt="pytest _ requests_allure" src="https://github.com/user-attachments/assets/72b9bf6c-83d1-4348-bd28-c1c9f9c50ac5" />

<img width="2029" height="1504" alt="tests_api_pytest_requests_allure" src="https://github.com/user-attachments/assets/30596859-8351-4e13-b164-418a764c4ead" />

# PULS – API SMS Registration Tests
Автоматические тесты для проверки регистрации и авторизации пользователей через SMS на платформе **PULS** (`upjet.dev.sandakov.space`).
## Используемый стек
Python 3.10+
pytest — фреймворк для автотестов
requests — отправка HTTP-запросов

##  Структура проекта
puls_sms_autotests/
conftest.py # Фикстура registered_user
test_api_sms_registration.py # Основной файл с тестами

##  Сценарий:

1. Полная регистрация пользователя по SMS 
2. Проверка ошибки при повторной регистрации (422)
3. Вход с верным телефоном и паролем (200)
4. Вход с неверным телефоном (401)

##  Установка зависимостей

```bash
pip install pytest requests

## Запустить конкретный файл:
pytest -s test_api_sms_registration.py

## Запустить все тесты:
pytest -s

 ## С HTML-отчётом:
 pytest -s test_api_sms_registration.py --html=report.html

## Фикстура находится в conftest.py. Она автоматически генерирует уникальные: номер телефона (phone), email (email), пароль (password), возвращает их как dict для использования в тестах

Все запросы отправляются на тестовый сервер https://upjet-back.dev.sandakov.space
SMS-код в тестовой среде — 54321
Регистрация делится на 3 этапа:
POST /api/auth/register
POST /api/auth/verify/phone/confirm
POST /api/auth/register/complete
