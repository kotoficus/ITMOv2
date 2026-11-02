# Spec Kit для практики 5

Рабочий корень — `practices/practice_05`, Git-ветка — `practice_05`.
Активная спецификация указана в `feature.json`; отдельная Git-ветка с
числовым префиксом не создаётся.

Использованы официальные шаблоны и workflow
[github/spec-kit](https://github.com/github/spec-kit/tree/7370e592f3cd9c06e5b698983957e227c75b30e2),
коммит `7370e592f3cd9c06e5b698983957e227c75b30e2`:

- `templates/spec-template.md` и `templates/commands/specify.md`;
- `templates/plan-template.md` и `templates/commands/plan.md`;
- `scripts/bash/resolve-template.sh` и `scripts/bash/setup-plan.sh`.

Два шаблона сохранены в `templates/` без изменений. Команды подготовки
выполнены из временной копии этого коммита с `SPECIFY_INIT_DIR`, указывающим
на корень практики. Шаблон Spec получен через resolver, а Plan создан
официальным setup-script. Содержательные документы заполняет агент.
Полный Specify CLI и интеграция команд в клиент не устанавливались;
это применение шаблонов и процесса Spec Kit, а не отчёт о запуске
несуществующих в этой сессии slash-команд.

Лицензия сохранённых материалов: [MIT](LICENSE.spec-kit).

Файла `extensions.yml` нет, поэтому hooks before/after Specify и Plan
отсутствуют. Overrides и presets не настроены.

Созданы Spec, checklist и результаты Plan: research, data model, contracts,
quickstart. Tasks и код относятся к следующим этапам и пока не созданы.
