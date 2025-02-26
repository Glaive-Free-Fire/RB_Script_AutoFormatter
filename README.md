# RB Script AutoFormatter

Данный проект содержит два скрипта для преобразования текста между скриптовым и читаемым форматами. 
Идеально подходит для работы с игровыми текстами, данными приложений или другими структурированными данными.

## 📦 Содержание
- `Script_for_unpacking.html` — распаковывает скриптованный текст в удобочитаемый формат.
- `Script_for_packing.html` — упаковывает текст обратно в скриптовый формат.

---

## 🛠️ Особенности

### `Script_for_unpacking.html`
- Поддерживает два режима:
  - **JobChange**: Обработка записей вида `число => #Заголовок` с извлечением списков.
  - **Library (Enemy)**: Работа с блоками данных, содержащими многострочные записи и иллюстрации.
- Автоматическое форматирование текста.
- Кнопка копирования результата.

### `Script_for_packing.html`
- Поддержка двух языков:
  - **RUS** (макс. длина строки: 39 символов).
  - **JAP** (макс. длина строки: 22 символа).
- Регулировка длины строки (±1 символ).
- Обработка иллюстраций (автоматическое объединение с предыдущим абзацем).
- Экранирование кавычек в тексте.
- Кнопка копирования результата.

---

## 🚀 Использование

1. **Запуск скриптов**:
   - Откройте файлы в любом современном браузере (Chrome, Firefox, Edge).
   - Никаких дополнительных установок не требуется.

2. **Инструкция для `Script_for_unpacking.html`**:
   - Выберите вкладку (`JobChange` или `Library`).
   - Вставьте скриптованный текст в левое поле.
   - Результат появится справа. Используйте кнопку **«Копировать результат»**.

3. **Инструкция для `Script_for_packing.html`**:
   - Выберите язык (RUS/JAP).
   - Отрегулируйте длину строки при необходимости.
   - Вставьте распакованный текст в левое поле.
   - Результат упаковки отобразится справа. Используйте кнопку **«Копировать результат»**.

---

## 📝 Примеры

### Распаковка (`Script_for_unpacking.html`):
**Ввод:**

123 => #Пример
[[ "Строка1", "Строка2" ], [ "Часть1", "Часть2" ]]

**Вывод:**
123 # Пример
Строка1Строка2

Часть1
Часть2

### Упаковка (`Script_for_packing.html`):
**Ввод (RUS):**
456
Привет, это тестовый текст.
Иллюстрация: автор

Copy
**Вывод:**
456 => [
"Привет, это тестовый текст.",
"",
"Иллюстрация: автор",
],


---

## 🔧 Технические детали
- Скрипты работают на чистом JavaScript.
- Для JAP-режима используется разбивка по символам, для RUS — по словам.
- Пустые строки автоматически форматируются как разделители.
- Поддерживается обработка многострочных блоков, начинающихся с цифр.

---

## 📜 Лицензия
Проект распространяется по лицензии MIT. Используйте свободно в любых целях.

---

## 📮 Обратная связь
Обнаружили баг или есть предложения?  
Пишите: ismayilovelchin1984@gmail.com
