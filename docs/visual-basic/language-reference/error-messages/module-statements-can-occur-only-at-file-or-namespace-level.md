---
title: Операторы Module могут присутствовать только на уровне файлов или пространств имен
ms.date: 07/20/2015
f1_keywords:
- bc30617
- vbc30617
helpviewer_keywords:
- BC30617
ms.assetid: 5e9de8e5-d26b-4fb2-9e28-814413fe9cef
ms.openlocfilehash: d01c30571fc34e142300ac8706c56d5e99175fcf
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397211"
---
# <a name="module-statements-can-occur-only-at-file-or-namespace-level"></a>Операторы Module могут присутствовать только на уровне файлов или пространств имен
`Module`операторы должны находиться в верхней части исходного файла сразу после `Option` и `Imports` инструкций, глобальных атрибутов и объявлений пространств имен, но перед всеми остальными объявлениями.  
  
 **Идентификатор ошибки:** BC30617  
  
## <a name="to-correct-this-error"></a>Исправление ошибки  
  
- Переместите оператор `Module` в начало объявления пространства имен или исходного файла.  
  
## <a name="see-also"></a>См. также раздел

- [Оператор Module](../statements/module-statement.md)
