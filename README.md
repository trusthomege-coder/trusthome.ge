# Trust Home - Real Estate Marketplace

Современная платформа недвижимости на React + Vite + Tailwind + Supabase с авторизацией, админ-панелью и квизом.

## 🚀 Что дальше делать

### 1. Настройка Supabase

1. **Создайте проект в Supabase:**
   - Перейдите на [supabase.com](https://supabase.com)
   - Создайте новый проект
   - Скопируйте URL и anon key

2. **Создайте файл `.env`:**
   ```env
   VITE_SUPABASE_URL=your_supabase_url_here
   VITE_SUPABASE_ANON_KEY=your_supabase_anon_key_here
   ```

3. **Выполните миграции:**
   - В Supabase Dashboard перейдите в SQL Editor
   - Выполните по очереди все файлы из папки `supabase/migrations/`:
     1. `create_properties_table.sql`
     2. `create_favorites_table.sql`
     3. `create_quiz_questions_table.sql`
     4. `create_quiz_responses_table.sql`
     5. `insert_sample_properties.sql`

### 2. Настройка аутентификации

1. **В Supabase Dashboard:**
   - Перейдите в Authentication → Settings
   - Отключите "Enable email confirmations" (для упрощения)
   - В "Site URL" укажите `http://localhost:5173`

2. **Создайте админ-аккаунт:**
   - Email: `trusthome.ge@gmail.com`
   - Пароль: `7664440admin`

### 3. Функционал проекта

#### 🔐 **Авторизация**
- Регистрация и вход по email/пароль
- Личный кабинет для всех пользователей
- Админ-панель для `trusthome.ge@gmail.com`

#### 👨‍💼 **Админ-панель**
- **Управление недвижимостью**: добавление, редактирование, удаление
- **Управление квизом**: создание и редактирование вопросов
- Полный CRUD через Supabase

#### 🏠 **Каталог**
- Карточки недвижимости из базы данных
- Фильтрация по категориям (аренда/продажа/проект)
- Добавление в избранное (только для авторизованных)

#### 📝 **Квиз**
- Интерактивная анкета в конце главной страницы
- Сохранение ответов в Supabase
- Редактирование вопросов в админ-панели

#### 🌍 **Мультиязычность**
- Переключение между русским и английским
- Все тексты переводимые

### 4. Структура базы данных

```sql
-- Недвижимость
properties (id, title, description, price, location, bedrooms, bathrooms, area, image_url, category, type)

-- Избранное
favorites (id, user_id, property_id)

-- Вопросы квиза
quiz_questions (id, question, question_en, options, options_en, order_index)

-- Ответы квиза
quiz_responses (id, user_id, responses, contact_info)
```

### 5. Запуск проекта

```bash
npm install
npm run dev
```

Проект будет доступен на `http://localhost:5173`

## 📱 Основные страницы

- **/** - Главная с квизом
- **/catalog** - Каталог недвижимости
- **/admin** - Админ-панель (только для админа)
- **/rent** - Аренда
- **/buy** - Продажа
- **/projects** - Проекты
- **/about** - О нас
- **/contacts** - Контакты

## 🎨 Дизайн

- Минималистичный стиль
- Белый и бежевый фон с синими акцентами
- Адаптивная верстка
- Smooth анимации
- shadcn/ui компоненты