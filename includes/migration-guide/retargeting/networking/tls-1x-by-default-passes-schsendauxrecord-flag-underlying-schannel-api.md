---
ms.openlocfilehash: e7f690030a5cb5605645f1ca42a6f08dcdd214f5
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615766"
---
### <a name="tls-1x-by-default-passes-the-sch_send_aux_record-flag-to-the-underlying-schannel-api"></a>TLS 1.x по умолчанию передает флаг SCH_SEND_AUX_RECORD базовому API SCHANNEL

#### <a name="details"></a>Подробнее

При использовании TLS 1.x .NET Framework зависит от базового интерфейса API Windows SCHANNEL. Начиная с .NET Framework 4.6 флаг [SCH_SEND_AUX_RECORD](https://docs.microsoft.com/windows/win32/api/schannel/ns-schannel-schannel_cred) передается SCHANNEL по умолчанию. В результате SCHANNEL разбивает данные для шифрования на две отдельных записи. В первой — один байт, а во второй — <em>n</em>–1 байт. В редких случаях это нарушает логику взаимодействия между клиентами и существующими серверами, которая предполагает, что данные находятся в одной записи.

#### <a name="suggestion"></a>Предложение

Если это изменение нарушает связь с существующим сервером, вы можете отключить отправку флага [SCH_SEND_AUX_RECORD](https://docs.microsoft.com/windows/win32/api/schannel/ns-schannel-schannel_cred) и восстановить предыдущее поведение, при котором данные не разделяются на две записи, добавив следующий переключатель в элемент [<](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) в разделе [<](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) файла конфигурации приложения:

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Net.DontEnableSchSendAuxRecord=true" />
</runtime>
```

> [!IMPORTANT]
> Этот параметр предоставляется исключительно для обратной совместимости. Его использование в других целях не рекомендуется.

| name    | Значение       |
|:--------|:------------|
| Область   | Пограничный случай        |
| Version | 4.6         |
| Type    | Изменение целевой платформы |

#### <a name="affected-apis"></a>Затронутые API

- <xref:System.Net.Security.SslStream?displayProperty=nameWithType>
- <xref:System.Net.ServicePointManager?displayProperty=nameWithType>
- <xref:System.Net.Http.HttpClient?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.HttpWebRequest?displayProperty=nameWithType>
- <xref:System.Net.FtpWebRequest?displayProperty=nameWithType>
