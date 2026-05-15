# Sprint Logs — примеры артефактов

> Это **демонстрационные примеры** того, как выглядят артефакты процесса по ходу одного спринта. В реальном проекте эти файлы лежат прямо в `docs/project/` (не в подпапке) и **генерируются Cowork и Claude Code** по ходу работы, как описано в `Dev-Cycle.md`.
>
> Цель этой папки — показать на сквозном примере, как одна фича проходит через цикл: prompt → report → review → test-cases.

## Что внутри

| Файл | Кто пишет | На какой фазе |
|---|---|---|
| `sprint-1-prompt.md` | Cowork | Фаза 2: PROMPT (до старта разработки) |
| `sprint-report-1.md` | Claude Code | Фаза 3: DEV (после реализации) |
| `code-review-sprint-1.md` | Cowork | Фаза 4: CODE REVIEW (до QA) |
| `test-cases-sprint-1.md` | Cowork → пользователь | Фаза 5: TEST PREP, заполняется в Фазу 6: QA |

Сценарий примера — `Sprint 1: главная страница со списком записей и фильтром по статусу`. Сам код в этой папке не лежит, только артефакты процесса.

## Чего здесь нет

- `sprint-N-fix-prompt.md`, `sprint-N-fix-report.md` — артефакты фазы FIX (когда в QA нашлись баги). Шаблон в `Dev-Cycle.md`.
- `sprint-N-design.md` — артефакт Architecture sprint'а. Шаблон в `Dev-Cycle.md`.
- `content-N-review.md` — артефакт Content sprint'а. Шаблон в `Dev-Cycle.md`.

Эти типы спринтов разобраны в `Dev-Cycle.md`, отдельные демо для них не делал, чтобы не плодить файлы.
