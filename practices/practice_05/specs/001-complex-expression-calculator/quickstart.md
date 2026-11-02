# Quickstart и проверка первой части

## Что существует сейчас

Подготовлены документы. `src/expression.js` и новые тесты ещё не существуют.
Ниже отдельно описаны текущая проверка и ожидаемые команды после реализации;
их результаты не выданы за фактические.

Из корня репозитория:

```sh
cd practices/practice_05
npm test
```

Текущий baseline: 7 тестов исходного калькулятора. Новые зависимости
приложения не нужны.

## После реализации по Spec/Plan

Предпосылки: Node.js >=20.19.0, папка `practices/practice_05`, реализованы
модули и соответствующие тесты из Plan. Полная проверка: `npm test`.

Условия успеха: 7 прежних тестов, A01–A14, E01–E11 и модульные проверки
матрицы Plan проходят. Количество тестов само по себе не доказывает
покрытие сценариев.

## Сквозные примеры через публичный фасад

Команды ниже предназначены **для будущей реализации**:

```sh
node --input-type=module -e 'import { calculate } from "./src/expression.js"; console.log(JSON.stringify(calculate("(2+3)*4")))'
```

Ожидается `{"ok":true,"value":{"re":20,"im":0},"text":"20"}`.

```sh
node --input-type=module -e 'import { calculate } from "./src/expression.js"; console.log(JSON.stringify(calculate("(1+2i)*(3-4i)")))'
```

Ожидается `{"ok":true,"value":{"re":11,"im":2},"text":"11 + 2i"}`.

```sh
node --input-type=module -e 'import { calculate } from "./src/expression.js"; console.log(JSON.stringify(calculate("2+")))'
```

Ожидается `SYNTAX_ERROR`, сообщение `Некорректное выражение.`,
`span: {start: 2, end: 2}`; полей `value` и `text` нет.

```sh
node --input-type=module -e 'import { calculate } from "./src/expression.js"; console.log(JSON.stringify(calculate("1/(i-i)")))'
```

Ожидается `DIVISION_BY_ZERO`, сообщение `Деление на ноль.`,
`span: {start: 2, end: 7}`. Следующий отдельный вызов с `2+2` успешен.

Прямую арифметику без парсера проверяет будущий `tests/complex.test.js`.
Полные схемы и грамматика описаны в `contracts/`; кода реализации здесь нет.

## История

Команд записи и Undo в этой части нет. Будущий сценарий записан
в [history.md](contracts/history.md); он не относится к приёмке этой части.
