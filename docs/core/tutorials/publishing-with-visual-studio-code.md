---
title: Публикация консольного приложения .NET Core с помощью Visual Studio Code
description: При публикации создается набор файлов, которые необходимы для запуска приложения .NET Core.
ms.date: 06/08/2020
ms.openlocfilehash: 442d08c9b016407327ba30db0aae78b5cf6b6fe3
ms.sourcegitcommit: 1cbd77da54405ea7dba343ac0334fb03237d25d2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2020
ms.locfileid: "84701454"
---
# <a name="tutorial-publish-a-net-core-console-application-using-visual-studio-code"></a>Учебник. Публикация консольного приложения .NET Core с помощью Visual Studio Code

В этом руководстве показано, как опубликовать консольное приложение, чтобы его могли запускать другие пользователи. При публикации создается набор файлов, которые необходимы для запуска приложения. Чтобы развернуть файлы, скопируйте их на целевой компьютер.

Для публикации приложения используется .NET Core CLI, поэтому приведенные в этом руководстве действия при желании можно выполнять в редакторе кода, отличном от Visual Studio Code.

## <a name="prerequisites"></a>Предварительные требования

- В этом руководстве используется консольное приложение, созданное в руководстве [Создание консольного приложения .NET Core в Visual Studio Code](with-visual-studio-code.md).

## <a name="publish-the-app"></a>Публикация приложения

1. Запустите Visual Studio Code.

1. Откройте папку проекта *HelloWorld*, созданного в руководстве [Создание консольного приложения .NET Core в Visual Studio Code](with-visual-studio-code.md).

1. В главном меню выберите **Вид** > **Терминал**.

   Терминал откроется в папке *HelloWorld*.

1. Выполните следующую команду:

   ```dotnetcli
   dotnet publish --configuration Release
   ```

   По умолчанию используется конфигурация сборки *Отладка*, поэтому эта команда задает конфигурацию сборки *Выпуск*. Выходные данные конфигурации сборки "Выпуск" содержат минимальную символическую отладочную информацию и полностью оптимизированы.

   Результат команды должен быть примерно таким:

   ```
   Microsoft (R) Build Engine version 16.6.0+5ff7b0c9e for .NET Core
   Copyright (C) Microsoft Corporation. All rights reserved.

   Determining projects to restore...
   All projects are up-to-date for restore.
   HelloWorld -> C:\Projects\HelloWorld\bin\Release\netcoreapp3.1\HelloWorld.dll
   HelloWorld -> C:\Projects\HelloWorld\bin\Release\netcoreapp3.1\publish\
   ```

## <a name="inspect-the-files"></a>Проверка файлов

По умолчанию в ходе публикации создается платформенно-зависимое развертывание. При таком развертывании опубликованное приложение выполняется на компьютере с установленной средой выполнения .NET Core. Чтобы запустить опубликованное приложение, можно использовать исполняемый файл или выполнить команду `dotnet HelloWorld.dll` из командной строки.

В следующих шагах будут рассмотрены файлы, созданные в процессе публикации.

1. Выберите **Обозреватель** на панели навигации слева.

1. Разверните узел *bin/Release/netcoreapp3.1/publish*.

   :::image type="content" source="media/publishing-with-visual-studio-code/published-files-output.png" alt-text="Опубликованные файлы в обозревателе":::

   Как показано на рисунке, опубликованные выходные данные включают следующие файлы:

   * *HelloWorld.deps.json*

      Это файл зависимостей среды выполнения приложения. Он определяет библиотеки и компоненты .NET Core (включая библиотеку DLL, содержащую приложение), необходимые для запуска приложения. Дополнительные сведения см. в разделе [Runtime Configuration Files](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md) (Файлы конфигурации среды выполнения).

   * *HelloWorld.dll*

      Это версия [зависимого от платформы развертывания](../deploying/deploy-with-cli.md#framework-dependent-deployment) приложения. Чтобы выполнить эту библиотеку динамической компоновки, введите `dotnet HelloWorld.dll` в командной строке. Этот метод запуска приложения работает на любой платформе, где установлена среда выполнения .NET Core.

   * *HelloWorld.exe* (приложение *HelloWorld* в Linux, не созданное в macOS.)

      Это версия [исполняемого, зависящего от платформы файла](../deploying/deploy-with-cli.md#framework-dependent-executable) приложения. Файл зависит от операционной системы.

   * *HelloWorld.pdb* (необязателен для развертывания)

      Это файл отладочных символов. Этот файл не нужно распространять вместе с приложением, но желательно сохранить его на случай, если придется выполнять отладку опубликованной версии приложения.

   * *HelloWorld.runtimeconfig.json*

      Это файл конфигурации среды выполнения для приложения. Он определяет версию платформы .NET Core, для которой предназначено приложение. Кроме того, в него можно добавить параметры конфигурации. Дополнительные сведения см. в статье [Параметры конфигурации среды выполнения .NET Core](../run-time-config/index.md#runtimeconfigjson).

## <a name="run-the-published-app"></a>Запуск опубликованного приложения

1. В **обозревателе** щелкните правой кнопкой мыши папку *publish* (в macOS нажмите <kbd>CTRL</kbd>+щелчок) и выберите **Открыть в терминале**.

   :::image type="content" source="media/publishing-with-visual-studio-code/open-in-terminal.png" alt-text="Контекстное меню с командой Открыть в терминале":::

1. В Windows или Linux запустите приложение с помощью исполняемого файла.

   1. В Windows введите `.\HelloWorld.exe` и нажмите клавишу <kbd>ВВОД</kbd>.

   1. В Linux введите `./HelloWorld` и нажмите клавишу <kbd>ВВОД</kbd>.

   1. В ответ на запрос введите имя и нажмите любую клавишу, чтобы выйти.

1. На любой платформе запустите приложение с помощью команды [`dotnet`](../tools/dotnet.md):

   1. Введите `dotnet HelloWorld.dll` и нажмите клавишу <kbd>ВВОД</kbd>.

   1. В ответ на запрос введите имя и нажмите любую клавишу, чтобы выйти.

## <a name="additional-resources"></a>Дополнительные ресурсы

- [Развертывание приложений .NET Core](../deploying/index.md)

## <a name="next-steps"></a>Следующие шаги

В этом руководстве вы опубликовали консольное приложение. Далее вы создадите библиотеку классов.

> [!div class="nextstepaction"]
> [Создание библиотеки .NET Standard в Visual Studio для Mac](library-with-visual-studio-mac.md)
