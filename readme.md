# Общие файлы конфигурации для инструментов авторов

Собираем здесь конфиги для спеллеров и линтеров. Любое изменение через пулл реквест с как минимум одним апрувом от каждого направления.

## Установка

<details>
  <summary>Перед установкой</summary>

Перед установкой пакета необходимо настроить NPM, указав альтернативный репозиторий пакетов — GitHub Packages.

### Получение Personal Access Token <sup>[Справка ↗](https://docs.github.com/en/github/authenticating-to-github/creating-a-personal-access-token)</sup>

Для поиска и установки пакетов при создании токена необходимо выбрать область действия токена:

- [x] read:packages

Если необходима возможность обновлять пакеты в дальнейшем, следует дополнительно выбрать область действия токена:

- [x] write:packages

### Аутентификация с использованием Personal Access Token <sup>[Справка ↗](https://docs.github.com/en/packages/guides/configuring-npm-for-use-with-github-packages#authenticating-with-a-personal-access-token)</sup>

#### C помощью конфигурационных файлов:

- Создать файл `.npmrc` в домашней директории пользователя и добавить в него строку:

  ```bash
  //npm.pkg.github.com/:_authToken=TOKEN
  ```

- Создать файл `.npmrc` в директории репозитория и добавить в него строку:

  ```bash
  registry=https://npm.pkg.github.com/htmlacademy
  ```

#### С помощью инструментов командной строки npm:

- Воспользоваться командой `npm login` с флагом `scope`, который добавит к результатам поиска пакеты указанного разработчика из GitHub Packages:

  ```bash
  $ npm login --scope=@htmlacademy --registry=https://npm.pkg.github.com

  > Username: USERNAME
  > Password: TOKEN
  > Email: PUBLIC-EMAIL-ADDRESS
  ```

  Когда терминал запросит `USERNAME`, `TOKEN` и `PUBLIC-EMAIL-ADDRESS` — введите ваши значения.

</details>

```bash
npm install -DE @htmlacademy/configs
```

## Возможности

### yaspeller

Ищет опечатки в материалах. Для настройки необходимо в своём репозитории указать путь к файлу конфигурации.

```json
{
    "scripts": {
        "spellcheck": "yaspeller --config ./node_modules/@htmlacademy/configs/yaspeller.json ."
    }
}
```

При необходимости можно расширить базовый [словарь](https://github.com/hcodes/yaspeller#--dictionary-file) в своём репе:

```json
{
    "scripts": {
        "spellcheck": "yaspeller --config ./node_modules/@htmlacademy/configs/yaspeller.json --dictionary js-3-dictionary.json ."
    }
}
```

_`js-3-dictionary.json` — дополняющий словарь из той же директории, где и `package.json`._

### markdownlint-cli

CLI для линтера `Markdown`-файлов. Правит файлы в соответствии с конфигом `.markdownlint.yml`. Все правила линтера описаны в [документации markdownlint](https://github.com/DavidAnson/markdownlint/blob/main/doc/Rules.md#md048). При необходимости можно настраивать правила или отключать ненужные.

Найдёт ошибки и выведет их в консоль:

```json
{
    "scripts": {
        "markdownlint": "markdownlint --config ./node_modules/@htmlacademy/configs/.markdownlint.yml ."
    }
}
```

Автоматически исправит найденные ошибки:

```json
{
    "scripts": {
        "markdownlint:fix": "markdownlint --fix ./.markdownlint.yml ."
    }
}
```
