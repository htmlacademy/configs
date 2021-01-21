#  Общие файлы конфигурации для инструментов авторов

Собираем здесь конфиги для спеллеров и линтеров. Любое изменение через пулл реквест с как минимум одним апрувом от каждого направления.

## Установка:

Перед установкой пакета необходимо настроить NPM, указав альтернативный репозиторий пакетов — GitHub Packages.

### Получение Personal Access Token

[Справка на GitHub Docs](https://docs.github.com/en/github/authenticating-to-github/creating-a-personal-access-token)

Для поиска и установки пакетов при создании токена необходимо выбрать область действия токена:
- [x] read:packages

Если необходима возможность обновлять пакеты в дальнейшем, следует дополнительно выбрать область действия токена:
- [x] write:packages

### Аутентификация с использованием Personal Access Token

[Справка на GitHub Docs](https://docs.github.com/en/packages/guides/configuring-npm-for-use-with-github-packages#authenticating-with-a-personal-access-token)

* Первый вариант — с помощью конфигурационных файлов:

  * Создать файл `.npmrc` в домашней директории пользователя и добавить в него строку:

  ```bash
  //npm.pkg.github.com/:_authToken=TOKEN
  ```

  * Создать файл `.npmrc` в директории репозитория и добавить в него строку:

  ```bash
  registry=https://npm.pkg.github.com/htmlacademy
  ```

* Второй вариант — с помощью инструментов командной строки npm:

  * Воспользоваться командой `npm login` с флагом `scope`, который добавит к результатам поиска пакеты указанного разработчика из GitHub Packages:

  ```bash
  $ npm login --scope=@htmlacademy --registry=https://npm.pkg.github.com

  > Username: USERNAME
  > Password: TOKEN
  > Email: PUBLIC-EMAIL-ADDRESS
  ```

N.B. `TOKEN` заменить на полученный на предыдущем шаге.

### Установка пакета

```bash
npm install -DE @htmlacademy/configs
```

## yaspeller

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
