# Установка Go, настройка рабочего окружения для комфортной работы

Найти официальный гайд по установке GO можно [здесь](https://golang.org/doc/install).

Этот гайд подразумевает, что у вас есть менеджер пакетов, например [Homebrew](https://brew.sh) для macOS, [Chocolatey](https://chocolatey.org) для Windows, [Apt](https://help.ubuntu.com/community/AptGet/Howto) для Ubuntu или [yum](https://access.redhat.com/solutions/9934) для Linux дистрибутивов.

Для демонстрации приведен пример установки для macOS с помощью Homebrew.

For demonstration purposes we will show the installation procedure for OSX using Homebrew.

## Установка

Процесс установки предельно прост. Сначала нужно установить Homebrew, но который имеет зависимость с XCode, поэтому сначала убедитесь или установите XCode Command Line Tools.

```sh
xcode-select --install
```

Затем запустите следующую команду для установки Homebrew:

```sh
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
```

С этого момента у вас есть возможность установить Go командой:

```sh
brew install go
```

*Вы должны следовать инструкция по установки вашего пакетного менеджера. Обратите внимание, что здесь могут быть OS-специфичные требования.

Вы можете убедиться, что Go установлен, командой:

```sh
$ go version
go version go1.17 darwin/amd64
```

## Настройка окружения для Go

### Go Modules

Go версии 1.11 представил новый подход, который называется [модули](https://github.com/golang/go/wiki/Modules) или Go modules. Он стал стандартом начиная с Go 1.16, поэтому _использование `GOPATH` не рекомендуется_. Вы можете встретить использование `GOPATH` в старых обучающих материалах и статьях.

Модули призваны решить проблемы, связанные с управлением зависимостями, выбора нужной версии и надежной и предсказуемой сборки проекта. Подход также позволяет программисту запускать Go-код за пределами `GOPATH`.

Использование модулей довольно простое. Выберите любую директорию за пределами `GOPATH` как основную директорию вашего проекта, и создайте новый модуль внутри с помощью команды `go mod init`.

После выполнения команды создастся файл `go.mod`, который содержит путь к модулю и версию Go, что требуется для корректной работы модуля при его экспорте и использовании в других проектах.

Если путь до модуля не указан, то `go mod init` попытается предсказать путь до модуля основываясь на структуре проекта. Это также можно изменить, передав аргумент в эту команду.

```sh
mkdir my-project
cd my-project
go mod init <modulepath>
```

A `go.mod` file could look like this:

```
module cmd

go 1.16

```

The built-in documentation provides an overview of all available `go mod` commands.

```sh
go help mod
go help mod init
```

## Go Editor

Editor preference is very individualistic, you may already have a preference that supports Go. If you don't you should consider an Editor such as [Visual Studio Code](https://code.visualstudio.com), which has exceptional Go support.

You can install it using the following command:

```sh
brew install --cask visual-studio-code
```

You can confirm VS Code installed correctly you can run the following in your shell.

```sh
code .
```

VS Code is shipped with very little software enabled, you can enable new software by installing extensions. To add Go support you must install an extension, there are a variety available for VS Code, an exceptional one is [Luke Hoban's package](https://github.com/golang/vscode-go). This can be installed as follows:

```sh
code --install-extension golang.go
```

When you open a Go file for the first time in VS Code, it will indicate that the Analysis tools are missing, you should click the button to install these. The list of tools that gets installed (and used) by VS Code are available [here](https://github.com/golang/vscode-go/blob/master/docs/tools.md).

## Go Debugger

A good option for debugging Go (that's integrated with VS Code) is Delve. This can be installed as follows:

```sh
go get -u github.com/go-delve/delve/cmd/dlv
```

For additional help configuring and running the Go debugger in VS Code, please reference the [VS Code debugging documentation](https://github.com/golang/vscode-go/blob/master/docs/debugging.md).

## Go Linting

An improvement over the default linter can be configured using [GolangCI-Lint](https://golangci-lint.run).

This can be installed as follows:

```sh
brew install golangci/tap/golangci-lint
```

## Refactoring and your tooling

A big emphasis of this book is around the importance of refactoring.

Your tools can help you do bigger refactoring with confidence.

You should be familiar enough with your editor to perform the following with a simple key combination:

- **Extract/Inline variable**. Being able to take magic values and give them a name lets you simplify your code quickly
- **Extract method/function**. It is vital to be able to take a section of code and extract functions/methods
- **Rename**. You should be able to confidently rename symbols across files.
- **go fmt**. Go has an opinioned formatter called `go fmt`. Your editor should be running this on every file save.
- **Run tests**. It goes without saying that you should be able to do any of the above and then quickly re-run your tests to ensure your refactoring hasn't broken anything

In addition, to help you work with your code you should be able to:

- **View function signature** - You should never be unsure how to call a function in Go. Your IDE should describe a function in terms of its documentation, its parameters and what it returns.
- **View function definition** - If it's still not clear what a function does, you should be able to jump to the source code and try and figure it out yourself.
- **Find usages of a symbol** - Being able to see the context of a function being called can help your decision process when refactoring.

Mastering your tools will help you concentrate on the code and reduce context switching.

## Wrapping up

At this point you should have Go installed, an editor available and some basic tooling in place. Go has a very large ecosystem of third party products. We have identified a few useful components here, for a more complete list see https://awesome-go.com.
