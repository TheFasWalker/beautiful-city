# clean-city

This template should help get you started developing with Vue 3 in Vite.

## Recommended IDE Setup

[VSCode](https://code.visualstudio.com/) + [Volar](https://marketplace.visualstudio.com/items?itemName=Vue.volar) (and disable Vetur).

## Customize configuration

See [Vite Configuration Reference](https://vitejs.dev/config/).

## Project Setup

```sh
npm install
```

### Compile and Hot-Reload for Development

```sh
npm run dev
```

### Compile and Minify for Production

```sh
npm run build
```


Задание необходимо выполнить на Vue
1. Собрать приложение для просмотра сообщений и комментариев к ним на основе данных сервиса jsonplaceholder

1. posts
2. comments
3. users
2. Не использовать библиотеки готовых компонентов типа vuetify

3. Приложение должно включать таблицу сообщений и форму редактирования.

1. Таблица сообщений:
■ Должна быть сгруппирована по авторам.
■ Группы должны интерактивно скрываться и раскрываться.
■ В группе показывать данные пользователя: id, username, name, company.name, website
■ Для сообщения показывать id, title, words, chars . Последние два параметра рассчитывать при отображении
2. Форма редактирования должна содержать:
■ Id сообщения
■ Поля для редактирования title, body
■ Список комментариев, для каждого: email, name, body
