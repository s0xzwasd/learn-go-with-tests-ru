# Привет, мир!

**Весь код для этой главы вы можете найти [здесь](https://github.com/s0xzwasd/learn-go-with-tests-ru/tree/main/hello-world)**.

Программирование на любом языке начинается с [Hello, World](https://en.m.wikipedia.org/wiki/%22Hello,_World!%22_program).

- Создайте новую директорию в любом месте на вашем компьютере.
- Создайте новый файл `hello.go ` и вставьте в него следующий код:

```go
package main

import "fmt"

func main() {
	fmt.Println("Hello, world")
}
```

Затем запустите данный код командой `go run hello.go`.

## Как это устроено?

Когда вы пишете программы на Go, у вас должен быть пакет `main` с объявленной внутри одноименной функцией. Пакеты это способ группировки связанного кода вместе.

Ключевое слово `func` это объявление функции, которое состоит из имени и тела.

С помощью `import "fmt"` мы импортируем пакет, который содержит функцию `Println` и она необходима нам, чтобы вывести сообщение на экран.

## Как это протестировать?

Итак, как можно протестировать данную часть кода? Хорошая практика разделять собственный код от основного мира, чтобы избежать сайд-эффектов. Строка, которую мы передаем в функцию, является нашим кодом, а `Println` сайд-эффектом и выводит результат на экран.

Давайте разделим эти две сущности для удобства тестирования:

```go
package main

import "fmt"

func Hello() string {
	return "Hello, world"
}

func main() {
	fmt.Println(Hello())
}
```

Мы создали еще одну функцию с использованием `func`, но сейчас мы также добавили еще одно ключевое слово `string` в объявлении. Это значит, что функция должна возвращать тип данных `string`.

Теперь создадим новый файл `hello_test.go`, где напишем тест для нашей функции `Hello`.

```go
package main

import "testing"

func TestHello(t *testing.T) {
	got := Hello()
	want := "Hello, world"

	if got != want {
		t.Errorf("got %q want %q", got, want)
	}
}
```

## Go модули?

Следующим шагом будет запуск самих тестов. Введите `go test` в интерфейсе командной строки. Если тесты отмечены как пройденные, тогда вы скорее всего используете устаревшею версию Go. Однако, если вы используете Go версии 1.16 и выше, то тогда тесты не должны совсем запуститься. Вместо этого, вы должны увидеть следующее сообщение:

```shell
$ go test
go: cannot find main module; see 'go help modules'
```

В чем проблема? Если коротко, в [модулях](https://blog.golang.org/go116-module-changes). К счастью, проблему легко исправить. Введите `go mod init` в терминале. Команда создаст новый файл с содержимым:

```
module hello

go 1.16
```

Этот файл передает инструментам `go` основную информацию о вашем проекте. Если вы планируете выкладывать ваше приложение, к примеру на Github, вам нужно включить информацию об этом, а также информацию о зависимостях проекта. На данный момент файл содержит минимальное количество данных, и вы можете оставить его в таком виде. Для большего изучения модулей, вы можете обратиться к соответствующему разделу в [документации](https://golang.org/doc/modules/gomod-ref). Теперь вернемся к тестированию и изучению Go, поскольку теперь тесты должны запуститься даже на 1.16 версии Go.

В следующих разделах вам нужно выполнить `go mod init name` самостоятельно в каждой новой директории перед выполнением команд `go test` и `go build`

## Вернемся к тестированию

Запустите `go test` в вашем терминале. Тесты должны пройти успешно! Для убедительности попробуйте "сломать" тест изменив содержимое строки в `want`.

Обратите внимание, что вам не нужно выбирать между несколькими фреймворками для тестирования и затем разбираться с их установкой. В Go вам нужно использовать встроенные инструменты языка и писать тесты с тем же синтаксисом, как и остальной код.

### Написание тестов

Написание тестов это как написание обычных функций, где действует несколько правил:

* Тест должен находится в файле с именем `*_test.go`
* Название функции должно начинаться с ключевого слова `Test`
* Функция принимает только один аргумент: `t *testing.T`
* Для того чтобы использовать тип `t *testing.T`, вам нужно импортировать пакет `import "testing"` как мы уже делали для `fmt` в предыдущем примере

На данный момент достаточно знать что `t` с типом `*testing.T` это ваш указатель на то, чтобы использовать тестовый фреймворк и вы можете использовать `t.Fail()`, чтобы тест был отмечен как не пройденный.

Мы также рассмотрели несколько новых понятий:

#### `if`

Условные ветвления в Go очень похожи на реализацию в других языках.

#### Declaring variables Объявление переменных

Мы объявляем какие-то переменные с помощью синтаксиса `varName := value`, который помогает нам переиспользовать какие-то значения в наших тестах и повышает читаемость кода.

#### `t.Errorf`

Мы вызываем `Errof` _метод_ на аргументе `t` когда хотим вывести сообщение и провалить тест. Буква `f` отвечает за форматирование, которое позволяет нам создать строку и вставить в неё значения с помощью плейсхолдеров `%q`. Когда вы отмечаете тест как провальный, вам следует знать как это работает.

Вы можете прочитать о плейсхолдерах в строках в [документации](https://golang.org/pkg/fmt/#hdr-Printing). Для тестов `%q` очень полезно, поскольку он оборачивает ваши значения в двойные кавычки.

В дальнейшем мы рассмотрим разницу между функциями и методами.

### Документация

Другая сильная сторона Go – документация. Вы можете открыть её локально запустив `godoc -http :8000`. Затем, если вы перейдете на [localhost:8000/pkg](http://localhost:8000/pkg), то увидите список всех пакетов, установленных на вашем устройстве.

Основная сила стандартных библиотек это отличная документация с примерами. Перейдите к [http://localhost:8000/pkg/testing/](http://localhost:8000/pkg/testing/) и посмотрите, какое количество полезной и качественной информации доступно для вас.

Если вам не удается запустить `godoc` команду, тогда вы используете Go версии 1.14 и выше, поэтому утилита [не включена по-умолчанию](https://golang.org/doc/go1.14#godoc). Вы можете установить `godoc` самостоятельно с помощью `go install golang.org/x/tools/cmd/godoc`.

### Привет, USERNAME

Теперь у нас есть тест и мы можем продолжать улучшать свой код безопасно.

В последнем примере мы написали тест после основного кода лишь для примера чтобы показать как пишутся тесты и объявляются функции. С этого момента _мы начинаем писать сначала тесты_, а потом основной код.

Следующим заданием будет возможность указать получателя приветствия.

Давайте соберем все требования в тест. Это базы TDD, которые позволяют нам убедится в том, что наш тест _действительно_ проверяет то, что мы хотим. Когда вы сначала пишете код, а затем тесты, всегда есть риск того что ваши тесты могут отображаться как пройденные даже в случае, если код не работает как задумано.

```go
package main

import "testing"

func TestHello(t *testing.T) {
	got := Hello("Chris")
	want := "Hello, Chris"

	if got != want {
		t.Errorf("got %q want %q", got, want)
	}
}
```

Теперь запустим `go test` и вы должны получить следующую ошибку компиляции:

```text
./hello_test.go:6:18: too many arguments in call to Hello
    have (string)
    want ()
```

Когда мы работаем с языком со статической типизацией, важно слушать что говорит компилятор. Компилятор понимает как ваш код должен взаимодействовать и работать.

В этом случае компилятор говорит нам, что нужно сделать. Требуется изменить нашу функцию `Hello`, чтобы она принимала аргумент.

Изменив функцию `Hello`, чтобы она принимала аргумент с типом `string`:

```go
func Hello(name string) string {
	return "Hello, world"
}
```

Если вы попробуете запустить тесты ещё раз, `hello.go` не будет скомпилирован, поскольку вы не передаете никакого параметра. Передайте слово "world" в функцию `Hello`, чтобы ваш код скомпилировался:

```go
func main() {
	fmt.Println(Hello("world"))
}
```

Теперь при запуске тестов вы должны увидеть следующее сообщение:

```text
hello_test.go:10: got 'Hello, world' want 'Hello, Chris''
```

Нам удалось скомпилировать приложение, но оно не проходит по нашим критериям, которые мы указали в тесте.

Давайте сделаем тест успешным, используя имя аргумента и добавим его со строкой `Hello,`:

```go
func Hello(name string) string {
	return "Hello, " + name
}
```

Теперь при запуске тестов они должны отмечаться как пройденные. Обычная часть TDD-цикла: рефакторинг, который мы проделали.

### Немного о системе контроля версий

На этом моменте, если вы используете систему контроля версий (её следовать использовать), я бы порекомендовал коммитить код как он есть. У нас есть работающая программа, которая покрыта тестом.

В то же время, я бы не пушил изменения в мастер-ветку, поскольку я планирую осуществить рефакторинг в скором времени. Хорошо коммитить на данном этапе в случае, если вы начинаете погружаться в рефакторинг, так как вы всегда можете вернуться к работающей версии.

Здесь не будет много рефакторинг, но нам нужно сначала познакомиться с другой конструкцией языка: _константы_.

### Constants

Constants are defined like so

```go
const englishHelloPrefix = "Hello, "
```

We can now refactor our code

```go
const englishHelloPrefix = "Hello, "

func Hello(name string) string {
	return englishHelloPrefix + name
}
```

After refactoring, re-run your tests to make sure you haven't broken anything.

Constants should improve performance of your application as it saves you creating the `"Hello, "` string instance every time `Hello` is called.

To be clear, the performance boost is incredibly negligible for this example! But it's worth thinking about creating constants to capture the meaning of values and sometimes to aid performance.

## Hello, world... again

The next requirement is when our function is called with an empty string it defaults to printing "Hello, World", rather than "Hello, ".

Start by writing a new failing test

```go
func TestHello(t *testing.T) {
	t.Run("saying hello to people", func(t *testing.T) {
		got := Hello("Chris")
		want := "Hello, Chris"

		if got != want {
			t.Errorf("got %q want %q", got, want)
		}
	})
	t.Run("say 'Hello, World' when an empty string is supplied", func(t *testing.T) {
		got := Hello("")
		want := "Hello, World"

		if got != want {
			t.Errorf("got %q want %q", got, want)
		}
	})
}
```

Here we are introducing another tool in our testing arsenal, subtests. Sometimes it is useful to group tests around a "thing" and then have subtests describing different scenarios.

A benefit of this approach is you can set up shared code that can be used in the other tests.

There is repeated code when we check if the message is what we expect.

Refactoring is not _just_ for the production code!

It is important that your tests _are clear specifications_ of what the code needs to do.

We can and should refactor our tests.

```go
func TestHello(t *testing.T) {
	assertCorrectMessage := func(t testing.TB, got, want string) {
		t.Helper()
		if got != want {
			t.Errorf("got %q want %q", got, want)
		}
	}

	t.Run("saying hello to people", func(t *testing.T) {
		got := Hello("Chris")
		want := "Hello, Chris"
		assertCorrectMessage(t, got, want)
	})
	t.Run("empty string defaults to 'World'", func(t *testing.T) {
		got := Hello("")
		want := "Hello, World"
		assertCorrectMessage(t, got, want)
	})
}
```

What have we done here?

We've refactored our assertion into a function. This reduces duplication and improves readability of our tests. In Go you can declare functions inside other functions and assign them to variables. You can then call them, just like normal functions. We need to pass in `t *testing.T` so that we can tell the test code to fail when we need to.

For helper functions, it's a good idea to accept a `testing.TB` which is an interface that `*testing.T` and `*testing.B` both satisfy, so you can call helper functions from a test, or a benchmark.

`t.Helper()` is needed to tell the test suite that this method is a helper. By doing this when it fails the line number reported will be in our _function call_ rather than inside our test helper. This will help other developers track down problems easier. If you still don't understand, comment it out, make a test fail and observe the test output. Comments in Go are a great way to add additional information to your code, or in this case, a quick way to tell the compiler to ignore a line. You can comment out the `t.Helper()` code by adding two forward slashes `//` at the beginning of the line. You should see that line turn grey or change to another color than the rest of your code to indicate it's now commented out.

Now that we have a well-written failing test, let's fix the code, using an `if`.

```go
const englishHelloPrefix = "Hello, "

func Hello(name string) string {
	if name == "" {
		name = "World"
	}
	return englishHelloPrefix + name
}
```

If we run our tests we should see it satisfies the new requirement and we haven't accidentally broken the other functionality.

### Back to source control

Now we are happy with the code I would amend the previous commit so we only
check in the lovely version of our code with its test.

### Discipline

Let's go over the cycle again

* Write a test
* Make the compiler pass
* Run the test, see that it fails and check the error message is meaningful
* Write enough code to make the test pass
* Refactor

On the face of it this may seem tedious but sticking to the feedback loop is important.

Not only does it ensure that you have _relevant tests_, it helps ensure _you design good software_ by refactoring with the safety of tests.

Seeing the test fail is an important check because it also lets you see what the error message looks like. As a developer it can be very hard to work with a codebase when failing tests do not give a clear idea as to what the problem is.

By ensuring your tests are _fast_ and setting up your tools so that running tests is simple you can get in to a state of flow when writing your code.

By not writing tests you are committing to manually checking your code by running your software which breaks your state of flow and you won't be saving yourself any time, especially in the long run.

## Keep going! More requirements

Goodness me, we have more requirements. We now need to support a second parameter, specifying the language of the greeting. If a language is passed in that we do not recognise, just default to English.

We should be confident that we can use TDD to flesh out this functionality easily!

Write a test for a user passing in Spanish. Add it to the existing suite.

```go
	t.Run("in Spanish", func(t *testing.T) {
		got := Hello("Elodie", "Spanish")
		want := "Hola, Elodie"
		assertCorrectMessage(t, got, want)
	})
```

Remember not to cheat! _Test first_. When you try and run the test, the compiler _should_ complain because you are calling `Hello` with two arguments rather than one.

```text
./hello_test.go:27:19: too many arguments in call to Hello
    have (string, string)
    want (string)
```

Fix the compilation problems by adding another string argument to `Hello`

```go
func Hello(name string, language string) string {
	if name == "" {
		name = "World"
	}
	return englishHelloPrefix + name
}
```

When you try and run the test again it will complain about not passing through enough arguments to `Hello` in your other tests and in `hello.go`

```text
./hello.go:15:19: not enough arguments in call to Hello
    have (string)
    want (string, string)
```

Fix them by passing through empty strings. Now all your tests should compile _and_ pass, apart from our new scenario

```text
hello_test.go:29: got 'Hello, Elodie' want 'Hola, Elodie'
```

We can use `if` here to check the language is equal to "Spanish" and if so change the message

```go
func Hello(name string, language string) string {
	if name == "" {
		name = "World"
	}

	if language == "Spanish" {
		return "Hola, " + name
	}
	return englishHelloPrefix + name
}
```

The tests should now pass.

Now it is time to _refactor_. You should see some problems in the code, "magic" strings, some of which are repeated. Try and refactor it yourself, with every change make sure you re-run the tests to make sure your refactoring isn't breaking anything.

```go
const spanish = "Spanish"
const englishHelloPrefix = "Hello, "
const spanishHelloPrefix = "Hola, "

func Hello(name string, language string) string {
	if name == "" {
		name = "World"
	}

	if language == spanish {
		return spanishHelloPrefix + name
	}
	return englishHelloPrefix + name
}
```

### French

* Write a test asserting that if you pass in `"French"` you get `"Bonjour, "`
* See it fail, check the error message is easy to read
* Do the smallest reasonable change in the code

You may have written something that looks roughly like this

```go
func Hello(name string, language string) string {
	if name == "" {
		name = "World"
	}

	if language == spanish {
		return spanishHelloPrefix + name
	}
	if language == french {
		return frenchHelloPrefix + name
	}
	return englishHelloPrefix + name
}
```

## `switch`

When you have lots of `if` statements checking a particular value it is common to use a `switch` statement instead. We can use `switch` to refactor the code to make it easier to read and more extensible if we wish to add more language support later

```go
func Hello(name string, language string) string {
	if name == "" {
		name = "World"
	}

	prefix := englishHelloPrefix

	switch language {
	case french:
		prefix = frenchHelloPrefix
	case spanish:
		prefix = spanishHelloPrefix
	}

	return prefix + name
}
```

Write a test to now include a greeting in the language of your choice and you should see how simple it is to extend our _amazing_ function.

### one...last...refactor?

You could argue that maybe our function is getting a little big. The simplest refactor for this would be to extract out some functionality into another function.

```go
func Hello(name string, language string) string {
	if name == "" {
		name = "World"
	}

	return greetingPrefix(language) + name
}

func greetingPrefix(language string) (prefix string) {
	switch language {
	case french:
		prefix = frenchHelloPrefix
	case spanish:
		prefix = spanishHelloPrefix
	default:
		prefix = englishHelloPrefix
	}
	return
}
```

A few new concepts:

* In our function signature we have made a _named return value_ `(prefix string)`.
* This will create a variable called `prefix` in your function.
  * It will be assigned the "zero" value. This depends on the type, for example `int`s are 0 and for `string`s it is `""`.
    * You can return whatever it's set to by just calling `return` rather than `return prefix`.
  * This will display in the Go Doc for your function so it can make the intent of your code clearer.
* `default` in the switch case will be branched to if none of the other `case` statements match.
* The function name starts with a lowercase letter. In Go public functions start with a capital letter and private ones start with a lowercase. We don't want the internals of our algorithm to be exposed to the world, so we made this function private.

## Wrapping up

Who knew you could get so much out of `Hello, world`?

By now you should have some understanding of:

### Some of Go's syntax around

* Writing tests
* Declaring functions, with arguments and return types
* `if`, `const` and `switch`
* Declaring variables and constants

### The TDD process and _why_ the steps are important

* _Write a failing test and see it fail_ so we know we have written a _relevant_ test for our requirements and seen that it produces an _easy to understand description of the failure_
* Writing the smallest amount of code to make it pass so we know we have working software
* _Then_ refactor, backed with the safety of our tests to ensure we have well-crafted code that is easy to work with

In our case we've gone from `Hello()` to `Hello("name")`, to `Hello("name", "French")` in small, easy to understand steps.

This is of course trivial compared to "real world" software but the principles still stand. TDD is a skill that needs practice to develop, but by breaking problems down into smaller components that you can test, you will have a much easier time writing software.
