1. Устанавливаем `vk-miniapps-deploy`:

    `npm install @vkontakte/vk-miniapps-deploy --include=dev`

2. Создаём `vk-hosting-config.json`

    ``` JSON
    {
        "static_path": "build", // directory with files to host

        "app_id": 123456, // app id

        "endpoints": {

        "mobile": "index.html", // mobile app

        "web": "index.html", // desktop in browser

        "mvk": "index.html" // mobile in browser

        }
    }
    ```

3. Добавляем

    ``` JSON
    "predeploy": "npm run build",

    "deploy": "vk-miniapps-deploy"
    ```

4. Добавляем `"homepage": "."` в `package.json`
5. Запускаем `npm run deploy`, соглашаемся со всеми пунктами

_!! Если используем CI/CD понадобится сохранить ключ из последнего шага !!_

Взято из [документации VK-mini-apps](https://dev.vk.com/ru/mini-apps/development/hosting/overview)

При добавлении CI/CD потребуется добавить переменную окружения `MINI_APPS_ACCESS_TOKEN` (ключ) и параметр `"noprompt": 1` в файл `vk-hosting-config.json`