# Структура приложения

Когда первоначальная настройка завершена, давайте взглянем на наше приложение `my-app`: 

```sh
my-app
├── config
│   ├── environment.js
│   ├── module-map.ts
│   └── resolver-configuration.ts
├── dist/
├── src
│   ├── ui
│   │   ├── components
│   │   │   └── MyApp
│   │   │       ├── component.ts
│   │   │       └── template.hbs
│   │   ├── styles
│   │   │   └── app.css
│   │   └── index.html
│   ├── index.ts
│   └── main.ts
├── ember-cli-build.js
│
... other files ...
```

В кратце, выше перечисленные файлы и директории преназначены для: 

- `my-app/config/environment.js`: конфигурационный Glimmer файл 
- `my-app/config/*.ts`: конфигурационные файлы. *Важно: Глиммер работает только с использованием Typescript. В ближайшее время мы добавим поддержку ES2015 Javascript*
- `my-app/dist`: ваши скомпилированные исходники
- `my-app/src/index.ts`: используется для инициализации приложения, перед тем как наше Glimmer приложение будет загружено (Glimmer приложение будет вставлено в div с ID указанным вами (смотрите `containerElement` свойство))
- `my-app/ember-cli-build.js`: используется для конфигурирования Ember-CLI (импорт vendor файлов, настройка Broccoli, и.т.д) 

Однако, больше всего времени мы проведем в директории `my-app/src/ui` 

## Директория UI

Как вы можете увидеть, Glimmer помещает все наши компоненты в директорию `my-app/src/ui/components` с корневым компонентом `MyApp`, здесь начинается разработка приложения. Вся остальная логика и компоненты должны быть размещены внутри `MyApp/template.hbs` файла.

Итак, давайте добавим новый компонент в Glimmer. Чтобы это сделать, выполним следущую команду для генерации первого компонента из blueprint:

```sh
$ ember g glimmer-component HelloGlimmer
installing component
  create src/ui/components/HelloGlimmer/component.ts
  create src/ui/components/HelloGlimmer/component-test.ts
  create src/ui/components/HelloGlimmer/template.hbs
```

Как вы можете увидеть, мы сгенерировали два файла (`component.ts` и `template.hbs`) в директории `src/ui/components/HelloGlimmer`. Glimmer компоненты используют шаблон для генерации HTML (с использованием [Handlebars](http://handlebarsjs.com) шаблонизатора с расширенным функционалом от Glimmer/Ember) и Typescript/Javascript файл, который предоставляет свойства и обработчики (известные как actions в Ember) для шаблона. Больше деталей как работает Handlebars будет рассказано далее.    

Если вы сгенерируете дополнительные компоненты, они также будут размещены в `src/ui/components` если мы сознательно не вложим их. Для примера, давайте добавим второй компонент с названием `ConferenceSpeakers`:  

```sh
$ ember g glimmer-component ConferenceSpeakers
installing component
  create src/ui/components/ConferenceSpeakers/component.ts
  create src/ui/components/ConferenceSpeakers/component-test.ts
  create src/ui/components/ConferenceSpeakers/template.hbs
```

Давайте посмотрим на наш новый компонент `conference-speakers` в структуре приложения:

```sh
my-app
│
... snipped ...

└── src
    └── ui
        ├── components
        │   ├── ConferenceSpeakers
        │   │   ├── component.ts
        │   │   ├── component-test.ts
        │   │   └── template.hbs
        │   └── HelloGlimmer
        │       ├── component.ts
        │       ├── component-test.ts
        │       └── template.hbs
        ├── styles
        │   └── app.css
        └── index.html

... snipped ...
```

Мы можем использовать новый компонент в `MyApp/template.hbs` файле:

```hbs
<div>
  <ConferenceSpeakers />
</div>
```

Также мы добавим под-компонент в наше приложение, для демонстрации более глубокой вложености:

```sh
$ ember g glimmer-component ConferenceSpeakers/ConferenceSpeaker
installing component
  create src/ui/components/ConferenceSpeakers/ConferenceSpeaker/component.ts
  create src/ui/components/ConferenceSpeakers/ConferenceSpeaker/component-test.ts
  create src/ui/components/ConferenceSpeakers/ConferenceSpeaker/template.hbs
```

Эта команда сгенерирует следующую структуру внутри директории `ConferenceSpeakers`:

```sh
my-app
│
... snipped ...

└── src
    └── ui
        └── components
            └── ConferenceSpeakers
                ├── ConferenceSpeaker
                │   ├── component.ts
                │   ├── component-test.ts
                │   └── template.hbs
                ├── component.ts
                └── template.hbs

... snipped ...
```
Наш новый компонент может быть использован только внутри файла `ConferenceSpeakers/template.hbs`: 

```hbs
<div>
  <ConferenceSpeaker />
</div>
```

Glimmer использует "local resolution" для вложенных компонентов, `ConferenceSpeaker` не будет работать в нашем корневом компоненте (`MyApp/template.hbs`):

```hbs
{{!-- invalid --}}
<ConferenceSpeakers/ConferenceSpeaker />
```

Подробнее о "local resolution" стратегии будет добавлено в ближайшее время.

## Стили

В зависимости от того, где вы используете Glimmer приложение, стили содержащихся приложений уже будут влиять на внешний вид вашего приложения. Однако вы также можете добавить новые стили, которые применяются только к вашим компонентам Glimmer, отредактировав `src/ui/styles/app.css`
