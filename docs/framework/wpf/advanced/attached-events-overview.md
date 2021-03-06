---
title: Общие сведения о вложенных событиях
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- handling attached events [WPF]
- defining attached events as routed events [WPF]
- attached events [WPF], scenarios for
- attached events vs. routed events [WPF]
- backing attached events with routed events [WPF]
- attached events [WPF], definition
ms.assetid: 2c40eae3-80e4-4a45-ae09-df6c9ab4d91e
ms.openlocfilehash: e125c9a57090049f4319da96c7004f06606d0147
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141566"
---
# <a name="attached-events-overview"></a>Общие сведения о вложенных событиях

Расширяемый язык разметки приложений (XAML) определяет языковую составляющую и тип события, называемый *прилагаемым событием.* Концепция присоединенного события позволяет добавить обработчик для конкретного события в произвольный элемент, а не в элемент, который фактически определяет или наследует событие. В этом случае ни объект, потенциально вызывающий событие, ни конечный обрабатывающий экземпляр не определяет или иным образом не "владеет" событием.  

<a name="prerequisites"></a>
## <a name="prerequisites"></a>Предварительные требования  
 Предполагается, что вы ознакомились с разделами [Общие сведения о перенаправленных событиях](routed-events-overview.md) и [Обзор XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md).  
  
<a name="Syntax"></a>
## <a name="attached-event-syntax"></a>Синтаксис присоединенных событий  
 Прилагаемые события имеют синтаксис XAML и шаблон кодирования, который должен использоваться резервным кодом для поддержки прилагаемого использования событий.  
  
 В синтаксисе XAML прилагаемое событие указывается не только названием события, но и типом владения плюс названием события, разделенным точкой (.). Так как имя события квалифицируется с помощью имени типа, которому оно принадлежит, синтаксис присоединенных событий позволяет подключить любое присоединенное событие к любому элементу, для которого может быть создан экземпляр.  
  
 Например, ниже приводится синтаксис XAML для крепления `NeedsCleaning` обработчика для пользовательского прилагаемого события:  
  
 [!code-xaml[WPFAquariumSln#AE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquarium/Window1.xaml#ae)]  
  
 Обратите внимание на префикс `aqua:`. Префикс необходим в этом случае, поскольку присоединенное событие является пользовательским событием, которое поступает из пользовательского сопоставленного xmlns.  
  
<a name="WPFImplements"></a>
## <a name="how-wpf-implements-attached-events"></a>Реализация присоединенных событий в WPF

В WPF прилагаемые <xref:System.Windows.RoutedEvent> события поддерживаются полем и направляются через дерево после их поднятия. Как правило, источником присоединенного события (объектом, вызывающим событие) является система или служба, и таким образом, объект, который выполняет код, порождающий это событие, не является непосредственной частью дерева элементов.  
  
<a name="Scenarios"></a>
## <a name="scenarios-for-attached-events"></a>Сценарии для присоединенных событий  
 В WPF прилагаемые события присутствуют в определенных областях функций, где есть <xref:System.Windows.Input.Mouse> абстракция уровня обслуживания, например для событий, включенных статическим классом или классом. <xref:System.Windows.Controls.Validation> Классы, которые взаимодействуют со службой или используют ее, могут использовать событие в синтаксисе присоединенных событий или предоставить присоединенное событие как перенаправленное событие, которое является частью процесса интеграции возможностей службы классом.  
  
 Хотя WPF определяет ряд прилагаемых событий, сценарии, в которых вы будете использовать или обрабатывать прикрепленное событие непосредственно, очень ограничены. Как правило, прилагаемые события служат цели архитектуры, но затем направляются на неприлагаемые (при поддержке события CLR "обертка") маршрутизированное событие.  
  
 Например, базовое прикрепленное <xref:System.Windows.Input.Mouse.MouseDown?displayProperty=nameWithType> событие можно легче обрабатывать <xref:System.Windows.UIElement> с <xref:System.Windows.UIElement.MouseDown> любым <xref:System.Windows.UIElement> приведенным, используя его, вместо того, чтобы иметь дело с прикрепленным синтаксисом события либо в XAML, либо в коде. Присоединенное событие выполняет определенную роль в архитектуре, поскольку оно обеспечивает будущее расширение типов устройств ввода. Гипотетическое устройство будет <xref:System.Windows.Input.Mouse.MouseDown?displayProperty=nameWithType> только нужно поднять для того, чтобы имитировать <xref:System.Windows.Input.Mouse> ввод мыши, и не нужно будет получать от этого. Однако этот сценарий включает обработку событий кодом, и обработка XAML прилагаемого события не имеет отношения к данному сценарию.  
  
<a name="Handling"></a>
## <a name="handling-an-attached-event-in-wpf"></a>Обработка присоединенного события в WPF  
 Процесс для обработки присоединенного события и код обработчика, который вы будете писать, по сути аналогичны перенаправленному событию.  
  
 В целом прилагаемый WPF событие не сильно отличается от маршрутизированного события WPF. Различия заключаются в том, как происходит исходное событие и как оно подвергается воздействию класса в качестве члена (что также влияет на синтаксис обработчика XAML).  
  
 Однако, как отмечалось ранее, существующие прилагаемые WPF события не предназначены для обработки в WPF. Гораздо чаще целью событий является включение составного элемента для передачи состояния в родительский элемент при компоновке. В этом случае событие обычно вызывается в коде и зависит от обработки класса в соответствующем родительском классе. <xref:System.Windows.Controls.Primitives.Selector> Например, элементы внутри события, как <xref:System.Windows.Controls.Primitives.Selector.Selected> ожидается, повысят <xref:System.Windows.Controls.Primitives.Selector> прикрепленное событие, которое затем обрабатывается классом класса, а затем потенциально преобразуется <xref:System.Windows.Controls.Primitives.Selector> классом в другое маршрутизированное событие. <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> Дополнительные сведения о перенаправленных событиях и обработке классов см. в разделе [Маркировка перенаправленных событий как обработанных и обработка классов](marking-routed-events-as-handled-and-class-handling.md).  
  
<a name="Custom"></a>
## <a name="defining-your-own-attached-events-as-routed-events"></a>Определение собственных присоединенных событий как перенаправленных событий  
 Если вы вытекаете из общих базовых классов WPF, вы можете реализовать свои собственные прилагаемые события, включив определенные методы шаблона в свой класс и используя утилиты, которые уже присутствуют на базовых классах.  
  
 Шаблон выглядит следующим образом.  
  
- Метод __Добавить*обработчик EventName*__ с двумя параметрами. Первым параметром является экземпляр, к которому добавляется обработчик событий. Вторым параметром является обработчик событий для добавления. Метод должен `public` быть `static`и, без значения возврата.  
  
- Метод __Удалить обработчик*EventName*__ с двумя параметрами. Первым параметром является экземпляр, из которого удаляется обработчик событий. Вторым параметром является удаление обработчика событий. Метод должен `public` быть `static`и, без значения возврата.  
  
 Метод __аксессуара Add*EventName*Обработчик__ облегчает обработку XAML при заявленных атрибутах обработчика событий на элементе. Методы __«Добавить обработчик*событий»*__ и __«Удалить*обработчик событий»*__ также позволяют получить доступ к коду в хранилище обработчиков событий для прилагаемого события.  
  
 Этот общий шаблон еще не является достаточно точным для практической реализации в рамках, поскольку любая реализация чтения XAML может иметь различные схемы для определения основных событий в поддерживающем языке и архитектуре. Это одна из причин того, что WPF реализует прилагаемые события как маршрутизированные события; идентификатор для использования<xref:System.Windows.RoutedEvent>для события () уже определен системой событий WPF. Кроме того, routing событие является естественным расширением реализации концепции xAML языкового уровня прилагаемого события.  
  
 Реализация __Add*EventName*Handler__ для прилагаемого события <xref:System.Windows.UIElement.AddHandler%2A> WPF состоит из вызова с маршрутизированным событием и обработчика в качестве аргументов.  
  
 Эта стратегия реализации и система маршрутных событий в целом <xref:System.Windows.UIElement> ограничивают обработку прикрепленных событий либо производными классами, либо производными классами, так как <xref:System.Windows.ContentElement> только эти классы имеют <xref:System.Windows.UIElement.AddHandler%2A> реализации.  
  
 Например, следующий код `NeedsCleaning` определяет прикрепленное событие `Aquarium`в классе владельца, используя прилагаемую WPF стратегию события, объявляющую прикрепленное событие маршрутизированным событием.  
  
 [!code-csharp[WPFAquariumSln#AECode](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#aecode)]
 [!code-vb[WPFAquariumSln#AECode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#aecode)]  
  
 Обратите внимание, что метод, используемый для <xref:System.Windows.EventManager.RegisterRoutedEvent%2A>создания прикрепленного поля идентификатора событий, на самом деле является тем же методом, который используется для регистрации неприкрепленного маршрутизированного события. Все присоединенные события и перенаправленные события регистрируются в централизованном внутреннем хранилище. Эта реализация хранилища событий обеспечивает поддержку режима "события в качестве интерфейса", который рассматривается в разделе [Общие сведения о перенаправленных событиях](routed-events-overview.md).  
  
<a name="Raising"></a>
## <a name="raising-a-wpf-attached-event"></a>Вызов присоединенного события WPF  
 Обычно не требуется поднимать из кода существующие прилагаемые WPF события. Эти события следуют общей концептуальной модели «обслуживания», а классы обслуживания, такие как, <xref:System.Windows.Input.InputManager> отвечают за повышение событий.  
  
 Однако, если вы определяете пользовательское прикрепленное событие, основанное <xref:System.Windows.RoutedEvent>на модели <xref:System.Windows.UIElement.RaiseEvent%2A> WPF, основывая прилагаемые события на, вы можете использовать для поднятия прикрепленного события из любого <xref:System.Windows.UIElement> или <xref:System.Windows.ContentElement>. Повышение маршрутизированного события (прикреплено или нет) требует, чтобы вы объявили определенный элемент дерева элемента в качестве источника событий; этот источник сообщается <xref:System.Windows.UIElement.RaiseEvent%2A> в качестве вызываемого абонента. За определение того, какой элемент передается как источник в дереве, отвечает служба.  
  
## <a name="see-also"></a>См. также раздел

- [Общие сведения о перенаправленных событиях](routed-events-overview.md)
- [Подробное описание синтаксиса XAML](xaml-syntax-in-detail.md)
- [Код XAML и пользовательские классы для WPF](xaml-and-custom-classes-for-wpf.md)
