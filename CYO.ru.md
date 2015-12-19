Пару слов о тестах. В проекте остались только два вида тестов: тесты функции Mustache.render и тесты отдельных компонентов библиотеки (в том числе и Mustache.render).
Чтобы их выполнить, запускаем команды:
`npm run test-render`

`npm run test` (или просто `npm test`)

Первая команда сразу говорит нам:
`TypeError: Mustache.clearCache is not a function`,
а сами тесты даже не стартуют.

Первый шаг к тому, чтобы получить работающие тесты - реализовать все функции, на отсутствие которых тесты ругаются. Начнем как раз с `Mustache.clearCache`:

```
var Mustache = {};

Mustache.clearCache = function() {};

module.exports = Mustache;
```

Теперь при выполнении `npm run test-render` мы получаем другую ошибку:
```TypeError: Mustache.render is not a function```
а значит, нужно реализовать и ее:
```
Mustache.render = function() { return ''; };
```
После чего вывод 