# Image Resize Bot

Бот который умеет изменять размеры изображений для последующей публикации в Instagram

## How To Run

### Prod

    docker=-compose -f docker-compose.yml up --build -d

Не забудьте перед запуском создать все необходимые переменные окружения и сгенерировать dhparam

    sudo openssl dhparam -out ./dhparam/dhparam-2048.pem 2048