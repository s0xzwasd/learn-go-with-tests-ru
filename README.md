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

### Создание приложения

После погружения в Go пришло время написать свое собственное приложения, используя полученные знания о большинстве важных аспектов языка и как применять TDD.

Каждая глава построена по принципу итеративности и зависит от предыдущей. Приложение обрастает новыми функции шаг за шагом.

Новые понятия будут представлены, чтобы научиться писать качественный код, но большинство материала будет зависеть от стандартных библиотек языка, которые были в предыдущей главе.

В конце главы вы получите полное представление о том, как писать программы на языке Go, покрытые при этом тестами, что особенно требуется для любого серьезного приложения.

* [HTTP-сервер](http-server.md) - Мы создадим приложение, которое получает HTTP-запросы и отвечает на них.
* [JSON, маршрутизация и вложения](json.md) - Мы создадим наши собственные запросы, которые возвращают JSON и разберемся как устроена маршрутизация HTTP-запросов.
* [IO и сортировка](io.md) - Мы сохраним и прочитаем наши данные с диска и научимся эти данные сортировать.
* [Командная строка и структура проекта](command-line.md) - Используем нашу кодовую базу для нескольких приложений и прочитаем ввод из командной строки.
* [Пакет time](time.md) - Установим активности на определенный период времени с помощью пакета `time`.
* [Веб-сокеты](websockets.md) - Узнаем как написать и протестировать сервер, который использует веб-сокеты.

### Частые вопросы и ответы

Я часто сталкиваюсь с популярным вопросом от моих студентов:

> Как я могу протестировать функцию, которая сначала делает x, затем y, а в конце z?

Если у вас есть подобные вопросы – заведите новый тикет на GitHub и я постараюсь найти время и написать маленькую главу о том, как решить эту проблему. Я чувствую, что такой контент ценнее, поскольку это настоящие проблемы вокруг тестирования.

* [Вызовы OS-команд](os-exec.md) - Пример как мы можем вызывать OS-команды для того, чтобы получить данные и сохранить нашу бизнес-логику способной для тестирования.
* [Создание собственных ошибок](error-types.md) - Пример как мы можем создавать собственные ошибки, чтобы улучшить тесты и сделать код удобным для дальнейшей работы.
* [Context-независимый Reader](context-aware-reader.md) - Узнаем как TDD дополняет `io.Reader` с отменой. Основываясь на статье ["Context-aware io.Reader for Go"](https://pace.dev/blog/2020/02/03/context-aware-ioreader-for-golang-by-mat-ryer).
* [Проектирование HTTP-хандлеров](http-handlers-revisited.md) - Тестирование HTTP-хандлеров кажется болью для большинства разработчиков. Мы найдем основные проблемы и научимся проектировать HTTP-хандлеров правильно.

### Дополнения / Обсуждения

* [Почему?](why.md) - Посмотрите видео или почитайте о том, почему юнит-тестирование и TDD важны.
* [Введение в дженерики](intro-to-generics.md) - Научитесь как писать функции которые принимают аргументы с дженериками и напишите свою собственную структуру данных.
* [Анти-паттерны](anti-patterns.md) - Маленькая глава об анти-паттернах в TDD и юнит-тестировании.

## Внести свой вклад в развитие проекта

* Данный _проект находится в стадии разработки_, поэтому не стесняйтесь связаться и предложить свои идеи.
* Прочитайте как правильно [контрибьютить](https://github.com/quii/learn-go-with-tests/tree/842f4f24d1f1c20ba3bb23cbc376c7ca6f7ca79a/contributing.md) в проект.
* Есть идеи? Создайте новый запрос!

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
