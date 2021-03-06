---
title: Обзор
description: Узнайте, как можно использовать Windows Forms для создания смарт-клиентов, отвечающих потребностям современных предприятий и конечных пользователей.
ms.date: 03/30/2017
helpviewer_keywords:
- smart clients
- Windows Forms, about Windows Forms
ms.assetid: 3a2b6284-c8d6-4e1c-8c69-0bed38f38cd4
ms.openlocfilehash: 820d5bae54ecb5a868314197d6a7e45e097b57de
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325992"
---
# <a name="windows-forms-overview"></a>Обзор Windows Forms

В этом обзоре рассматриваются преимущества интеллектуальных клиентских приложений, основные возможности программирования Windows Forms, а также использование Windows Forms для разработки интеллектуальных клиентов, удовлетворяющих запросам современных предприятий и конечных пользователей.

## <a name="windows-forms-and-smart-client-apps"></a>Windows Forms и интеллектуальные клиентские приложения

 Windows Forms позволяет разрабатывать интеллектуальные клиенты. *Интеллектуальный клиент* — это приложение с полнофункциональным графическим интерфейсом, простое в развертывании и обновлении, способное работать при наличии или отсутствии подключения к Интернету и использующее более безопасный доступ к ресурсам на локальном компьютере по сравнению с традиционными приложениями Windows.

### <a name="build-rich-interactive-user-interfaces"></a>Создание многофункциональных интерактивных пользовательских интерфейсов

 Windows Forms — это технология интеллектуальных клиентов для NET Framework. Она представляет собой набор управляемых библиотек, упрощающих выполнение стандартных задач, таких как чтение из файловой системы и запись в нее. С помощью такой среды разработки, как Visual Studio, можно создавать интеллектуальные клиентские приложения Windows Forms, которые отображают информацию, запрашивают ввод от пользователей и обмениваются данными с удаленными компьютерами по сети.

 В Windows Forms *форма* — это визуальная поверхность, на которой выводится информация для пользователя. Обычно приложение Windows Forms строится путем помещения элементов управления на форму и написания кода для реагирования на действия пользователя, такие как щелчки мыши или нажатия клавиш. *Элемент управления* — это отдельный элемент пользовательского интерфейса, предназначенный для отображения или ввода данных.

 При выполнении пользователем какого-либо действия с формой или одним из ее элементов управления создается событие. Приложение реагирует на эти события с помощью кода и обрабатывает события при их возникновении. Подробнее см. в разделе [Создание обработчиков событий в Windows Forms](creating-event-handlers-in-windows-forms.md).

 Windows Forms включает широкий набор элементов управления, которые можно добавлять на формы: текстовые поля, кнопки, раскрывающиеся списки, переключатели и даже веб-страницы. Список всех элементов управления, которые можно использовать в форме, представлены в разделе [Элементы управления для использования в формах Windows Forms](./controls/controls-to-use-on-windows-forms.md). Если существующий элемент управления не удовлетворяет потребностям, в Windows Forms можно создать пользовательские элементы управления с помощью класса <xref:System.Windows.Forms.UserControl>.

 В состав Windows Forms входят многофункциональные элементы пользовательского интерфейса, позволяющие воссоздавать возможности таких сложных приложений, как Microsoft Office. Используя элементы управления <xref:System.Windows.Forms.ToolStrip> и <xref:System.Windows.Forms.MenuStrip>, можно создавать панели инструментов и меню, содержащие текст и рисунки, подменю и другие элементы управления, такие как текстовые поля и поля со списками.

 С помощью **конструктор Windows Forms** перетаскивания в Visual Studio можно легко создавать Windows Forms приложения. Достаточно выделить элемент управления курсором и поместить его в нужное место на форме. Для преодоления трудностей, связанных с выравниванием элементов управления, конструктор предоставляет такие средства, как линии сетки и линии привязки. А также при использовании Visual Studio или компиляции из командной строки можно использовать <xref:System.Windows.Forms.FlowLayoutPanel> <xref:System.Windows.Forms.TableLayoutPanel> <xref:System.Windows.Forms.SplitContainer> элементы управления, и для создания расширенных макетов форм за меньшее время.

 Наконец, если нужно создать свои собственные элементы пользовательского интерфейса, пространство имен <xref:System.Drawing> содержит широкий набор классов, необходимых для отрисовки линий, кругов и других фигур непосредственно на форме.

> [!NOTE]
> Элементы управления Windows Forms не предназначены для маршалинга между доменами приложений. По этой причине технологии Майкрософт не поддерживают передачу элементов управления Windows Forms через границы <xref:System.AppDomain>, хотя на первый взгляд базовый тип <xref:System.Windows.Controls.Control> класса <xref:System.MarshalByRefObject> подразумевает такую возможность. Приложения Windows Forms с несколькими доменами приложений поддерживаются только при условии, что элементы управления Windows Forms не передаются через границы доменов приложения.

#### <a name="create-forms-and-controls"></a>Создание форм и элементов управления

Пошаговые инструкции по использованию этих возможностей можно найти в приведенных ниже разделах справки.

|Описание|Раздел справки|
|-----------------|----------------|
|Использование элементов управления в формах|[Практическое руководство. Добавление элементов управления в формы Windows Forms.](./controls/how-to-add-controls-to-windows-forms.md)|
|Использование элемента управления <xref:System.Windows.Forms.ToolStrip>|[Практическое руководство. Создание базового элемента управления ToolStrip со стандартными элементами с помощью конструктора](./controls/create-a-basic-wf-toolstrip-with-standard-items-using-the-designer.md)|
|Создание графических элементов с помощью <xref:System.Drawing>|[Приступая к программированию графики](./advanced/getting-started-with-graphics-programming.md)|
|Создание пользовательских элементов управления|[Практическое руководство. Наследование класса UserControl](./controls/how-to-inherit-from-the-usercontrol-class.md)|

### <a name="display-and-manipulate-data"></a>Отображение данных и работа с ними
 Во многих приложениях нужно отображать данные из базы данных, XML-файла, веб-службы XML или другого источника данных. Windows Forms предоставляет гибкий элемент управления с именем <xref:System.Windows.Forms.DataGridView> для отображения таких табличных данных в традиционном формате строк и столбцов так, что каждый фрагмент данных занимает свою собственную ячейку. С помощью <xref:System.Windows.Forms.DataGridView> можно, помимо прочего, настроить внешний вид отдельных ячеек, зафиксировать строки и столбцы на своем месте, а также обеспечить отображение сложных элементов управления внутри ячеек.

 При использовании интеллектуальных клиентов Windows Forms можно легко подключаться к источникам данных по сети. <xref:System.Windows.Forms.BindingSource>Компонент представляет соединение с источником данных и предоставляет методы для привязки данных к элементам управления, перехода к предыдущим и следующим записям, изменения записей и сохранения изменений в исходном источнике. Элемент управления <xref:System.Windows.Forms.BindingNavigator> предоставляет простой интерфейс на основе компонента <xref:System.Windows.Forms.BindingSource> для перехода между записями.

 Вы можете легко создавать элементы управления с привязкой к данным с помощью окна "Источники данных". В нем приводятся имеющиеся в проекте источники данных, такие как базы данных, веб-службы и объекты. Создавать элементы управления с привязкой к данным можно путем перетаскивания объектов из этого окна в формы проекта. Также можно связывать существующие элементы управления с данными, перетаскивая объекты из окна "Источники данных" в существующие элементы управления.

 Другой тип привязки к данным в формах Windows Forms — это *параметры*. Большинство интеллектуальных клиентских приложений должны сохранять некоторые сведения о своем состоянии во время выполнения, такие как последние известные размеры форм, а также сохранять пользовательские предпочтения, например место сохранения файлов по умолчанию. Параметры приложения отвечает этим требованиям, предоставляя простой способ хранения обоих типов сведений на клиентском компьютере. После определения этих параметров с помощью Visual Studio или редактора кода параметры сохраняются в формате XML и автоматически считываются обратно в память во время выполнения.

#### <a name="display-and-manipulate-data"></a>Отображение данных и работа с ними

Пошаговые инструкции по использованию этих возможностей можно найти в приведенных ниже разделах справки.

|Описание|Раздел справки|
|-----------------|----------------|
|Использование компонента <xref:System.Windows.Forms.BindingSource>|[Практическое руководство. Связывание элементов управления Windows Forms с компонентом BindingSource с помощью конструктора](./controls/bind-wf-controls-with-the-bindingsource.md)|
|Работа с источниками данных ADO.NET|[Практическое руководство. Сортировка и фильтрация данных ADO.NET с помощью компонента BindingSource в Windows Forms](./controls/sort-and-filter-ado-net-data-with-wf-bindingsource-component.md)|
|Использование окна "Источники данных"|[Привязка элементов управления Windows Forms к данным в Visual Studio](/visualstudio/data-tools/bind-windows-forms-controls-to-data-in-visual-studio)|
|Работа с параметрами приложения|[Практическое руководство. Создание параметров приложения](./advanced/how-to-create-application-settings.md)|

### <a name="deploy-apps-to-client-computers"></a>Развертывание приложений на клиентских компьютерах

После создания приложения необходимо отправить его пользователям, чтобы они могли установить и запустить его на своих клиентских компьютерах. При использовании технологии ClickOnce можно развертывать приложения в Visual Studio, используя всего несколько щелчков мышью, и предоставить пользователям URL-адрес, указывающий на ваше приложение в Интернете. Технология ClickOnce управляет всеми элементами и зависимостями в приложении и обеспечивает правильную установку приложения на клиентском компьютере.

Приложения ClickOnce можно настроить для запуска только в том случае, если пользователь подключен к сети или работает как в сети, так и в автономном режиме. При указании того, что приложение должно поддерживать автономную работу, ClickOnce добавляет ссылку на приложение в меню " **Пуск** " пользователя. Пользователь может открыть приложение без использования URL-адреса.

Когда вы обновляете приложение, на веб-сервере публикуется новый манифест развертывания и новая копия приложения. ClickOnce обнаружит, что доступно обновление, и обновите установку пользователя. для обновления старых сборок не требуется пользовательское программирование.

#### <a name="deploy-clickonce-apps"></a>Развертывание приложений ClickOnce

Полное введение в ClickOnce см. в статье [безопасность и развертывание ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment). Пошаговые инструкции по использованию этих возможностей можно найти в приведенных ниже разделах справки.

|Описание|Раздел справки|
|-----------------|----------------|
|Развертывание приложения с помощью ClickOnce|[Практическое руководство. Публикация приложения ClickOnce с помощью мастера публикации](/visualstudio/deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard)<br /><br /> [Разбор примера: развертывание вручную приложения ClickOnce](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-application)|
|Обновление развертывания ClickOnce|[Руководство. Управление обновлениями для приложения ClickOnce](/visualstudio/deployment/how-to-manage-updates-for-a-clickonce-application)|
|Управление безопасностью с помощью ClickOnce|[Практическое руководство. Включение параметров безопасности ClickOnce-приложений](/visualstudio/deployment/how-to-enable-clickonce-security-settings)|

### <a name="other-controls-and-features"></a>Другие элементы управления и функции

В Windows Forms имеется множество других возможностей, которые упрощают и ускоряют реализацию общих задач, таких как создание диалоговых окон, печать, добавление справки и документации, а также локализация приложений на различных языках. Кроме того, Windows Forms полагается на надежную систему безопасности .NET Framework. Благодаря ей можно создавать более надежные приложения.

#### <a name="implement-other-controls-and-features"></a>Реализация других элементов управления и функций

Пошаговые инструкции по использованию этих возможностей можно найти в приведенных ниже разделах справки.

|Описание|Раздел справки|
|-----------------|----------------|
|Печать содержимого формы|[Практическое руководство. Печать графических изображений в Windows Forms](./advanced/how-to-print-graphics-in-windows-forms.md)<br /><br /> [Практическое руководство. Печать многостраничных текстовых файлов в Windows Forms](./advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md)|
|Дополнительные сведения о безопасности форм Windows Forms|[Общие сведения о безопасности в Windows Forms](security-in-windows-forms-overview.md)|

## <a name="see-also"></a>См. также

- [начало работы с Windows Forms](getting-started-with-windows-forms.md)
- [Создание новой формы Windows Forms](creating-a-new-windows-form.md)
- [Общие сведения об элементе управления ToolStrip](./controls/toolstrip-control-overview-windows-forms.md)
- [Общие сведения об элементе управления DataGridView](./controls/datagridview-control-overview-windows-forms.md)
- [Общие сведения о компоненте BindingSource](./controls/bindingsource-component-overview.md)
- [Общие сведения о параметрах приложений](./advanced/application-settings-overview.md)
- [Развертывание и безопасность технологии ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment)
