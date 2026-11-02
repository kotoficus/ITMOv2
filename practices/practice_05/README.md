# Практика 5. SDD в существующем проекте

Условие: [презентация](prenetation.pdf). Рабочая ветка: `practice_05`.
Проект: калькулятор из выполненной практики 4, ветка `practice-04`,
коммит `47b8263`. Исходные модуль и тесты перенесены в эту папку,
чтобы практика воспроизводилась отдельно, без переноса MCP и зависимостей.

## Текущее состояние

Согласованы развитие в три этапа (парсер, комплексная арифметика, история
JSON с Undo), разделение парсинга/вычисления и комплексный тип с `im = 0`
для вещественных значений. По текущему запросу подготовлены **Spec и Plan
первой части**, объединяющей парсер и комплексную арифметику:

- [Spec: поведение, сценарии и приёмка](specs/001-complex-expression-calculator/spec.md).
- [Plan: модули, последовательность и проверки](specs/001-complex-expression-calculator/plan.md).
- [Контракт результата и ошибок](specs/001-complex-expression-calculator/contracts/calculation.md).
- [Грамматика](specs/001-complex-expression-calculator/contracts/grammar.md).
- [Будущее поведение истории и Undo](specs/001-complex-expression-calculator/contracts/history.md).
- [Research](specs/001-complex-expression-calculator/research.md),
  [data model](specs/001-complex-expression-calculator/data-model.md),
  [quickstart](specs/001-complex-expression-calculator/quickstart.md),
  [checklist](specs/001-complex-expression-calculator/checklists/requirements.md).
- [Происхождение шаблонов Spec Kit](.specify/README.md) и
  [фактическая проверка планирования](evidence/spec-kit-planning.md).

Модули нового ядра и их тесты пока не создавались. Текущий код — исходный
калькулятор из практики 4; [baseline](evidence/baseline.txt) содержит его
7 тестов. Будущие команды в quickstart обозначены отдельно от выполненных.

Прежний OpenSpec-черновик `validate-calculator-input` заменён новым scope,
оставлен для истории подготовки и не должен переходить в apply.
Его наличие не означает реализацию, приёмку или archive. Окружение OpenSpec
сохранено; Spec Kit используется как другой SDD-фреймворк для ДЗ.

## Проверка

Из этой папки:

```sh
npm test
```

Зависимости для калькулятора не нужны. Требуется Node.js с `node:test`;
для OpenSpec 1.14.1 презентация указывает Node.js >=20.19.0.
Фактическое окружение: Node.js v26.10.0, npm 11.19.1.

### Ранее подготовленное окружение OpenSpec

OpenSpec для практической части можно установить командой из задания:

```sh
npm install -g @fission-ai/openspec@1.14.1
openspec --version
openspec list --json
openspec validate validate-calculator-input --type change --strict --no-interactive
```

При подготовке использована временная установка того же пакета,
без изменения глобальных пакетов пользователя.

## Следующие этапы

После просмотра текущего Spec/Plan: Tasks и реализация двух инкрементов
первой части с проверками. Затем — история JSON и Undo, UI и сквозная
проверка по общему контракту. Текущий запрос ограничен планированием.

Полное задание презентации ещё не закрыто: предстоят отдельные
спецификации команд UI/логики до/после согласования, независимые проверки,
работающее демо и рефлексия. Отдельно остаются практические шаги OpenSpec
(полный цикл принятого изменения и правило config с фрагментом до/после).
Наличие документов не выдаётся за выполнение этих этапов.
