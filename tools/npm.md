# NPM

Менеджер пакетов для JS.

## Где искать модули

* [npmjs.com](https://www.npmjs.com/)
* [npms.io](https://npms.io)

## Команды

### Обновление NPM

```bash
npm install npm -g
```

### paclage.json

```bash
npm init --yes
```

Генератор npm пакетов: [generator-nm](https://www.npmjs.com/package/generator-nm)

```bash
npm install -g yo generator-nm
```

### Зависимости

#### Установка новых зависимостей

* Для проекта: `npm install --save` или `npm install -S`
* Для сборки, тестирование и прочего: `npm install --save-dev` или `npm install -D`

#### Установка зависимостей

* `npm install` — установит все зависимости
* `npm install --production` — утановит только зависимости проекта (без `devDependencies`)

#### Чистка зависимостей

* `npm prune --production` — удалит все `devDependencies`

#### Фиксация зависимостей, что бы небыло сюрпризов

* `npm shrinkwrap` — фиксирует всё дерево зависимостей (создаёт файл `npm-shrinkwrap.json`)

[shrinkpack](https://www.npmjs.com/package/shrinkpack)

Утилита, которая скачивает архивы всех зависимостей в папку `node_shrinkwrap`, и обновляет `npm-shrinkwrap.json` что бы `npm` использовал её вместо сети.

`npm install --global shrinkpack`

#### Что обновлять

* `~1.0.0` — обновлять патчи
* `^1.0.0` — обновлять минорные и патчи
* `1.0.x` — обновлять `x`

Можно проверить, что скачается: [semver.npmjs.com](https://semver.npmjs.com/)

#### Проверка обновлений

* `npm outdated`

Полезный инструмент для полуавтоматического обновления [greenkeeper.io](https://greenkeeper.io)

### Таски

В секцию `scripts` файла `package.json` можно добавить свои таски, и выполнять их следующим образом:

```bash
npm run <taskName>
```

Поддерживается 4 шортката:

* `npm start`
* `npm stop`
* `npm restart`
* `npm test`

Важно!!! В тасках не нужно писать путь до исполняющегося файла в зависимостях. Вместо `./node_modules/.bin/webpack` достаточно просто написать `webpack`.

### Публикация

#### Обновление (поднятие) версии

* `npm version patch`
* `npm version minor`
* `npm version major`
* `npm version 2.0.0`

Эта команда делает следующее:

1. Создаёт коммит с увеличенной версией в `package.json`
2. Добавляет git тег с этой версией

#### Чеклист перед публикацией

1. Убедиться, что `master`
2. Посмотреть, что нет новых коммитов в `upstream`
3. Проверить, что все зависимости записаны в `package.json`
4. Тесты
5. Поднять версию `npm version`
6. Опубликовать `npm publish`
7. Запушить коммит и тег

Утилита, которая всё это проверяет: [np](https://www.npmjs.com/package/np)

## Разработка

Если вы одновременно изменяете два зависимых модуля, вам поможет `npm link`.

## Настройки (.npmrc)

* `cache-min=9999` — что бы реже смотрел в онлайн
* `loglevel=silent` — убирает логи из консоли
* `progress=false` — убирает прогресс бар (ускоряет установку)
* `save-exact=true` — сохраняет версию без `^`
* `ignore-scripts=true` — выключает выполнение `scripts` в `package.json` (вопрос безопасности)

## Ссылки

* Источник: [npm — найдётся подходящий модуль](https://www.youtube.com/watch?v=-moRyiijffU)
