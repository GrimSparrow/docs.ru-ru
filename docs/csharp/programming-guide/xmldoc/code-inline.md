---
title: Руководство по программированию на C#. <c>
ms.date: 07/20/2015
f1_keywords:
- c
- <c>
helpviewer_keywords:
- text, marking as code [C#]
- code, marking text as [C#]
- c C# XML tag
- <c> C# XML tag
ms.assetid: aad5b16e-a29e-445e-bd0d-eea0b138d7b2
ms.openlocfilehash: a09bcd069e2f85f4a21736cb218c42c0e481d70b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287471"
---
# <a name="c-c-programming-guide"></a>\<c> (руководство по программированию на C#)

## <a name="syntax"></a>Синтаксис

```xml
<c>text</c>
```

## <a name="parameters"></a>Параметры

- `text`

  Текст, который нужно указать в качестве кода.

## <a name="remarks"></a>Примечания

С помощью тега `<c>` можно указать, что текст в описании необходимо пометить как код. Чтобы определить несколько строк в качестве кода, используйте тег [\<code>](./code.md).

Чтобы обработать комментарии документации и сохранить их в файл, выполняйте сборку с параметром [-doc](../../language-reference/compiler-options/doc-compiler-option.md).

## <a name="example"></a>Пример

[!code-csharp[csProgGuideDocComments#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#2)]
  
## <a name="see-also"></a>См. также

- [Руководство по программированию на C#](../index.md)
- [Рекомендуемые теги для комментариев документации](./recommended-tags-for-documentation-comments.md)
