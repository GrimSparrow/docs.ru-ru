---
title: Добавление столбцов в таблицу данных
description: Объект DataTable содержит объекты DataColumn, на которые ссылается свойство Columns таблицы. Используйте этот пример кода для добавления столбцов в таблицу в ADO.NET.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e85c4a0e-4f3f-458c-b58b-0ddbc06bf974
ms.openlocfilehash: 9d6d21696acd7a6b63cfd6d2ea7e906ec2acd7c9
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286951"
---
# <a name="adding-columns-to-a-datatable"></a>Добавление столбцов в таблицу данных
Объект <xref:System.Data.DataTable> содержит коллекцию <xref:System.Data.DataColumn> объектов, на которые ссылается свойство **Columns** таблицы. Эта коллекция столбцов наряду с ограничениями определяет схему, или структуру, таблицы.  
  
 Объекты **DataColumn** создаются в таблице с помощью конструктора **DataColumn** или путем вызова метода **Add** свойства **Columns** таблицы, то есть <xref:System.Data.DataColumnCollection> . Метод **Add** принимает необязательные аргументы **ColumnName**, **DataType**и **Expression** и создает новый **столбец** данных в качестве члена коллекции. Он также принимает существующий объект **DataColumn** и добавляет его в коллекцию и возвращает ссылку на добавленный **DataColumn-столбец** по запросу. Поскольку объекты **DataTable** не относятся к какому-либо источнику данных, .NET Framework типы используются при указании типа данных **DataColumn**.  
  
 В следующем примере в **таблицу DataTable**добавляются четыре столбца.  
  
```vb  
Dim workTable As DataTable = New DataTable("Customers")  
  
Dim workCol As DataColumn = workTable.Columns.Add( _  
    "CustID", Type.GetType("System.Int32"))  
workCol.AllowDBNull = false  
workCol.Unique = true  
  
workTable.Columns.Add("CustLName", Type.GetType("System.String"))  
workTable.Columns.Add("CustFName", Type.GetType("System.String"))  
workTable.Columns.Add("Purchases", Type.GetType("System.Double"))  
```  
  
```csharp  
DataTable workTable = new DataTable("Customers");  
  
DataColumn workCol = workTable.Columns.Add("CustID", typeof(Int32));  
workCol.AllowDBNull = false;  
workCol.Unique = true;  
  
workTable.Columns.Add("CustLName", typeof(String));  
workTable.Columns.Add("CustFName", typeof(String));  
workTable.Columns.Add("Purchases", typeof(Double));  
```  
  
 Обратите внимание, что в этом примере свойству для столбца **CustID** присвоено значение, которое не разрешает значения **DBNull** и ограничивает значения уникальными. Однако если определить столбец **CustID** в качестве первичного ключевого столбца таблицы, то свойству **AllowDbNull** автоматически будет присвоено значение **false** , а свойству **UNIQUE** будет автоматически присвоено значение **true**. Дополнительные сведения см. в разделе [Определение первичных ключей](defining-primary-keys.md).  
  
> [!CAUTION]
> Если имя столбца не указано для столбца, то столбцу присваивается добавочное имя по умолчанию для столбца*N,* начинающееся с «Column1», при добавлении в **датаколумнколлектион**. Рекомендуется избегать использования соглашения об именовании "Column*N*" при указании имени столбца, так как указываемое имя может конфликтовать с существующим именем столбца по умолчанию в **датаколумнколлектион**. Если указанное имя уже существует, вызывается исключение.  
  
 Если элемент <xref:System.Xml.Linq.XElement> используется в качестве <xref:System.Data.DataColumn.DataType%2A> объекта <xref:System.Data.DataColumn> в <xref:System.Data.DataTable>, то XML-сериализация не будет работать при считывании данных. Например, если документ <xref:System.Xml.XmlDocument> записывается методом `DataTable.WriteXml`, то во время сериализации в XML-код создается дополнительный родительский узел в элементе <xref:System.Xml.Linq.XElement>. Чтобы избежать этой проблемы, используйте тип <xref:System.Data.SqlTypes.SqlXml> вместо <xref:System.Xml.Linq.XElement>. Методы `ReadXml` и `WriteXml` правильно работают с <xref:System.Data.SqlTypes.SqlXml>.  
  
## <a name="see-also"></a>См. также

- <xref:System.Data.DataColumn>
- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataTable>
- [Определение схемы таблицы данных](datatable-schema-definition.md)
- [DataTables](datatables.md)
- [Общие сведения об ADO.NET](../ado-net-overview.md)
