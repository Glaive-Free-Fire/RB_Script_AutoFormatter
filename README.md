# RB_Script_AutoFormatter

## Описание

RB_Script_AutoFormatter - это инструмент для автоматического форматирования текстовых описаний в правильный формат данных для RPG Maker VX Ace. Скрипт создан специально для работы с переводом игры "もんむす・くえスト！RPG終章" (Monmusu Quest! RPG Final Chapter), которая использует специфический формат хранения описаний персонажей, предметов и другого игрового контента.

Инструмент позволяет преобразовать обычный текст с описаниями в структурированные блоки данных, совместимые с форматом сохранения RPG Maker VX Ace, автоматически учитывая максимальную длину строк, сохраняя специальные форматы текста (широкие пробелы) и правильно обрабатывая различные разделы описаний (Экипировка, Навыки, Способности).

## Функциональность

- **Три режима работы**: 
  - Library(Enemy) - для форматирования описаний противников
  - JobChange - для форматирования описаний профессий/классов персонажей
  - Skill Replacer - для замены ссылок на навыки (Skill XXX) на их фактические названия

- **Поддержка двух языков**:
  - RUS - для русского перевода
  - JAP - для японского оригинала

- **Настраиваемые параметры форматирования**:
  - Регулируемая длина строки для каждого режима и языка (кроме Skill Replacer)
  - Корректное сохранение широких пробелов (　) между элементами списков
  - Автоматическое разделение длинных описаний на строки подходящей длины

- **Специальные возможности форматирования**:
  - Обработка блоков "Экипировка", "Навыки", "Способности" с сохранением структуры
  - Поддержка блоков иллюстраций с префиксами на русском и японском языках
  - Правильное экранирование кавычек в выходных данных

- **Замена ссылок на навыки (Skill Replacer)**:
  - Автоматический поиск и замена ссылок на навыки (формат "Skill XXX") на их фактические названия
  - Загрузка файла Skills.txt для получения соответствия номеров навыков и их названий
  - Обновление исходного текста с заменёнными названиями навыков

## Использование

### Базовое использование

1. Откройте HTML-файл скрипта в любом современном браузере
2. Выберите нужный режим работы (Library/JobChange/Skill Replacer)
3. Для режимов Library и JobChange:
   - Выберите язык (RUS/JAP) 
   - Вставьте исходный текст в поле ввода
   - Отформатированный результат появится в правой части экрана
   - При необходимости нажмите кнопку "Копировать результат" для копирования отформатированного текста
4. Для режима Skill Replacer:
   - Загрузите файл Skills.txt, содержащий список навыков и их номера
   - Вставьте исходный текст с ссылками на навыки (формат "Skill XXX") в поле ввода
   - Нажмите кнопку "Обработать Skills" для замены ссылок на фактические названия навыков
   - Обновлённый текст с заменёнными названиями появится в поле ввода

### Структура исходного текста

#### Примеры для режима Library(Enemy)

**Пример на русском языке:**
```
766
Одна из кукол Владык Монстров, созданная Кагэцугуми из тел прежних правительниц. Поскольку эту Владыку прославляли за красоту, подобную небесной деве, Кагэцугуми постаралась максимально точно воспроизвести её прижизненную красоту. Благодаря влиянию матери в ней проявились драконьи черты, что делает её физически крайне выносливой. Её отточенное мастерство владения мечом ничуть не уступает тому, каким оно было при жизни.
Иллюстрация： UN_DO
```

**Пример на японском языке:**
```
766
影紬が歴代魔王の屍を素材に造り上げた魔王人形のうちの一体。天女の如く美しい魔王と讃えられていたので、影紬は生前の美しさを可能な限り再現する形で仕上げたという。母親の影響で竜の特質が発現しており、肉体的にも極めて頑丈。その練達した刀さばきは、生前と比べて微塵も衰えていないという。
```

**Более подробный пример с разделами:**
```
237 # Минотавр 
Сильный монстр, обладающий мощью дикого быка. Умело обращается с топором.
Высокая защита компенсирует недостаток скорости и магической защиты.

Экипировка: Кэйкоги　Нагрудник　Шляпа　Роскошный венец
Навыки: Топоры　Дубины　Железный шар　Тех. Зверя  
Способности: Нет
```

#### Примеры для режима JobChange

**Пример на русском языке:**
```
65 # Ниндзя
Восточный убийца, живущий и умирающий в тени. Эффективно прерывает жизнь врагов уникальными техниками, известными как ниндзюцу. Также обладает огромной атакующей силой благодаря уникальному стилю с оружием в обеих руках. Обладает чрезвычайно высокой скоростью и уклонением, но низкой выносливостью и защитой.
Экипировка: Кинжал　Ниндзято　Кама
Навыки: Ниндзюцу 
Способности: Парное Оружие　Возможность экипировки кэйкоги
```

**Пример на японском языке:**  
```
65 # 忍者
闇に生き、闇に死する東方の暗殺者忍術と呼ばれる独特の技で、効率よく敵の命を絶つまた両手に武器を持つ独特のスタイルにより、攻撃力も絶大素早さや回避率は極めて高いが、体力や防御力は低い事に注意
装備武器：短剣　忍者刀　鎌
スキル：忍術
アビリティ：二刀流　武道着装備可能
```

#### Примеры для режима Skill Replacer

**Пример исходного текста со ссылками на навыки:**
```
Персонаж овладел уникальным Skill 123, который позволяет использовать Skill 45 и Skill 789. Также доступно пассивное умение Skill 1001, дающее 10% шанс нанести двойной урон при атаке.
```

**Пример файла Skills.txt:**
```
Skill 123 = "Танец клинков"
Skill 45 = "Рывок"
Skill 789 = "Ураганный удар" 
Skill 1001 = "Острота клинка"
```

**Результат после замены:**
```
Персонаж овладел уникальным Танец клинков, который позволяет использовать Рывок и Ураганный удар. Также доступно пассивное умение Острота клинка, дающее 10% шанс нанести двойной урон при атаке.
```

### Важные особенности форматирования

#### Идентификатор и заголовок

- Формат начинается с числового идентификатора
- Для JobChange после идентификатора следует символ `#` и название класса/профессии
- Для Library может быть просто числовой идентификатор без названия

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

### Настройка длины строки

- Используйте кнопки "+" и "-" в секции "ДЛИНА СТРОКИ" для изменения максимальной длины строки
- Для каждого режима и языка максимальная длина строки устанавливается независимо 
- Рекомендуемые значения:
  - RUS (Library): 39-45 символов
  - JAP (Library): 20-25 символов
  - JobChange: 30-35 символов
- Для режима Skill Replacer настройка длины строки не применяется

## Особенности форматирования

### Выходной формат данных

Скрипт автоматически преобразует исходный текст в структуру, совместимую с RPG Maker VX Ace. Пример выходного формата:

```
237 => # Минотавр
  [[
    "Сильный монстр, обладающий мощью дикого быка. Умело",
    "обращается с топором. Высокая защита компенсирует", 
    "недостаток скорости и магической защиты.",
],
[
    "Экипировка: Кэйкоги　Нагрудник　Шляпа　Роскошный венец",
    "Навыки: Топоры　Дубины　Железный шар　Тех. Зверя",
    "Способности: Нет",
  ]],
```

### Автоматический перенос

При превышении максимальной длины строки текст автоматически переносится на следующую строку с соблюдением корректных отступов.

### Обработка иллюстраций

Строки, начинающиеся с префикса "Иллюстрация:" или "イラスト：", обрабатываются специальным образом и помещаются в конец описания.

### Замена ссылок на навыки

В режиме Skill Replacer скрипт выполняет поиск ссылок на навыки в формате "Skill XXX" и заменяет их на фактические названия навыков, используя данные из загружаемого файла Skills.txt.

## Установка

1. Скачайте файл `Script_for_packing.html`
2. Откройте файл в любом современном веб-браузере
3. Никаких дополнительных установок или зависимостей не требуется

## Требования

- Современный веб-браузер с поддержкой JavaScript
- Поддержка кодировки UTF-8 для корректной работы с широкими пробелами и японскими символами

## Контрибуция

Вклады в проект приветствуются! Если у вас есть идеи по улучшению форматирования, новым функциям или замеченные ошибки, создавайте Issue или Pull Request.

## Лицензия

Этот проект распространяется под лицензией MIT. См. файл LICENSE для деталей.

---

**Примечание**: Скрипт создан специально для работы с переводом игры "もんむす・くえスト！RPG終章" и может потребовать модификации для использования с другими проектами RPG Maker.
