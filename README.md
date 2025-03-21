# RB_Script_AutoFormatter

## Описание

RB_Script_AutoFormatter - это инструмент для автоматизации работы с .rb скриптами, позволяющий быстро сохранять их в распакованном формате для редактирования и последующей упаковки обратно в формат игры. Особенно полезен для локализации и редактирования игровых данных в проектах на RPG Maker.

## Функциональность

Инструмент предоставляет следующие возможности:

- **Распаковка скриптов** - извлечение данных из .rb файлов в удобный для редактирования формат
- **Форматирование текста** - автоматическое форматирование с учетом длины строки и структуры данных
- **Упаковка обратно в игру** - сохранение отредактированных данных в формате, совместимом с игрой
- **Поддержка нескольких типов данных**:
  - Library(Enemy) - описания врагов
  - JobChange - описания классов/профессий
  - Library(Medal) - описания медалей/достижений
  - Skill Replacer - замена ссылок на навыки

## Использование

### Базовое использование

1. Выберите нужный режим работы (Library(Enemy), JobChange, Library(Medal) или Skill Replacer)
2. Выберите язык (RUS или JAP)
3. Вставьте исходный текст в поле ввода
4. Нажмите "Копировать результат" для получения отформатированного текста
5. Для сохранения в файл:
   - Переключитесь в "Режим прямой компиляции"
   - Загрузите исходный файл
   - Нажмите "Компилировать данные"

### Структура исходного текста

#### Примеры для режима Library(Enemy)

```
1 # Слизь
Обычная слизь, которую можно встретить в любом подземелье. Слабый противник, который не представляет угрозы для опытных авантюристов. Иллюстрация: Художник
```

#### Примеры для режима JobChange

```
1 => # Воин
Базовый класс, специализирующийся на ближнем бою. Экипировка: Мечи, Топоры, Копья Навыки: Рассечение, Выпад Способности: Стойкость
```

#### Примеры для режима Skill Replacer

```
<Skill: 123>
<Skill: 456>
```

### Важные особенности форматирования

#### Идентификатор и заголовок

- Каждый блок должен начинаться с числового идентификатора
- За идентификатором следует символ # и название на японском (для режима Library(Enemy))
- Для JobChange используется формат `ID => # Название`

#### Широкие пробелы

- В исходных данных используются японские широкие пробелы `　` для разделения элементов в списках
- Эти пробелы необходимо сохранять, так как они используются игрой для корректного разделения элементов
- Скрипт автоматически обрабатывает и сохраняет эти пробелы в выходных данных

#### Секции описания

Для корректного форматирования важно правильно обозначать начало каждой секции:

- **Экипировка:** или **Экипировка：** (с японским двоеточием)
- **Навыки:** или **Навыки：**
- **Способности:** или **Способности：**

На японском:
- **装備武器：**
- **スキル：**
- **アビリティ：**

#### Обработка иллюстраций

- Скрипт находит информацию об иллюстраторе как в русском ("Иллюстрация:"), так и в японском ("イラスト：") тексте
- Если в тексте на активном языке нет информации об иллюстраторе, используется информация из другого языка
- В результате форматирования всегда используется японское двоеточие: "Иллюстрация："

### Настройка длины строки

- Используйте поле "ДЛИНА СТРОКИ" для указания максимальной длины строки в символах
- По умолчанию используется значение 40 символов
- Для японского текста рекомендуется использовать значение 30-35 символов
- Для русского текста оптимально 40-45 символов

## Порядок размещения блоков и интеллектуальная сортировка

Скрипт сохраняет порядок блоков в соответствии с их идентификаторами. При компиляции данных в файл:

1. Скрипт анализирует структуру исходного файла
2. Находит соответствующие блоки данных по их идентификаторам
3. Заменяет содержимое блоков на новые отформатированные данные
4. Сохраняет исходную структуру файла и порядок блоков

## Особенности форматирования

### Выходной формат данных

- Для Library(Enemy) данные форматируются в виде массива строк
- Для JobChange используется вложенная структура массивов
- Для Library(Medal) используется формат, аналогичный Library(Enemy)

### Автоматический перенос

Скрипт автоматически переносит текст, соблюдая указанную максимальную длину строки:
- Переносы делаются по пробелам
- Сохраняется структура секций (экипировка, навыки, способности)
- Информация об иллюстраторе всегда размещается в конце описания

### Замена ссылок на навыки

В режиме Skill Replacer:
- Скрипт заменяет теги вида `` на соответствующие названия навыков
- Необходимо предварительно загрузить файл Skills для корректной замены

## Установка

1. Скачайте файлы проекта из репозитория
2. Откройте файл Script_for_packing.html в любом современном браузере
3. Для распаковки используйте Script_for_unpacking.html

## Требования

- Современный веб-браузер с поддержкой JavaScript
- Для работы с файлами требуется доступ к файловой системе

## Контрибуция

Вклады в проект приветствуются! Если у вас есть идеи по улучшению или вы нашли ошибку:
1. Создайте issue с описанием проблемы или предложения
2. Отправьте pull request с вашими изменениями

## Лицензия

Этот проект распространяется под лицензией MIT. Инструмент разработан специально для работы с проектом "RPG終章" и может потребовать модификации для использования с другими проектами RPG Maker.
