# Авиценна — сайт сети клиник

Современный сайт медицинского центра «Авиценна» (Бишкек), построенный на TanStack Start + React + Tailwind CSS.

**Опубликованная версия в Lovable**: https://avicennav1.lovable.app

## Разработка

```sh
bun install
bun run dev
```

## Деплой на любой сервер

Сборка не привязана к конкретному хостингу: `vite build` запускает Nitro, который сам
определяет платформу по переменным окружения CI (Vercel, Netlify, Cloudflare и др.).
Если платформа не определяется (например, свой VPS), укажите пресет явно через
переменную `NITRO_PRESET`:

```sh
# Обычный Node-сервер / VPS — результат в .output/, запуск: node .output/server/index.mjs
NITRO_PRESET=node_server bun run build

# Vercel
NITRO_PRESET=vercel bun run build

# Netlify
NITRO_PRESET=netlify bun run build

# Cloudflare Workers
NITRO_PRESET=cloudflare-module bun run build
```

Сборка и запуск на чистом Node:

```sh
npm install
NITRO_PRESET=node_server npm run build
node .output/server/index.mjs   # по умолчанию порт 3000
```

### Переменные окружения

Задайте их в панели хостинга или в `.env` на сервере:

- `VITE_SUPABASE_URL`
- `VITE_SUPABASE_PUBLISHABLE_KEY`
- `VITE_SUPABASE_PROJECT_ID`
- `SUPABASE_URL`
- `SUPABASE_PUBLISHABLE_KEY`
- `SUPABASE_PROJECT_ID`
- `LOVABLE_API_KEY` — берётся из секретов проекта в Lovable (нужен для ИИ-функций).
- `VITE_LOVABLE_CONNECTOR_GOOGLE_MAPS_BROWSER_KEY` и `VITE_LOVABLE_CONNECTOR_GOOGLE_MAPS_TRACKING_ID` — если используется карта филиалов.

Всё, что начинается с `VITE_`, вшивается в код на этапе сборки, поэтому эти значения
должны быть доступны именно при запуске `npm run build`, а не только при запуске сервера.

### Примечание про сборку в Lovable

Сборка внутри Lovable всегда настраивается на собственный хостинг Lovable и игнорирует
`NITRO_PRESET` — это не влияет на самостоятельный деплой.
