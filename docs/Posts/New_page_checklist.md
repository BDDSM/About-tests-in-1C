---
title: Чек-лист
---
# Чек-лист добавления новой статьи

## Процесс

- [ ] Статья пишется в отдельной ветке. Пушить в мастер запрещено.
- [ ] Статья пишется полноценно локально с промежуточными коммитами.
- [ ] После завершения требуется создать "Запрос на слияние".
- [ ] В статье не должно быть битых ссылок. Статья с битыми ссылками будет автоматически отклонена при "Запросе на слияние".

## Файлы

- [ ] Все статьи размещаются в подкаталоге [docs](/docs).
- [ ] Статья размещается в предсказуемом и логичном месте.
- [ ] Имя файла: `<ИмяСтатьиЛатиницей>.md`.
- [ ] Все дополнительные файлы - изображения, файлы для скачивания итп, размещаются в каталоге `<ИмяСтатьиЛатиницей>.assets`.
- [ ] Пустых каталогов быть не должно. Файлы `.gitkeep` запрещены.

## Контент

- [ ] Статья начинается с заголовка `# Заголовок статьи`. По этому заголовку формируется имя статьи на панели навигации.
- [ ] Все внутренние ссылки в статье должны быть указаны на конкретные файлы `*.md`.
- [ ] Все внутренние ссылки должны быть относительными - без указания полного пути и в начале не должно быть слеша `/`.
- [ ] Все пути в ссылках указаны с прямыми слешами `/`. Чтобы не путаться - слеши должны быть такими же, как и в адресной строке браузера.

## Указание ссылок на статью

- [ ] Cтатья должна быть указана на главной странице в файле [`index.md`](../index.md)

## Дополнительные возможности в оформлении

- Для автоформирования содержания статьи следует использовать заголовки: `## Заголовок первого уровня`, `### Заголовок второго уровня`, `#### Заголовок третьего уровня`
- Поддерживаются смайлики, выделения, таблицы и прочее от классической markdown разметки

### Оформление блоков кода

Код можно разукрашивать, если указать идентификатор языка, выводить в закладках и подсвечивать строки.

Примеры оформления блоков https://squidfunk.github.io/mkdocs-material/extensions/admonition/

??? note "Пример блока"
    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla et euismod
    nulla. Curabitur feugiat, tortor non consequat finibus, justo purus auctor
    massa, nec semper lorem quam in massa.

- Примеры оформления блоков кода https://squidfunk.github.io/mkdocs-material/extensions/codehilite/

``` bsl tab="ДобавитьОтбор"  hl_lines="11"
// Добавляет отбор в группу отбора условного оформления
//
// Параметры:
//  пУО    - ЭлементУсловногоОформленияКомпоновкиДанных  - Элемент условного оформления
//  ПутьКДаннымПоля        - Строка - путь к данным поля
//  пЗначение            - Любое - значение отбора
//  ВидСравнения        - ВидСравненияКомпоновкиДанных - вид сравнения.
//
// Возвращаемое значение:
//  ОбщийМодуль - этот модуль
Функция ДобавитьОтбор( пУО, Знач ПутьКДаннымПоля, Знач пЗначение, Знач ВидСравнения = Неопределено ) Экспорт
    
    Если ВидСравнения = Неопределено Тогда
        
        ВидСравнения = ВидСравненияКомпоновкиДанных.Равно;
        
    КонецЕсли;
    
    Отбор                = пУО.Отбор.Элементы.Добавить( Тип( "ЭлементОтбораКомпоновкиДанных" ) );
    Отбор.ВидСравнения   = ВидСравнения;
    Отбор.Использование  = Истина;
    Отбор.ЛевоеЗначение  = Новый ПолеКомпоновкиДанных( ПутьКДаннымПоля );
    Отбор.ПравоеЗначение = пЗначение;
    
    Возврат к2УО;
    
КонецФункции
```

``` bsl tab="Отбор_Заполнено"
// Добавляет отбор на заполнение поля в группу отбора условного оформления
//
// Параметры:
//  пУО    - ЭлементУсловногоОформленияКомпоновкиДанных  - Элемент условного оформления
//  ПутьКДаннымПоля - Строка - путь к данным поля.
//
// Возвращаемое значение:
//  ОбщийМодуль - этот модуль
Функция Отбор_Заполнено( пУО, Знач ПутьКДаннымПоля ) Экспорт
    
    ДобавитьОтбор( пУО, ПутьКДаннымПоля, , ВидСравненияКомпоновкиДанных.Заполнено );
    
    Возврат к2УО;
    
КонецФункции

}
```

``` bsl tab="Равенство полей"
// Добавляет отбор в группу отбора условного оформления
//
// Параметры:
//  пУО    - ЭлементУсловногоОформленияКомпоновкиДанных  - Элемент условного оформления
//  ПутьКДаннымЛевогоПоля - Строка - путь к данным поля
//  ПутьКДаннымПравогоПоля - Строка - путь к данным поля.
//
// Возвращаемое значение:
//  ОбщийМодуль - этот модуль
Функция Отбор_РавенствоПолей( пУО, Знач ПутьКДаннымЛевогоПоля, Знач ПутьКДаннымПравогоПоля ) Экспорт
    
    ДобавитьОтбор( пУО, ПутьКДаннымЛевогоПоля, Новый ПолеКомпоновкиДанных( ПутьКДаннымПравогоПоля ), ВидСравненияКомпоновкиДанных.Равно );
    
    Возврат к2УО;
    
КонецФункции
```

### Файл `.page`

С помощью этих файлов можно задавать имя каталогу, сортировать файлы, включать/выключать скрытие для одного файла или скрывать каталог в целом.
Подробнее: https://squidfunk.github.io/mkdocs-material/plugins/awesome-pages/#usage

Например, файл этого раздела означает, что раздел называется Знания, а сортировка - файл index.md, потом каталог Posts, потом Certification, а дальше в алфавитном порядке:

```
title: Знания
arrange:
    - index.md
    - Posts
    - Certification
    - ...
```

## Локальный веб-сервер

Должен быть установлен python.

??? example "Установка python"
    [Скачиваем](https://www.python.org/) питон. Запускаем выборочную установку.
    
    ![image-20200610195424201](New_page_checklist.assets/image-20200610195424201.png)
    
    Снимаем все галочки, кроме pip.
    
    ![image-20200610195733694](New_page_checklist.assets/image-20200610195733694.png)
    
    Снимаем все, кроме добавления в переменные окружения.
    
    ![image-20200610195837006](New_page_checklist.assets/image-20200610195837006.png)

    Можно тыкнуть в отключение лимитов в длине пути, но это не обязательно (но это не точно).

### Установка/обновление библиотек

Запустить в корне репозитория `pip_Install_update.bat` или в командной строке выполнить следующий код:

```cmd
pip install --upgrade mkdocs mkdocs-material pygments-bsl pymdown-extensions mkdocs-minify-plugin mkdocs-awesome-pages-plugin mkdocs-git-revision-date-localized-plugin
```

??? done "pip_Install_update.bat"
    ![pip_Install_update](New_page_checklist.assets/pip_Install_update.gif)

В конце должна появится надпись, что нас достиг саксесс.

### Запуск сервиса локально

В корне репозитория запускаем `mkdocs_serve.bat` или в командной строке, находясь в корне репозитория:

```cmd
mkdocs serve
```

??? done "mkdocs_serve.bat"
    ![mkdocs_serve](New_page_checklist.assets/mkdocs_serve.gif)

На первое предупреждение не пугаемся. Через некоторое время будет выведено сообщение, что сервер поднят по адресу [http://127.0.0.1:8000/](http://127.0.0.1:8000/) и включено отслеживание изменений.

Отслеживание изменений означает, что после каждого сохранения файла в репозитории - статьи, вспомогательных файлов или настроечных - сайт будет сам пересобираться и выводить уже обновленную статью.

Через поднятый локальный сервер удобно смотреть на верстку сайта и контролировать ошибки в настройках, потерянные ссылки итп.

Когда сервер больше не нужен - достаточно закрыть окно комадной панели.

??? attention "Не страшное предупреждение has no git logs, using current timestamp"
    Когда создана новая статья, но еще не закоммичена, то сервер ругается вот так:
        ![image-20200610201757936](New_page_checklist.assets/image-20200610201757936.png)
        На него можно не обращать внимание или просто закоммитить изменения и предупреждение уйдет.

??? fail "Предупреждение о битой ссылке"
    Такое предупреждение означает, что в файле `knowledge\Posts\New_page_checklist.md` есть ссылка на файл `knowledge\Posts\test.md`, но самого этого файла не существует. Это битая ссылка и гитлаб не даст влить такую статью. Убедитесь, что регистр букв совпадает и слеши правильные.
    ![image-20200610202108342](New_page_checklist.assets/image-20200610202108342.png)

??? fail "Ошибка в файле .pages"
    Если в файле `.pages` ошибка, то выскочет такая страшная штука, где указано, что в файле `E:\GIT_Repo\Konstanta\wiki\docs\knowledge\Posts\.pages` неправильно указан порядок, т.к. файл `New_post1.md` не найден.
    ![image-20200610202418995](New_page_checklist.assets/image-20200610202418995.png)