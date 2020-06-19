#  Общие файлы конфигурации для инструментов авторов

Собираем здесь конфиги для спеллеров и линтеров. Любое изменение через пулл реквест с как минимум одним апрувом от каждого направления.

Установка:

```bash
npm install git+ssh://git@github.com:htmlacademy/configs.git --save-dev
```

## yaspeller

Ищет опечатки в материалах. Для настройки необходимо в своём репозитории указать путь к файлу конфигурации.

```json
{
    "scripts": {
        "spellcheck": "yaspeller --config ./node_modules/configs/yaspeller.json ."
    }
}
```

При необходимости можно расширить базовый [словарь](https://github.com/hcodes/yaspeller#--dictionary-file) в своём репе:

```json
{
    "scripts": {
        "spellcheck": "yaspeller --config ./node_modules/configs/yaspeller.json --dictionary js-3-dictionary.json ."
    }
}
```

_`js-3-dictionary.json` — дополняющий словарь из той же директории, где и `package.json`._
