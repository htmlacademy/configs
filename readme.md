#  Общие файлы конфигурации для инструментов авторов

Собираем здесь конфиги для спеллеров и линтеров. Любое изменение через пулл реквест с как минимум одним апрувом от каждого направления.

Установка:

```bash
npm install git+ssh://git@github.com:htmlacademy/configs.git --save-dev
```

## yaspeller

Ищет опечатки в материалах. Для настройки необходимо в репозитории курса указать путь к файлу конфигурации.

```json
{
    "scripts": {
        "spellcheck": "yaspeller --config ./node_modules/configs/yaspeller.json ."
    }
}
```

При необходимости можно завести [словарь](https://github.com/hcodes/yaspeller#--dictionary-file) конкретного курса и расширить общий:

```json
{
    "scripts": {
        "spellcheck": "yaspeller --config ./node_modules/configs/yaspeller.json --dictionary js-3-dictionary.json ."
    }
}
```

_`js-3-dictionary.json` — словарь конкретного курса в той же директории, где и `package.json`._
