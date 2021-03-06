---
title: Выбор правильного размещения в Azure
description: Узнайте, какой способ переноса в Azure подходит для вашего веб-приложения ASP.NET.
author: CESARDELATORRE
ms.author: cesardl
ms.date: 03/01/2020
ms.openlocfilehash: a8ad946b03f97272cb8685620858af6b21a372dc
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/09/2020
ms.locfileid: "81433352"
---
# <a name="choose-the-right-azure-hosting-option"></a>Выбор правильного размещения в Azure

В этой статье сравниваются варианты, доступные в Azure при переносе существующих приложений .NET Framework из локальной среды в Azure.

При переносе существующих приложений .NET Framework в Azure следует учитывать следующие важные аспекты:

1. Варианты вычислительных сред.
1. Варианты баз данных.
1. Сетевые подключения и безопасность
1. Проверка подлинности и авторизация.

## <a name="compute-choices"></a>Варианты вычислительных сред.

Для переноса существующих приложений .NET Framework в Azure существует несколько вариантов. Но так как платформа .NET Framework работает только с ОС Windows, эти варианты ограничиваются службами вычислений на базе Windows.

В таблице ниже приводится несколько сравнений и рекомендаций, которые помогут вам выбрать правильную вычислительную среду при переносе существующего приложения .NET.

|                 | Виртуальные машины Azure | Служба приложений Azure | Контейнеры Windows |
|-----------------|-----------|-------------------|--------------------|
|Время использования      |<ul><li>Приложение в значительной степени зависит от сервера и локально хранящихся MSI-файлов установки.</li><li>Вам нужен самый простой способ переноса приложения</li></ul>|Приложение не зависит от сервера, это просто "чистое" веб-приложение ASP.NET (MVC, WebForm) или n-уровневое приложение (Web API, WCF) с доступом к серверу базы данных. |<ul><li>Приложение зависит от сервера-источника, но эти зависимости можно включить в образ Docker Windows.</li><li>Необходимость модернизировать приложение, чтобы подготовить его к процессам [DevOps в облаке](../../architecture/modernize-with-azure-containers/modernize-existing-apps-to-cloud-optimized/reasons-to-modernize-existing-net-apps-to-cloud-optimized-applications.md).</li></ul>|
|Преимущества  |<ul><li>Самый простой способ переноса.</li><li>Знакомая среда. В качестве среды развертывания используется виртуальная машина, что соответствует локальным серверам.</li></ul> |Текущее обслуживание PaaS — простой способ масштабирования приложений и управления ими в Azure. |<ul><li>Подготовка к новым возможностям и процессам DevOps в облаке с зависимостями, включенными в контейнеры приложений.</li><li>Практически нет необходимости в рефакторинге кода .NET или C#.</li></ul> |
|Минусы             |Это инфраструктура как услуга (IaaS). Обслуживание обходится дорого. Необходимость управлять такими элементами инфраструктуры виртуальных машин, как сеть, подсистема балансировки нагрузки, горизонтальное масштабирование, службы IIS и т. д. |<ul><li>[Поддерживаются](https://appmigration.microsoft.com/assessment) не все приложения.</li><li>Для некоторых приложений требуется выполнять рефакторинг и даже незначительно изменять архитектуру, чтобы они поддерживали службу приложений Azure.</li></ul> |<ul><li>Курс обучения навыкам работы с Docker.</li><li>Требуется изменить некоторые параметры конфигурации приложения и код.</li></ul>|
|Требования |Виртуальная машина Windows Server с такими же требованиями, как и для приложения в локальной среде. | Требования к Службе приложений Azure, указанные в инструкциях по [проверке готовности](https://github.com/Azure/App-Service-Migration-Assistant/wiki/Readiness-Checks). |<ul><li>[Модуль Docker — Enterprise для Windows Server 2019](https://azuremarketplace.microsoft.com/marketplace/apps/cloud-infrastructure-services.docker-windows-2019)<br />or</li><li>[Служба контейнеров Azure (AKS)](https://azure.microsoft.com/services/container-service/) (то есть оркестратор Kubernetes)<br />or<li>оркестратор [Azure Service Fabric](https://azure.microsoft.com/services/service-fabric/)</li></ul> |
|Как осуществить перенос |См. статью [Перенос веб-приложения ASP.NET на виртуальную машину Azure](vm.md). | См. статью [Перенос веб-приложения ASP.NET в службу приложений Azure](app-service.md). | Следуйте рекомендациям, сценариям и пошаговым инструкциям, которые приводятся в электронной книге [Modernize existing .NET applications with Azure cloud and Windows Containers](https://aka.ms/liftandshiftwithcontainersebook) (Модернизация существующих приложений .NET с помощью облака Azure и контейнеров Windows). |

На следующей блок-схеме показано дерево принятия решений при планировании переноса существующих приложений .NET Framework в Azure. Хотя вариант Б является самым простым, по возможности попробуйте сначала вариант А.

![Блок-схема, на которой показано дерево принятия решений по размещению](../media/migration/choose/decision-tree.png)

## <a name="database-choices"></a>Варианты баз данных.

Для переноса реляционных баз данных в Azure существует несколько вариантов. Чтобы выбрать правильный способ переноса для существующего приложения .NET, см. статью [Перенос базы данных SQL Server в Azure](sql.md).

## <a name="networking-and-security-considerations"></a>Сетевые подключения и безопасность

При развертывании приложений в общедоступном облаке, таком как Microsoft Azure, может потребоваться изолировать и защитить некоторые сети. Для этого можно [создать сети периметра](https://docs.microsoft.com/azure/architecture/reference-architectures/dmz/), например [сеть периметра между Azure и локальным центром обработки данных](https://docs.microsoft.com/azure/architecture/reference-architectures/dmz/secure-vnet-hybrid) или [сеть периметра между Azure и Интернетом](https://docs.microsoft.com/azure/architecture/reference-architectures/dmz/secure-vnet-dmz). Вы можете реализовать сети периметра, используя [виртуальные сети Microsoft Azure](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview).

Виртуальные сети Azure позволяют выполнять следующие задачи:

- Создание управляемой гибридной инфраструктуры.
- Использование собственных IP-адресов и DNS-серверов.
- Обеспечение безопасности подключений с помощью VPN-соединения IPsec или ExpressRoute.
- Детальный контроль над трафиком между подсетями.
- Создание сложных сетевых топологий с виртуальными модулями.
- Создание изолированной и безопасной среды для ваших приложений.

Чтобы приступить к созданию собственной виртуальной сети, изучите [документацию по виртуальным сетям Azure](https://docs.microsoft.com/azure/virtual-network/).

## <a name="authentication-and-authorization-considerations-when-migrating-to-azure"></a>Проверка подлинности и авторизация при переносе в Azure

Безопасность — самый важный вопрос для любой организации, которая переносит свои данные в облако. Большинство компаний тратят много времени, денег и усилий разработчиков на создание и разработку модели безопасности. Поэтому важно, чтобы компании могли использовать существующие ресурсы, например хранилища удостоверений и решения для единого входа.

Большинство существующих корпоративных приложений .NET B2E, которые выполняются в локальной среде, используют Active Directory для проверки подлинности и управления удостоверениями. Azure AD Connect позволяет интегрировать локальные каталоги с Azure Active Directory. Чтобы приступить к работе, изучите статью [Интеграция локальных каталогов с Azure Active Directory](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect).

При планировании дальнейших действий с Azure Active Directory ознакомьтесь со статьей [Определение требований к идентификации для решений гибридной идентификации](https://docs.microsoft.com/azure/active-directory/active-directory-hybrid-identity-design-considerations-business-needs).

Другие варианты связаны с протоколами проверки подлинности [OAuth](https://en.wikipedia.org/wiki/OAuth) и [OpenID](https://en.wikipedia.org/wiki/OpenID), которые часто используются в клиентских приложениях. Как правило, когда применяются автономные базы данных удостоверений, например базы данных SQL удостоверений ASP.NET с программой-оболочкой IdentityServer4, использующей OAuth, подключение к локальным базам данных или каталогам не требуется.

## <a name="next-steps"></a>Следующие шаги

> [!div class="nextstepaction"]
> [Перенос веб-приложения ASP.NET в службу приложений Azure](app-service.md)
