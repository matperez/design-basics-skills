# Responsive: техническая справка

## Viewport meta-тег

Обязателен для любой мобильной адаптации:

```html
<meta name="viewport" content="width=device-width, initial-scale=1">
```

Без него мобильный браузер рендерит страницу в 980px и масштабирует — responsive-стили не сработают.

**Не использовать** `maximum-scale=1` или `user-scalable=no` — это ломает зум и нарушает доступность.

## Breakpoints

### Подход: по контенту, а не по устройствам

Меняй layout там, где **ломается читаемость или композиция**, а не по таблице устройств.

### Ориентировочные диапазоны

| Диапазон | Ширина | Типичное |
|----------|--------|----------|
| Small phone | 320–375px | iPhone SE, старые Android |
| Phone | 376–428px | Большинство современных телефонов |
| Tablet | 768–834px | iPad mini, средние планшеты |
| Laptop | 1024–1440px | Ноутбуки |
| Desktop | 1440px+ | Мониторы |

### Mobile-first медиазапросы

```css
/* Базовые стили — для мобильных */
.card { width: 100%; }

/* Расширение для планшетов и выше */
@media (min-width: 768px) {
  .cards { display: grid; grid-template-columns: 1fr 1fr; gap: 1.5rem; }
}

/* Расширение для десктопа */
@media (min-width: 1024px) {
  .cards { grid-template-columns: repeat(3, 1fr); }
}
```

## CSS Grid и Flexbox

### Grid: авто-раскладка без медиазапросов

```css
.cards {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
  gap: 1rem;
}
```

Браузер сам считает, сколько колонок помещается. Медиазапрос не нужен.

### Flexbox: обёртка с минимальной шириной

```css
.cards {
  display: flex;
  flex-wrap: wrap;
  gap: 1rem;
}
.card {
  flex: 1 1 280px;
}
```

## Container Queries (2023+)

Компонент реагирует на ширину **своего контейнера**, а не viewport. Удобно для карточек, встраиваемых виджетов, сайдбаров.

```css
.card-wrapper {
  container-type: inline-size;
}

@container (min-width: 400px) {
  .card { display: flex; gap: 1rem; }
}

@container (max-width: 399px) {
  .card { display: block; }
}
```

## Fluid Typography

### clamp() — один размер для всех экранов

```css
h1 { font-size: clamp(1.75rem, 4vw + 0.5rem, 3.5rem); }
p  { font-size: clamp(1rem, 1vw + 0.75rem, 1.25rem); }
```

**Не использовать** чистые `vw` без фиксированной добавки — ломается зум.

### Базовый размер

- Для body text: **≥16px** (меньше — iOS зумит формы автоматически).
- Длина строки: 35–55 символов на мобиле (на десктопе — 65–80).
- Межстрочный: 1.4–1.6 для body.

## Responsive Images

### srcset + sizes

```html
<img
  src="image-800.jpg"
  srcset="image-400.jpg 400w, image-800.jpg 800w, image-1200.jpg 1200w"
  sizes="(max-width: 600px) 100vw, 50vw"
  alt="Описание"
  width="800"
  height="600"
  loading="lazy"
>
```

### Форматы

| Формат | Когда |
|--------|-------|
| **AVIF** | Лучшая компрессия; поддержка растёт |
| **WebP** | Широкая поддержка; хороший баланс |
| **JPEG** | Фотографии; fallback |
| **PNG** | Прозрачность; UI-элементы |
| **SVG** | Логотипы, иконки, диаграммы |

### CLS (Cumulative Layout Shift)

Явные `width` и `height` на `<img>` или CSS `aspect-ratio` предотвращают «прыжки» layout при загрузке.

```css
img {
  max-width: 100%;
  height: auto;
}
```

### Lazy loading

```html
<img loading="lazy" …>
```

Для изображений выше fold — **не** ставить `loading="lazy"` (замедляет LCP).

## Единицы viewport

| Единица | Что | Когда |
|---------|-----|-------|
| `vh` | 1% высоты viewport (может «прыгать» из-за адресной строки) | Десктоп |
| `dvh` | Динамическая высота (учитывает адресную строку) | Мобильные hero-секции |
| `svh` | Малая высота (с видимой адресной строкой) | Безопасный минимум |
| `lvh` | Полная высота (без адресной строки) | Максимум |

Для hero на мобиле:

```css
.hero { min-height: 100dvh; }
```

## Зоны касания (WCAG 2.2)

| Уровень | Минимум | Рекомендация |
|---------|---------|-------------|
| **AA (SC 2.5.8)** | 24×24 CSS px | Минимум; с учётом padding и spacing |
| **AAA (SC 2.5.5)** | 44×44 CSS px | Цель для тач-интерфейсов |
| **Material / Apple** | 48dp / 44pt | Продуктовые гайдлайны |

Расстояние между кликабельными зонами: **≥8px**.

## Предпочтения пользователя

```css
/* Тёмная тема */
@media (prefers-color-scheme: dark) { … }

/* Отключённые анимации */
@media (prefers-reduced-motion: reduce) {
  *, *::before, *::after {
    animation-duration: 0.01ms !important;
    transition-duration: 0.01ms !important;
  }
}

/* Повышенный контраст */
@media (prefers-contrast: more) { … }
```

## Источники

- [web.dev — Responsive web design basics](https://web.dev/articles/responsive-web-design-basics)
- [web.dev — The new responsive](https://web.dev/articles/new-responsive)
- [web.dev — Macro layouts](https://web.dev/learn/design/macro-layouts)
- [MDN — Responsive web design](https://developer.mozilla.org/en-US/docs/Learn/CSS/CSS_layout/Responsive_Design)
- [WCAG 2.2 SC 2.5.8 — Target Size (Minimum)](https://www.w3.org/WAI/WCAG22/Understanding/target-size-minimum.html)
- [WCAG 2.2 SC 2.5.5 — Target Size (Enhanced)](https://www.w3.org/WAI/WCAG22/Understanding/target-size-enhanced.html)
