---
title: Строки
description: Узнайте, как тип «строки» F's представляет собой неизменяемый текст в виде последовательности символов Unicode.
ms.date: 07/05/2019
ms.openlocfilehash: 242a2cefa1cce8995090dddd1d1fd7181e0f5e0c
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739568"
---
# <a name="strings"></a>Строки

> [!NOTE]
> Ссылки на справочник по API в этой статье ведут на сайт MSDN.  Работа над справочником по API docs.microsoft.com не завершена.

Тип `string` представляет собой неизменяемый текст как последовательность символов Unicode. `string` — это псевдоним для `System.String` в .NET Framework.

## <a name="remarks"></a>Примечания

Строки буквальные знаки разграничены характером кавычки () . Символ backslash \\ () используется для кодирования определенных специальных символов. Backslash и следующий символ вместе известны как *побег последовательности*. Последовательности побега, поддерживаемые в буквах строки F', отображаются в следующей таблице.

|Символ|Escape-последовательность|
|---------|---------------|
|Предупреждение|`\a`|
|Отмена|`\b`|
|Подача страницы|`\f`|
|Новая строка|`\n`|
|Возврат каретки|`\r`|
|Вкладка|`\t`|
|Вертикальная табуляция|`\v`|
|Обратная косая черта|`\\`|
|Знак кавычек|`\"`|
|Апостроф|`\'`|
|символьный формат Юникода|`\DDD`(где `D` указывается десятичная цифра; диапазон 000 - 255; например, `\231` q "q")|
|символьный формат Юникода|`\xHH`(где `H` указывается гексадецимальная цифра; диапазон 00 `\xE7` - FF; например, q "q")|
|символьный формат Юникода|`\uHHHH`(UTF-16) (где `H` указываетг гексадецимальная цифра; диапазон 0000 - FFFF;  например, `\u00E7` "кв")|
|символьный формат Юникода|`\U00HHHHHH`(UTF-32) (где `H` указываетг гексадецимальная цифра; диапазон 000000 - 10FFFF;  например, `\U0001F47D` «»👽« »)|

> [!IMPORTANT]
> Последовательность `\DDD` побега является десятичной нотации, а не октальной нотации, как в большинстве других языков. Таким образом, `8` `9` цифры и являются `\032` действительными, и последовательность представляет пространство (U'0020), в `\040`то время как тот же кодовый пункт в октальной нотации будет .

> [!NOTE]
> Будучи ограниченным к диапазону 0 - 255 `\DDD` (0xFF), и `\x` последовательности побега фактически [ISO-8859-1](https://en.wikipedia.org/wiki/ISO/IEC_8859-1#Code_page_layout) набор символов, так как что соответствует первым 256 Unicode кодовых точек.

## <a name="verbatim-strings"></a>Дословные струны

Если предшествует символ а, буквальный является дословной строки. Это означает, что любые последовательности побега игнорируются, за исключением того, что два символа метки цитатинтерно интерпретируются как один символ метки цитаты.

## <a name="triple-quoted-strings"></a>Тройные цитируемые струны

Кроме того, строка может быть заключена тройными котировками. В этом случае все последовательности побега игнорируются, включая символы двойной отметки цитаты. Чтобы указать строку, содержащую встроенную строку, можно использовать дословную строку или тройную строку. Если вы используете строку стенографии, необходимо указать два символа метки цитаты, чтобы указать один символ метки цитаты. Если вы используете строку с тройным капотом, вы можете использовать символы одной метки цитаты без их разогнания в конце строки. Этот метод может быть полезен при работе с XML или другими структурами, которые включают встроенные кавычки.

```fsharp
// Using a verbatim string
let xmlFragment1 = @"<book author=""Milton, John"" title=""Paradise Lost"">"

// Using a triple-quoted string
let xmlFragment2 = """<book author="Milton, John" title="Paradise Lost">"""
```

В коде принимаются строки с разрывами строк, а разрывы строк интерпретируются буквально как новые линии, если только символ backslash не является последним символом перед разрывом строки. Ведущее белое пространство на следующей строке игнорируется при использовании символа backslash. Следующий код создает `str1` строку, которая `str2` имеет `"abcdef"`значение `"abc\ndef"` и строку, которая имеет значение.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1001.fs)]

## <a name="string-indexing-and-slicing"></a>Индексирование строк и нарезка

Вы можете получить доступ к отдельным символам в строке, используя массив, как синтаксис, следующим образом.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1002.fs)]

В результате получается `b`.

Или вы можете извлечь подстроки с помощью синтаксиса срезов массива, как показано в следующем коде.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1003.fs)]

Выходные данные выглядят следующим образом.

```console
abc
def
```

Вы можете представлять строки ASCII по массивам `byte[]`неподписанных байтов, введите тип. Вы добавляете суффикс `B` в строку буквально, чтобы указать, что это строка ASCII. Буквальные буквы ASCII, используемые с байт-массивами, поддерживают те же последовательности побега, что и строки Unicode, за исключением последовательностей выхода Unicode.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1004.fs)]

## <a name="string-operators"></a>Операторы струнных

Оператор `+` может использоваться для совмещения строк, сохраняя совместимость с функциями обработки строк .NET Framework. Следующий пример иллюстрирует конкатацию строки.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1006.fs)]

## <a name="string-class"></a>Струнный класс

Поскольку тип строки в F-на `System.String` самом деле `System.String` является типом рамочного соглашения .NET, все участники доступны. Это включает `+` в себя оператора, который используется для `Length` совмещения строк, свойство и `Chars` свойство, которое возвращает строку в виде массива символов Unicode. Для получения дополнительной информации `System.String`о строках см.

Используя `Chars` `System.String`свойство, вы можете получить доступ к отдельным символам в строке, указав индекс, как показано в следующем коде.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1005.fs)]

## <a name="string-module"></a>Струнный модуль

Дополнительная функциональность для обработки `String` строк `FSharp.Core` включена в модуль в пространстве имен. Для получения дополнительной информации [см.](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d)

## <a name="see-also"></a>См. также

- [Ссылка на язык F](index.md)
