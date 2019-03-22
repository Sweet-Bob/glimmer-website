<!---
# Installing

Glimmer uses [Ember CLI](https://ember-cli.com/), the battle-tested command-line interface tool (CLI) from the Ember project, to help you create and manage your applications.
It provides the following features, among others:

* Creating a new application with a conventional project layout
* A build pipeline with testing, development, and production environments
* [TypeScript](http://www.typescriptlang.org/) support out-of-the-box
* Generators for components and helpers
-->

# Установка

Glimmer использует [Ember CLI](https://ember-cli.com/), для создания и управления вашим приложением.
С помощью Ember CLI можно:

* Создавать новые приложения с жесткой структурой проекта (convention over configuration)
* Сборку проекта в dev, и prod окружении (с тестированием)
* [TypeScript](http://www.typescriptlang.org/) поддерживается из коробки
* Генераторы для components и helpers

<!---
## Pre-requisites

### Git

Ember CLI requires Git to manage many of its dependencies. Git comes with Mac OS X and most Linux distributions. Windows users can download and run <a href="http://git-scm.com/download/win">this Git installer</a>.

### Node.js and npm

Ember CLI is built with JavaScript, and expects the [Node.js](https://nodejs.org/)
runtime. It also requires dependencies fetched via [npm](https://www.npmjs.com/). npm is packaged with Node.js, so if your computer has Node.js
installed you are ready to go.

Ember requires Node.js 6 or higher and npm 2.14.2 or higher.
If you're not sure whether you have Node.js or the right version, run this on your
command line:

```bash
node --version
npm --version
```

If you get a *"command not found"* error or an outdated version for Node:

* Windows or Mac users can download and run [this Node.js installer](http://nodejs.org/download/).
* Mac users often prefer to install Node using [Homebrew](http://brew.sh/). After
installing Homebrew, run `brew install node` to install Node.js.
* Linux users can use [this guide for Node.js installation on Linux](https://nodejs.org/en/download/package-manager/).

If you get an outdated version of npm, run `npm install -g npm`.

### Yarn

We are going to use [Yarn](https://yarnpkg.com/en/) to manage dependencies in a Glimmer project, as it offers some advantages over npm, such as deterministic builds and the ability to work offline.

You can follow their <a href="https://yarnpkg.com/en/docs/install">installation instructions</a> to get set up.

## Installing

To generate new projects, we will need Ember CLI.

To install Ember CLI, run the following command:

```bash
yarn global add ember-cli
```

Alternatively, you can do:

```bash
npm install -g ember-cli
```

To verify that it's correctly installed, run the following command:

```bash
ember -v
```
-->

## Перед установкой

### Git

Для использования Ember CLI, должен быть установлен Git.    
В операционных системах Mac OS X и Linux, Git установлен по умолчанию.    
Для OS Windows вы можете скачать <a href="http://git-scm.com/download/win">инсталлер Git</a>. 

### Node.js и npm

Ember CLI использует JavaScript, и требует установленного [Node.js](https://nodejs.org/) + [npm](https://www.npmjs.com/). 

Для использования Ember у вас должен быть установлен Node.js 6 или выше, а также npm 2.14.2 или выше.   
Чтобы узнать ваши версии nodejs и npm, выполните в терминале:

```bash
node --version
npm --version
```

Если после ввода команд, терминал сообщил об ошибке *"command not found"*, или *"outdated version for nodejs"*   

* Windows или Mac пользователи могут скачать и установить Node.js [по этой ссылке](http://nodejs.org/download/).
* Пользовали Mac также могут установить Node используя [Homebrew](http://brew.sh/). После установки 
Homebrew, выполните команду `brew install node` для того, чтобы установить Node.js.
* Пользователи Linux могут использовать [инструкцию по установке Node.js](https://nodejs.org/en/download/package-manager/).

Если у вас устаревшая версия npm, выполните команду `npm install -g npm`.

### Yarn

Мы будем использовать [Yarn](https://yarnpkg.com/en/) для управления зависимостями в Glimmer проекте, т.к yarn реализует функционал лучше чем npm, такой как детерминированные сборки (lockfile) and способность работать offline.

Вы можете установить yarn с помощью <a href="https://yarnpkg.com/en/docs/install">этой инструкции</a>


## Установка

Для создания нового проекта, нам понадобится Ember CLI

```bash
yarn global add ember-cli
```

Или:

```bash
npm install -g ember-cli
```

Подтверждением успешной установки будет результат команды:

```bash
ember -v
```
