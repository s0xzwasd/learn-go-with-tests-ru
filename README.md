# Изучите Go через тестирование

<p>
  <img src="red-green-blue-gophers-smaller.png"  alt="Три гофера разных цветов: один думает о еде, другой готовит, третий убирает. Надпись: Red, Green, Refactor."/>
</p>

[Обложка нарисована Denise](https://twitter.com/deniseyu21)

[![Go Report Card](https://goreportcard.com/badge/github.com/quii/learn-go-with-tests)](https://goreportcard.com/report/github.com/quii/learn-go-with-tests)

## Форматы для чтения

- [Gitbook](https://s0xzwasd.gitbook.io/learn-go-with-tests/)
- [EPUB or PDF](https://github.com/s0xzwasd/learn-go-with-tests/releases)

## Доступные переводы

- [English](https://quii.gitbook.io/learn-go-with-tests)
- [中文](https://studygolang.gitbook.io/learn-go-with-tests)
- [Português](https://larien.gitbook.io/aprenda-go-com-testes/)
- [日本語](https://andmorefine.gitbook.io/learn-go-with-tests/)
- [한국어](https://miryang.gitbook.io/learn-go-with-tests/)
- [Türkçe](https://halilkocaoz.gitbook.io/go-programlama-dilini-ogren/)

## Поддержите меня

Я горжусь тем, что предлагаю эту книгу для свободного использования, бесплатно. Однако, если вы хотите поддержать меня или выразить благодарность, то можете воспользоваться следующими пунктами:

- [Отметьте меня в Твиттере: @quii](https://twitter.com/quii)
- [Купите чашку кофе :coffee:](https://www.buymeacoffee.com/quii)
- [Поддержите проект на GitHub](https://github.com/sponsors/quii)

## Почему мне стоит это читать?

* Узнайте о языке Go с помощью написания тестов.
* **Погрузитесь в TDD с головой**. Go хороший язык для этого, потому-что он прост для изучения и в нём отлично реализованы тесты из коробки.
* Получите уверенность, что вы можете писать надежные и хорошо протестированные системы на Go.
* [Посмотрите видео или почитайте](why.md), почему юнит-тестирование и TDD важны.

## Оглавление

### Основы Go

1. [Установка Go](install-go.md) - Настройте рабочее окружение для комфортной работы.
2. [Привет, мир!](hello-world.md) - Объявляйте переменные, константы, используйте ветвления, напишите вашу первую программу на Go и тест для неё. Синтаксис подтестов и замыканий.
3. [Числа](integers.md) - Укрепите знания синтаксиса для функций и изучите новые пути улучшения документации вашего кода.
4. [Циклы](iteration.md) - Узнайте о цикле `for` и для чего нужны бенчмарки.
5. [Массивы и Слайсы](arrays-and-slices.md) - Научитесь работать с массивами, слайсами, `len`, `range`, изучите вариативные функции и покройте тестами программу.
6. [Структуры, методы и интерфейсы](structs-methods-and-interfaces.md) - Погрузитесь в методы, узнайте об интерфейсах, структурах и табличных тестах.
7. [Указатели и ошибки](pointers-and-errors.md) - Узнайте об указателях и обработке ошибок в Go.
8. [Карты](maps.md) - Научитесь пользоваться картами для хранения данных.
9. [Управление зависимостями](dependency-injection.md) - Получите представления об управлении зависимости и как это связано с использованием интерфейсов и пакета `io`.
10. [Мокинг (имитация)](mocking.md) - Возьмите существующий не протестированный код и используйте DI с мокингом для написания тестов.
11. [Многопоточность](concurrency.md) - Узнайте как писать многопоточный код и как сделать вашу программу быстрее.
12. [Оператор Select](select.md) - Научитесь красиво и элегантно синхронизировать асинхронные процессы.
13. [Рефлексия](reflection.md) - Получите основы о рефлексии в Go.
13. [Синхронизация](sync.md) - Узнайте о пакете `sync`, который включает в себя `WaitGroup` и `Mutex`.
13. [Использование context](context.md) - Используйте пакет `context` для управления и закрытия долгих процессов.
14. [Property-based testing (использование предикатов)](roman-numerals.md) - Попрактикуйтесь в TDD с помощью Roman Numerals заданий и получите основы PBT.
15. [Использование math](math.md) - Научитесь использовать пакет `math` и нарисуйте часы с использованием SVG.
16. [Чтение файлов](reading-files.md) - Читайте файлы и обрабатывайте их.

### Build an application

Now that you have hopefully digested the _Go Fundamentals_ section you have a solid grounding of a majority of Go's language features and how to do TDD.

This next section will involve building an application.

Each chapter will iterate on the previous one, expanding the application's functionality as our product owner dictates.

New concepts will be introduced to help facilitate writing great code but most of the new material will be learning what can be accomplished from Go's standard library.

By the end of this, you should have a strong grasp as to how to iteratively write an application in Go, backed by tests.

* [HTTP server](http-server.md) - We will create an application which listens to HTTP requests and responds to them.
* [JSON, routing and embedding](json.md) - We will make our endpoints return JSON and explore how to do routing.
* [IO and sorting](io.md) - We will persist and read our data from disk and we'll cover sorting data.
* [Command line & project structure](command-line.md) - Support multiple applications from one code base and read input from command line.
* [Time](time.md) - using the `time` package to schedule activities.
* [WebSockets](websockets.md) - learn how to write and test a server that uses WebSockets.

### Questions and answers

I often run in to questions on the internets like

> How do I test my amazing function that does x, y and z

If you have such a question raise it as an issue on github and I'll try and find time to write a short chapter to tackle the issue. I feel like content like this is valuable as it is tackling people's _real_ questions around testing.

* [OS exec](os-exec.md) - An example of how we can reach out to the OS to execute commands to fetch data and keep our business logic testable/
* [Error types](error-types.md) - Example of creating your own error types to improve your tests and make your code easier to work with.
* [Context-aware Reader](context-aware-reader.md) - Learn how to TDD augmenting `io.Reader` with cancellation. Based on [Context-aware io.Reader for Go](https://pace.dev/blog/2020/02/03/context-aware-ioreader-for-golang-by-mat-ryer)
* [Revisiting HTTP Handlers](http-handlers-revisited.md) - Testing HTTP handlers seems to be the bane of many a developer's existence. This chapter explores the issues around designing handlers correctly.

### Meta / Discussion

* [Why](why.md) - Watch a video, or read about why unit testing and TDD is important
* [Intro to generics](intro-to-generics.md) - Learn how to write functions that take generic arguments and make your own generic data-structure
* [Anti-patterns](anti-patterns.md) - A short chapter on TDD and unit testing anti-patterns

## Contributing

* _This project is work in progress_ If you would like to contribute, please do get in touch.
* Read [contributing.md](https://github.com/quii/learn-go-with-tests/tree/842f4f24d1f1c20ba3bb23cbc376c7ca6f7ca79a/contributing.md) for guidelines
* Any ideas? Create an issue

## Background

I have some experience introducing Go to development teams and have tried different approaches as to how to grow a team from some people curious about Go into highly effective writers of Go systems.

### What didn't work

#### Read _the_ book

An approach we tried was to take [the blue book](https://www.amazon.co.uk/Programming-Language-Addison-Wesley-Professional-Computing/dp/0134190440) and every week discuss the next chapter along with the exercises.

I love this book but it requires a high level of commitment. The book is very detailed in explaining concepts, which is obviously great but it means that the progress is slow and steady - this is not for everyone.

I found that whilst a small number of people would read chapter X and do the exercises, many people didn't.

#### Solve some problems

Katas are fun but they are usually limited in their scope for learning a language; you're unlikely to use goroutines to solve a kata.

Another problem is when you have varying levels of enthusiasm. Some people just learn way more of the language than others and when demonstrating what they have done end up confusing people with features the others are not familiar with.

This ends up making the learning feel quite _unstructured_ and _ad hoc_.

### What did work

By far the most effective way was by slowly introducing the fundamentals of the language by reading through [go by example](https://gobyexample.com/), exploring them with examples and discussing them as a group. This was a more interactive approach than "read chapter x for homework".

Over time the team gained a solid foundation of the _grammar_ of the language so we could then start to build systems.

This to me seems analogous to practicing scales when trying to learn guitar.

It doesn't matter how artistic you think you are, you are unlikely to write good music without understanding the fundamentals and practicing the mechanics.

### What works for me

When _I_ learn a new programming language I usually start by messing around in a REPL but eventually, I need more structure.

What I like to do is explore concepts and then solidify the ideas with tests. Tests verify the code I write is correct and documents the feature I have learned.

Taking my experience of learning with a group and my own personal way I am going to try and create something that hopefully proves useful to other teams. Learning the fundamentals by writing small tests so that you can then take your existing software design skills and ship some great systems.

## Для кого эта книга

* Любому, кто заинтересовался в изучении Go.
* Любому, кто уже немного знаком с Go, но хочет изучить TDD подход.

## Что мне потребуется для прохождения?

* Компьютер и установленный терминал, которым вы хорошо пользуетесь.
* Установленный [Go](https://golang.org/).
* Текстовый редактор кода.
* Небольшие познания в программировании. Понимание концепции ветвлений, что такое переменная, функция и т.д

## Обратная связь

* Создавайте новые тикеты/предлагайте изменения [здесь](https://github.com/s0xzwasd/learn-go-with-tests) или отметьте меня в [Twitter](https://twitter.com/quii).

[Лицензия MIT](LICENSE.md)

[Логотип нарисовал egonelbre](https://github.com/egonelbre), спасибо!
