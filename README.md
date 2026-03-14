# Unicode в глубину

Серия технических статей о стандарте Unicode — от основ до внутреннего устройства библиотек.

## О серии

Unicode — это не просто «поддержка разных языков». Это сложный стандарт с базой данных символов, алгоритмами нормализации, сортировки, разбиения текста на кластеры. Эта серия разбирает Unicode изнутри: файлы стандарта, алгоритмы, реализации в Python и Node.js, исходники библиотеки ICU.

Каждая статья сопровождается запускаемыми примерами кода (Python и/или Node.js), которые можно найти в [репозитории](https://github.com/comtextspace/unicode).

---

## Статьи

### [1. Основы Unicode: кодовые точки, плоскости, блоки](docs/01-basics/article.md)

История создания Unicode, кодовые точки, 17 плоскостей (BMP и за её пределами), блоки, скрипты и категории символов. Всё что нужно знать перед тем, как идти глубже.

### [2. Unicode Character Database (UCD): файлы и структура](docs/02-ucd-files/article.md)

Где живут данные Unicode и как их читать. Разбираем `UnicodeData.txt`, `Blocks.txt`, `Scripts.txt`, `PropList.txt`, `EastAsianWidth.txt` и другие файлы UCD вручную — без библиотек.

### [3. Кодировки: UTF-8, UTF-16, UTF-32](docs/03-encodings/article.md)

Чем кодировка отличается от кодового пространства. Алгоритм UTF-8 побайтово, суррогатные пары UTF-16, BOM (включая UTF-8 BOM). Ловушки: почему `len('🌍') == 2` в JavaScript, Variation Selectors и графемные кластеры.

### [4. Нормализация Unicode: NFD, NFC, NFKD, NFKC](docs/04-normalization/article.md)

Почему одна и та же буква может быть разными байтами. Каноническая и совместимая декомпозиция, Canonical Combining Class, обратная композиция. Где это важно: сравнение строк, пароли, безопасность, Confusables (UTS #39).

### [5. Коллация: Unicode Collation Algorithm и CLDR](docs/05-collation/article.md)

Почему `sort()` врёт для большинства языков. Многоуровневые веса L1/L2/L3, таблица DUCET, локальные правила CLDR. Примеры с PyICU и `Intl.Collator`.

### [6. Unicode на практике: Linux, инструменты, исходники ICU](docs/06-linux-tools/article.md)

Утилиты `uniname`, `iconv`, `hexdump`. Структура репозитория ICU и как читать исходники коллации. Модуль `regex` с поддержкой `\p{Script=Cyrillic}`. Практический скрипт-анализатор Unicode-состава текста.

---

## Примеры кода

Все примеры есть в репозитории рядом с каждой статьёй:

| Статья | Python | Node.js |
|---|---|---|
| 1. Основы | `docs/01-basics/examples.py` | `docs/01-basics/examples.js` |
| 2. UCD файлы | `docs/02-ucd-files/examples.py` | — |
| 3. Кодировки | `docs/03-encodings/examples.py` | `docs/03-encodings/examples.js` |
| 4. Нормализация | `docs/04-normalization/examples.py` | `docs/04-normalization/examples.js` |
| 5. Коллация | `docs/05-collation/examples.py` | `docs/05-collation/examples.js` |
| 6. Linux/ICU | `docs/06-linux-tools/examples.py` | — |

### Быстрый старт

```bash
# Запустить примеры Python (без зависимостей для большинства)
python3 docs/01-basics/examples.py

# Анализатор Unicode-состава произвольного текста
python3 docs/06-linux-tools/examples.py myfile.txt

# Node.js примеры
node docs/01-basics/examples.js
```

---

## Ресурсы

Ссылки на спецификации, UCD-файлы, документацию библиотек — в разделе [Ресурсы](docs/resources.md).
