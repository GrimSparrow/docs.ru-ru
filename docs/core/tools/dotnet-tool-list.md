---
title: Команда dotnet tool list
description: Команда dotnet tool list выводит список средств .NET Core, установленных на компьютере.
ms.date: 02/14/2020
ms.openlocfilehash: 7ca894ab0f5daf0118ff92fb39e0118b952b3d83
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2020
ms.locfileid: "84768278"
---
# <a name="dotnet-tool-list"></a>dotnet tool list

**Эта статья относится к следующему.** ✔️ SDK для .NET Core 2.1 и более поздних версий

## <a name="name"></a>name

`dotnet tool list` — выводит все [средства .NET Core](global-tools.md) указанного типа, установленных на компьютере в настоящее время.

## <a name="synopsis"></a>Краткий обзор

```dotnetcli
dotnet tool list -g|--global

dotnet tool list --tool-path <PATH>

dotnet tool list --local

dotnet tool list

dotnet tool list -h|--help
```

## <a name="description"></a>Описание

Команда `dotnet tool list` позволяет получить список всех установленных на компьютере глобальных, установочных и локальных средств .NET Core. Эта команда выводит имя пакета, установленную версию и команду средства.  Чтобы использовать эту команду, необходимо указать один из следующих параметров:

* Чтобы получить список глобальных средств, установленных в расположении по умолчанию, используйте параметр `--global`.
* Чтобы получить список глобальных средств, установленных в настраиваемом расположении, используйте параметр `--tool-path`.
* Для перечисления локальных средств — локальное средство. Используйте параметр `--local` или опустите параметры `--global`, `--tool-path` и `--local`.

**Локальные средства доступны в пакете SDK для .NET Core, начиная с версии 3.0.**

## <a name="options"></a>Параметры

- **`-g|--global`**

  Выводит глобальные средства на уровне пользователя. Не может использоваться вместе с параметром `--tool-path`. Пропуск `--global` и `--tool-path` выводит локальные инструменты.

- **`-h|--help`**

  Выводит краткую справку по команде.

- **`--local`**

  Выдает список локальных средств для текущего каталога. Не сочетается с параметрами `--global` и `--tool-path`. Если не указывать `--global` и `--tool-path`, выдает список локальных средств, даже если `--local` не заданы.

- **`--tool-path <PATH>`**

  Задает пользовательское расположение для глобальных средств. Путь может быть абсолютным или относительным. Не может использоваться вместе с параметром `--global`. Пропуск `--global` и `--tool-path` выводит локальные инструменты.

## <a name="examples"></a>Примеры

- **`dotnet tool list -g`**

  Выводит все глобальные средства, установленные на уровне пользователя на вашем компьютере (для текущего профиля пользователя).

- **`dotnet tool list --tool-path c:\global-tools`**

  Выводит глобальные средства в определенном каталоге Windows.

- **`dotnet tool list --tool-path ~/bin`**

  Выводит глобальные средства в определенном каталоге Linux/macOS.

- **`dotnet tool list`** или **`dotnet tool list --local`**

  Выводит все локальные средства, доступные в текущем каталоге.

## <a name="see-also"></a>См. также

- [Средства .NET Core](global-tools.md)
- [Учебник. Установка и использование глобального средства .NET Core с помощью интерфейса командной строки .NET Core](global-tools-how-to-use.md)
- [Учебник. Установка и использование локального средства .NET Core с помощью интерфейса командной строки .NET Core](local-tools-how-to-use.md)
