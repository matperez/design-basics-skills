# Дизайн-система: как строить и адаптировать

## Что такое дизайн-система

Дизайн-система — коллекция переиспользуемых компонентов, гайдлайнов и инструментов, которая обеспечивает consistency и качество продукта при масштабировании.

## 4 ключевых компонента

### 1. UI Kit (компоненты)
Переиспользуемые building blocks:
- Кнопки (primary, secondary, destructive, ghost)
- Формы (input, select, checkbox, radio, toggle)
- Карточки, модалки, тосты, tooltips
- Навигация (tabs, sidebar, breadcrumbs, pagination)
- Иконки (consistent стиль, единый размер grid)

### 2. Design Tokens
Конкретные значения, определяющие визуальный язык:
- **Colors:** primary, secondary, accent, neutral, semantic (success, warning, error, info)
- **Typography:** font families, sizes, weights, line heights
- **Spacing:** базовый шаг (4px или 8px) и множители
- **Border radius, shadows, z-index, breakpoints**

Tokens хранятся в формате, доступном и дизайну, и коду (JSON, CSS variables, Figma variables).

### 3. Patterns (паттерны поведения)
Решения для типичных задач:
- Навигация (sidebar vs top bar vs bottom tabs)
- Формы (валидация, error states, autosave)
- Таблицы (sorting, filtering, pagination)
- Empty states, loading states, error states
- Responsive breakpoints и адаптация

### 4. Documentation
- **Как** использовать каждый компонент (do / don't с примерами)
- **Когда** какой паттерн выбирать
- **Accessibility** требования для каждого компонента
- **Changelog** и versioning

## Когда строить свою, когда взять существующую

| Ситуация | Подход | Примеры |
|----------|--------|---------|
| MVP / стартап / маленькая команда | Взять готовую, кастомизировать tokens | Material Design, shadcn/ui, Chakra UI |
| Средний продукт, 5–15 дизайнеров | Форкнуть готовую, адаптировать компоненты | Polaris (e-commerce), Carbon (enterprise) |
| Enterprise, несколько продуктов | Полностью кастомная с governance | Apple HIG, Salesforce Lightning |

## 12 известных дизайн-систем (для вдохновения)

| Система | Кто | Особенности |
|---------|-----|------------|
| **Material Design 3** | Google | Dynamic color, comprehensive documentation, open-source |
| **Apple HIG** | Apple | Все платформы Apple, принципы + паттерны + компоненты |
| **Polaris** | Shopify | E-commerce focused, content guidelines, accessibility |
| **Carbon** | IBM | Enterprise, accessibility-first, open-source |
| **Ant Design** | Alibaba | Enterprise, rich components, i18n |
| **Atlassian Design** | Atlassian | Collaboration tools, extensive patterns |
| **Lightning** | Salesforce | Enterprise, accessibility, extensive tokens |
| **Spectrum** | Adobe | Creative tools, cross-platform |
| **Fluent** | Microsoft | Cross-platform, inclusive design |
| **TapTap** | Community | Figma-native, dark mode, Auto Layout 5.0 |
| **Arco** | ByteDance | Theme customization, Design Lab |
| **Dialect** | Community | Free, lightweight starter kit |

## Процесс создания

1. **Audit** — инвентаризация существующих компонентов и стилей.
2. **Define tokens** — цвета, типографика, spacing, breakpoints.
3. **Build core components** — начни с самых используемых (button, input, card, nav).
4. **Document** — do / don't для каждого компонента.
5. **Pilot** — применить к одному продукту / экрану, собрать фидбек.
6. **Scale** — расширить на все продукты, настроить governance.
7. **Maintain** — обновлять, версионировать, собирать requests.

## Governance

- **Кто владеет?** Выделенная команда или ротация ownership.
- **Как вносить изменения?** RFC / proposal → review → merge.
- **Versioning:** semver (breaking / feature / patch).
- **Deprecation:** объявлять заранее, дать время на миграцию.
