## Деплой приложения на Django с использованием Docker и Git Actions

Этот репозиторий содержит необходимую конфигурацию и скрипты для развёртывания приложения на Django с использованием Docker и Git Actions. Процесс развёртывания включает в себя настройку приложения Django в контейнере Docker, загрузку образа Docker на Docker Hub и развёртывание приложения на удалённом сервере с помощью Docker Compose и Git Actions. При успешном развёртывании отправляется уведомление в указанный чат в Telegram.

### Переменные окружения

Перед началом работы убедитесь, что установлены следующие переменные окружения в вашем репозитории или настройках Git Actions:

- `DOCKERHUB_TOKEN`: Пароль от Docker Hub для загрузки образов
- `DOCKERHUB_USERNAME`: Имя пользователя Docker Hub для загрузки образов
- `HOST`: Удалённый сервер для развёртывания
- `USER`: Имя пользователя на удалённом сервере для развёртывания
- `SSH_KEY`: SSH-ключ для подключения к удалённому серверу
- `PASSPHRASE`: Секретная фраза для SSH-ключа (при необходимости)
- `TELEGRAM_TOKEN`: Токен бота или пользователя в Telegram для уведомлений
- `TELEGRAM_TO`: ID чата для уведомлений о ходе работы

Для PostgreSQL Database:

- `POSTGRES_DB`: Название базы данных PostgreSQL
- `POSTGRES_PASSWORD`: Пароль для базы данных PostgreSQL
- `POSTGRES_USER`: Имя пользователя базы данных PostgreSQL

Для Django приложения:

- `SERVER_NAME`: Доменное имя или IP-адрес удалённого сервера

### Шаги развёртывания

1. **Настройка приложения Django:**

   Склонируйте этот репозиторий и настройте ваше приложение Django внутри него.

2. **Создание и загрузка Docker-образа:**

   - Настройте Dockerfile и docker-compose.yml вашего приложения Django по необходимости.
   - Выполните необходимые команды для создания Docker-образа и его загрузки на Docker Hub.

3. **Конфигурация удалённого сервера:**

   - Удостоверьтесь, что удалённый сервер соответствует требованиям Docker и Docker Compose.
   - Настройте аутентификацию на удалённом сервере с использованием ключей SSH.

4. **Git Actions Workflow:**

   - Настройте файл сценария Git Actions (`/.github/workflows/build_and_deploy.yml`) с соответствующими параметрами.
   - Сценарий должен включать шаги для подключения к удалённому серверу, получения последних изменений кода и развёртывания Docker Compose.

5. **Уведомление в Telegram:**

   - Создайте бота в Telegram или используйте свою учётную запись для генерации токена.
   - Получите ID чата, куда вы хотите получать уведомления.
   - Настройте сценарий для отправки уведомления в Telegram при успешном развёртывании.

**Примечание:** Аккуратно обращайтесь с конфиденциальной информацией, такой как SSH-ключи, пароли и токены, безопасным образом, используя секреты Git Actions или другие надёжные методы.

Не стесняйтесь изменять и адаптировать предоставленные инструкции и скрипты в соответствии с требованиями вашего проекта. Удачи в развёртывании! Если у вас есть вопросы, не стесняйтесь обращаться.