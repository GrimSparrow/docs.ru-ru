---
title: Изменение порядка столбцов в элементе управления DataGridView с помощью конструктора
ms.date: 03/30/2017
helpviewer_keywords:
- columns [Windows Forms], order of
- DataGridView control [Windows Forms], column order
- Windows Forms, columns
- data [Windows Forms], displaying
ms.assetid: 7fe52a98-75d6-448c-97a5-65ca2c568c1a
ms.openlocfilehash: 7540203fb1c0465caeb045275734d1a7c6f25ee8
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628752"
---
# <a name="how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a>Практическое руководство. Изменение порядка столбцов элемента управления DataGridView в формах Windows Forms с помощью конструктора

При привязке элемента управления Windows Forms <xref:System.Windows.Forms.DataGridView> к источнику данных порядок вывода автоматически создаваемых столбцов определяется источником данных. Если этот порядок не является предпочтительным, можно изменить порядок столбцов с помощью конструктора. Кроме того, может потребоваться добавить в элемент управления несвязанные столбцы и изменить их порядок их вывода. Дополнительные сведения об изменении порядка столбцов программным способом см. в разделе [как изменить порядок столбцов в элементе управления Windows Forms DataGridView](how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control.md).

Для следующей процедуры требуется проект **приложения Windows** с формой, содержащей элемент управления <xref:System.Windows.Forms.DataGridView>. Сведения о настройке такого проекта см. в статьях [как создать проект приложения Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) и [как добавить элементы управления в Windows Forms](how-to-add-controls-to-windows-forms.md).

## <a name="to-change-the-column-order-using-the-designer"></a>Изменение порядка столбцов с помощью конструктора

1. Щелкните глиф действия конструктора (![маленькая черная стрелка](./media/designer-actions-glyph.gif)) в правом верхнем углу элемента управления <xref:System.Windows.Forms.DataGridView>, а затем выберите **изменить столбцы**.

2. Выберите столбец из списка **Выбранные столбцы** .

3. Щелкните стрелку вверх или вниз справа от списка **Выбранные столбцы** , пока выбранный столбец не будет расположен в нужном месте.

## <a name="see-also"></a>См. также раздел

- <xref:System.Windows.Forms.DataGridView>
- [Практическое руководство. Добавление и удаление столбцов элемента управления DataGridView в формах Windows Forms с помощью конструктора](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [Как создать проект приложения Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Практическое руководство. Добавление элементов управления в формы Windows Forms](how-to-add-controls-to-windows-forms.md)
