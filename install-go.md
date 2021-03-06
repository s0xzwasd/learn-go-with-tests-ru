# Установка Go, настройка рабочего окружения для комфортной работы

Найти официальный гайд по установке Go можно [здесь](https://golang.org/doc/install).

Этот гайд подразумевает, что у вас есть менеджер пакетов, например [Homebrew](https://brew.sh) для macOS, [Chocolatey](https://chocolatey.org) для Windows, [Apt](https://help.ubuntu.com/community/AptGet/Howto) для Ubuntu или [yum](https://access.redhat.com/solutions/9934) для Linux дистрибутивов.

Для демонстрации приведен пример установки для macOS с помощью Homebrew.

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

*Вы должны следовать инструкциям по установке для вашего пакетного менеджера. Обратите внимание, что для каждого менеджера могут быть свои требования.

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

`go.mod` файл будет выглядеть примерно как показано ниже:

```
module cmd

go 1.17

```
Вы можете вызвать Go документацию с помощью следующих команд.

```sh
go help mod
go help mod init
```

## Редактор кода

Выбор редактора кода всегда индвидуален, возможно у вас уже есть предпочтение в этом вопросе. Главное, чтобы ваш редактор поддерживал Go. Как один из вариантов вы можете рассмотреть [Visual Studio Code](https://code.visualstudio.com) и установить его с помощью следующей команды:

```sh
brew install --cask visual-studio-code
```

После установки вы можете проверить, что VS Code установлен правильно, выполнив следующую команду в вашем терминале:

```sh
code .
```

VS Code поставляется с небольшим количеством функционала, но вы можете его расширить, установив плагины. Для поддержки Go нужно установить [плагин](https://marketplace.visualstudio.com/items?itemName=golang.go) командой:

```sh
code --install-extension golang.go
```

Когда вы откроете Go файл первый раз в VS Code, вам будет предложено установить инструменты для анализа кода. Вы можете посмотреть список этих инструментов [здесь](https://github.com/golang/vscode-go/blob/master/docs/tools.md).

## Дебагер для Go

Стандартом для отладки Go кода является (также включен в VS Code) [Delve](https://github.com/go-delve/delve). Его можно установить командой:

```sh
go get -u github.com/go-delve/delve/cmd/dlv
```

Для дополнительной информации по настройке и запуску отладки в VS Code, можете посмотреть [документацию из официального репозитория плагина](https://github.com/golang/vscode-go/blob/master/docs/debugging.md).

## Линтеры для Go

Помимо стандартного линтера в Go вы можете также использовать [golangci-lint](https://golangci-lint.run), который можно установить командой:

```sh
brew install golangci-lint
```

## Рефакторинг кода

Красной нитью во всей книге является важность рефакторинга. Ваши инструменты могут позволить вам делать больше рефакторинга и быть уверенным в конечном результате.

Стоит ознакомиться с вашим редактором кода и изучить базовые комбинации горячих клавиш:

- **Extract/Inline variable**. Позволяет взять "магические числа" из вашего кода и дать им имена, что упростит код и его читаемость в несколько шагов.
- **Extract method/function**. Важно иметь возможность взять часть кода и вынести его в отдельную функцию или метод.
- **Rename**. Вы должны быть уверены, что можете изменить имя символов (переменной, функции и т.д) быстро в нескольких файлах. Ручной рефакторинг утомляет и занимает много времени.
- **go fmt**. В Go есть стандартный форматтер вашего кода, который называется `go fmt`. Ваш редактор должен запускать его при каждом сохранении файла.
- **Run tests**. Вы должны иметь возможность запускать ваши тесты и быстро их перезапускать, чтобы убеждаться, что рефакторинг не повредил логику в коде.

Есть также дополнительные инструменты, которые помогут работать с кодом:

- **View function signature** - Вам никогда не нужно задумываться о том, как правильно вызвать функцию. Ваша IDE должна описывать и показывать документацию по функции, какие у неё параметры и какое значение она возвращает.
- **View function definition** - Если неясно, что делает функция, то у вас должна быть возможность быстро посмотреть исходный код функции и разобраться что происходит.
- **Find usages of a symbol** - Вы можете посмотреть как используется функция в контексте других частей приложения, что может помочь выбрать правильный процесс при рефакторинге.

Идеальное владение инструментами поможет концентрироваться на написании кода и снизить когнитивную нагрузку при переключении с одной задачи на другую.

## Итоги

Вы установили Go, выбрали редактор кода и настроили базовые инструменты для дальнейшей работы. У Go очень большая экосистема и большой выбор инструментов под каждую задачу. Мы рассмотрели только несколько из них, однако вы можете пойти дальше и посмотреть доступные инструменты на https://awesome-go.com.
