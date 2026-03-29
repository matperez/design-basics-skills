# Каталог Layout'ов для Web Design

## 12 типов layout

### 1. Grid layout

**Что:** контент организован в строки и колонки.
**Подтипы:** modular grid (ячейки), single-column, multi-column (2–12).
**Best for:** e-commerce каталоги, блоги, responsive-сайты.
**Пример:** Nordstrom — modular grid для товаров.
**Почему работает:** responsive из коробки, знаком пользователям, масштабируется.

### 2. Split-screen layout

**Что:** страница разделена на две равные части.
**Best for:** лендинги, registration pages, сравнение опций.
**Пример:** Dropbox — план слева, форма справа.
**Почему работает:** два фокуса одновременно; идеально для «контент + действие».

### 3. Asymmetrical layout

**Что:** две зоны, но разного размера (60/40, 70/30).
**Best for:** продуктовые страницы, акцент на одном элементе.
**Пример:** FigJam — большой визуал + CTA сбоку.
**Почему работает:** большая зона притягивает взгляд → контроль внимания.

### 4. Full-screen layout

**Что:** одно изображение/видео занимает весь экран, контент поверх.
**Best for:** hero-секции, лендинги, минималистичные сайты.
**Пример:** Fruitful — полноэкранные фото + overlay текст.
**Почему работает:** максимальный визуальный impact за 50ms.
**Осторожно:** текст должен быть читаем поверх фона (contrast!).

### 5. Side-scrolling layout

**Что:** контент прокручивается горизонтально.
**Best for:** галереи, категории, карусели.
**Пример:** Netflix — горизонтальные ряды по жанрам.
**Почему работает:** компактно показывает много контента.
**Осторожно:** пользователи привыкли к вертикальному скроллу — нужны visual cues (стрелки).

### 6. Card layout

**Что:** контент в отдельных карточках, организованных в grid.
**Best for:** dashboard, каталоги, social feeds, рецепты.
**Пример:** Pinterest, Trello, Yellowbird.
**Почему работает:** каждая карточка — self-contained unit; легко сканировать.

### 7. Magazine layout

**Что:** смесь размеров блоков, как в журнале: hero + grid + текст.
**Best for:** новостные сайты, медиа, editorial.
**Пример:** BBC, Medium, The Verge.
**Почему работает:** визуальное разнообразие удерживает внимание.

### 8. Single-column layout

**Что:** один столбец контента, вертикальный скролл.
**Best for:** блоги, лонгриды, email newsletters, мобильный дизайн.
**Пример:** Medium статьи, Google Docs.
**Почему работает:** фокус на тексте, минимум отвлечений.

### 9. Hero layout

**Что:** большой visual + headline + CTA в верхней части, контент ниже.
**Best for:** лендинги, портфолио, product pages.
**Пример:** Apple product pages.
**Почему работает:** первые 50ms = визуальный impact + ценностное предложение.

### 10. Sidebar layout

**Что:** основной контент + боковая панель (навигация, фильтры, виджеты).
**Best for:** блоги, документация, dashboards, admin panels.
**Пример:** GitHub, Notion, WordPress admin.
**Почему работает:** навигация всегда видна; основной контент не перегружен.

### 11. Alternating layout

**Что:** секции чередуются: текст слева / изображение справа → наоборот.
**Best for:** лендинги, about pages, feature tours.
**Пример:** Stripe — чередование секций с анимациями.
**Почему работает:** ритм и визуальное разнообразие при скролле.

### 12. Featured image layout

**Что:** крупное изображение — главный элемент; текст и CTA вторичны.
**Best for:** фотография, портфолио, fashion, travel.
**Пример:** National Geographic, Unsplash.
**Почему работает:** визуал говорит за себя; текст — только поддержка.

## Матрица выбора

| Тип сайта | Рекомендуемые layout |
|-----------|---------------------|
| **E-commerce** | Grid (modular), Card, Sidebar (фильтры) |
| **Blog / Editorial** | Single-column, Magazine, Sidebar |
| **Landing page** | Hero, Split-screen, Alternating, Full-screen |
| **Portfolio** | Featured image, Grid, Full-screen |
| **SaaS / Product** | Hero + Alternating, Split-screen |
| **Dashboard** | Sidebar + Card + Grid |
| **Documentation** | Sidebar + Single-column |
| **Corporate** | Hero + Grid + Alternating |

## Eye patterns и layout

| Паттерн | Layout-рекомендация |
|---------|-------------------|
| **Z-pattern** | Лого top-left → CTA top-right → visual center → CTA bottom-right |
| **F-pattern** | Важное слева и сверху; вторичное — ниже и правее |
| **Focal point** | Один доминирующий элемент на экран; всё остальное — supporting |
