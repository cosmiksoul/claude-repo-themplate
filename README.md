# Web Dev Template для двухинстансной работы с Claude

Шаблон документации и процесса для веб-проекта, разрабатываемого парой инстансов:

- **Cowork** (Claude Cowork) — роль PM/Architect: планирование, документация, code review, тест-кейсы
- **Code** (Claude Code) — роль Developer: реализация, sprint-reports

Пользователь — Product Owner, Designer и QA в одном лице.

Процесс — адаптация и обобщение моего цикла разработки с Claude (`Dev-Cycle.md`). Подходит для веб-проектов любого небольшого размера, разрабатываемых соло-разработчиком вечерами по спринтам в 2-5 дней работы.

## Что в пакете

```
<project>/
├── CLAUDE.md                          ← корневой, читают оба инстанса
├── docs/
│   ├── project/
│   │   ├── Dev-Cycle.md               ← цикл разработки, 9 фаз
│   │   ├── Cowork-Onboarding.md       ← вход в проект для Cowork
│   │   ├── Code-Onboarding.md         ← вход в проект для Claude Code
│   │   ├── JTBD.md                    ← backlog user stories
│   │   └── CONTEXT.md                 ← история проекта, timeline
│   └── context/
│       ├── concept.md                 ← заполнить: зачем продукт
│       ├── architecture.md            ← заполнить: стек, структура
│       └── decisions-log.md           ← пустой, наполнять ADR по ходу
```

## Как запустить новый проект

1. Скопировать всё в корень проекта.
2. Заполнить плейсхолдеры `<project>`, `<short-pitch>`, `<stack>` в:
   - `CLAUDE.md`
   - `docs/context/concept.md`
   - `docs/context/architecture.md`
3. Сделать первичный набросок `JTBD.md` (можно черновой — Cowork доработает в первом PLAN).
4. Открыть инстанс Cowork → "Прочитай `docs/project/Cowork-Onboarding.md`, давай начнём". Дальше работа по `Dev-Cycle.md`.
5. Когда дойдёшь до фазы DEV первого спринта — открыть инстанс Claude Code → "Прочитай `docs/project/Code-Onboarding.md`, дальше работаем по `sprint-1-prompt.md`".

## Что НЕ входит в пакет

- Шаблоны `sprint-N-prompt.md`, `sprint-report-N.md`, `code-review-sprint-N.md`, `test-cases-sprint-N.md` — это **артефакты процесса**, которые Cowork (и Code для report) генерируют сами по инструкциям из `Dev-Cycle.md`. Туда зашиты шаблоны.
- билды / код / принципы деплоя — это часть конкретного проекта, не процесса.

## Что обновлять по ходу проекта

- `JTBD.md` — Cowork обновляет в фазе CLOSE каждого спринта (чек-боксы реальное состояние).
- `CONTEXT.md` — Cowork добавляет запись в Timeline после каждого CLOSE.
- `decisions-log.md` — пополняется новыми ADR по результатам обсуждений (Cowork формирует, ты утверждаешь).
- `CLAUDE.md` — обновляется когда появляются новые anti-patterns или меняются project-specific правила.
- `concept.md`, `architecture.md` — пополняются по мере вызревания решений.

## Принцип

> Cowork и Code — разные инстансы с разным контекстом.
> Cowork **не трогает код**. Code **не занимается планированием и архитектурой**.
> Пользователь — единственный источник продуктовых решений и единственный, кто видит реальный результат на устройстве.
