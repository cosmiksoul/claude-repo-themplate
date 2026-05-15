# Sprint 1 — Главная страница со списком записей и фильтром по статусу

## Overview

Первый продуктовый спринт. Реализуем главную страницу: компонент списка записей, загружаемого из локального хранилища, и фильтр по статусу (`active` / `done` / `all`). Это базовая поверхность, на которую дальше будут навешиваться остальные операции (создание, редактирование).

## Scope (user stories)

Из `docs/project/JTBD.md`:

- **U-1** ★ Как пользователь я хочу видеть список своих записей при открытии приложения, чтобы сразу понимать, что у меня есть. `[list]`
- **U-2** ★ Как пользователь я хочу переключать фильтр по статусу (все / активные / завершённые), чтобы быстро находить нужное. `[filter]`
- **U-3** Как пользователь я хочу, чтобы при отсутствии записей мне показывали понятный empty state, а не пустую страницу. `[empty-state]`

## Tasks

1. Создать компонент `RecordList` в `src/components/record-list/`.
   - Принимает массив записей и колбэк выбора записи.
   - Каждая запись — `id`, `title`, `status` (`active` | `done`), `createdAt`.
   - Если массив пустой — показывает empty state с текстом из `src/lib/copy.js` (ключ `emptyList`).
2. Создать компонент `StatusFilter` в `src/components/status-filter/`.
   - Три кнопки: All / Active / Done.
   - Активная кнопка визуально выделена.
   - Управляется через проп `value` и колбэк `onChange`.
3. На главной странице `src/pages/home.jsx`:
   - Читать записи из `localStorage` через `src/lib/storage.js` (функция `loadRecords`).
   - Хранить текущий фильтр в `useState`.
   - Рендерить `StatusFilter` сверху, `RecordList` снизу с отфильтрованными записями.
4. Тексты UI (заголовок, тексты кнопок, empty state) — только через `src/lib/copy.js`. Никаких хардкодов в JSX.

## Technical Notes

- Стек: React + Vite + Tailwind (см. `docs/context/architecture.md`).
- Стиль компонента — функциональный, без классов, через хуки.
- `src/lib/storage.js` уже существует с прошлого Pre-MVP, переиспользовать `loadRecords`.
- Структура записи зафиксирована в `docs/context/decisions-log.md`, ADR-002. Не менять.

## ADR Constraints

- **ADR-001 (no backend)** — никаких сетевых запросов. Все данные из localStorage.
- **ADR-002 (schema записи)** — не добавлять полей в структуру записи. Если возникает потребность — стоп, эскалация.
- **ADR-003 (UI-тексты только через `copy.js`)** — никаких строк в JSX напрямую.

## Files involved

**Создаются:**
- `src/components/record-list/record-list.jsx`
- `src/components/record-list/record-list.test.js`
- `src/components/status-filter/status-filter.jsx`
- `src/components/status-filter/status-filter.test.js`

**Модифицируются:**
- `src/pages/home.jsx` (сейчас пустая болванка)
- `src/lib/copy.js` (добавить ключи `emptyList`, `filterAll`, `filterActive`, `filterDone`)

## Acceptance criteria

1. При открытии главной страницы видны записи из localStorage.
2. Переключение фильтра меняет отображаемый список без перезагрузки.
3. При пустом списке (после очистки localStorage) виден empty state, не пустая страница и не ошибка.
4. Все тексты UI — из `copy.js`, в JSX нет хардкоднутых строк.
5. Unit-тесты на `RecordList` и `StatusFilter` зелёные.

## DO NOT

- Не трогать `src/lib/storage.js` — только использовать существующие функции.
- Не добавлять создание / удаление / редактирование записей — это user stories U-4, U-5, U-6 из JTBD, идут в Sprint 2.
- Не добавлять анимации переключения фильтра — обсудим в отдельном спринте, если понадобится.
- Не менять структуру записи (ADR-002).
- Не править `src/pages/settings.jsx` и `src/pages/about.jsx` — они не в скоупе.
