# Noix - Мебель на заказ в Ташкенте

Сайт-визитка для компании по изготовлению мебели на заказ.

## Структура проекта

```
mebel-site/
├── index.html          # Главная страница
├── style.css           # Стили
├── server.js           # Локальный сервер (для разработки)
├── start-server.bat    # Скрипт запуска локального сервера
├── Images/             # Изображения
│   ├── mebel-banner.png
│   ├── kuhni.png
│   ├── garderob.png
│   ├── shkaf.jpg
│   ├── prihojka.png
│   ├── spalna.png
│   ├── detskaya.jpg
│   └── remont1-5.jpg
└── icons/              # Иконки SVG
    ├── telegram.svg
    ├── instagram.svg
    └── phone.svg
```

## Локальный запуск

### Вариант 1: Через Node.js
```bash
node server.js
```
Сайт будет доступен на http://localhost:3000

### Вариант 2: Через bat-файл
Дважды кликните на `start-server.bat`

### Вариант 3: Через http-server
```bash
npx http-server . -p 3000
```

## Деплой

### Статический хостинг (GitHub Pages, Netlify, Vercel)

1. Загрузите все файлы на хостинг
2. Убедитесь, что `index.html` находится в корневой директории
3. Все пути уже относительные, дополнительная настройка не требуется

### Apache

Создайте файл `.htaccess` в корне проекта:
```apache
RewriteEngine On
RewriteBase /

# Перенаправление на index.html
DirectoryIndex index.html

# Кэширование статических файлов
<IfModule mod_expires.c>
  ExpiresActive On
  ExpiresByType image/jpg "access plus 1 year"
  ExpiresByType image/jpeg "access plus 1 year"
  ExpiresByType image/png "access plus 1 year"
  ExpiresByType image/svg+xml "access plus 1 year"
  ExpiresByType text/css "access plus 1 month"
  ExpiresByType application/javascript "access plus 1 month"
</IfModule>

# Gzip сжатие
<IfModule mod_deflate.c>
  AddOutputFilterByType DEFLATE text/html text/plain text/xml text/css text/javascript application/javascript
</IfModule>
```

### Nginx

Добавьте в конфигурацию:
```nginx
server {
    listen 80;
    server_name Noix.uz;
    root /path/to/mebel-site;
    index index.html;

    location / {
        try_files $uri $uri/ /index.html;
    }

    # Кэширование
    location ~* \.(jpg|jpeg|png|gif|ico|svg|css|js)$ {
        expires 1y;
        add_header Cache-Control "public, immutable";
    }
}
```

## Требования

- Современный веб-браузер
- Для локального запуска: Node.js (опционально)

## Особенности

- ✅ Адаптивный дизайн
- ✅ SEO оптимизация
- ✅ Структурированные данные (Schema.org)
- ✅ Open Graph мета-теги
- ✅ Модальное окно для просмотра изображений
- ✅ Бесконечная бегущая строка
- ✅ Плавающие кнопки для связи

## Контакты

- Телефон: +998 91 133 32 63
- Telegram: @mebel_blackwood
- Instagram: @noix.uz

## Лицензия

© 2026 Noix — Мебель под заказ в Ташкенте
