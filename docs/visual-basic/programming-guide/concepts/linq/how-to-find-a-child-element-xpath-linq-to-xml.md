---
title: Практическое руководство. Поиск дочернего элемента (XPath-LINQ to XML)
ms.date: 07/20/2015
ms.assetid: adb46c98-a650-42e2-b62d-835920fe8421
ms.openlocfilehash: 1b0a3af5a1679643d73649f9de6b1dc3c44cbb0d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2020
ms.locfileid: "84357171"
---
# <a name="how-to-find-a-child-element-xpath-linq-to-xml-visual-basic"></a>Как найти дочерний элемент (XPath-LINQ to XML) (Visual Basic)
В этом разделе сравнивается ось дочерних элементов XPath с методом [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XContainer.Element%2A>.  
  
 Выражение XPath - `DeliveryNotes`.  
  
## <a name="example"></a>Пример  
 В этом примере производится поиск дочернего элемента `DeliveryNotes`.  
  
 В этом примере используется следующий XML-документ: [Пример XML-файла. Несколько заказов на покупку (LINQ to XML)](sample-xml-file-multiple-purchase-orders-linq-to-xml.md).  
  
```vb  
Dim cpo As XDocument = XDocument.Load("PurchaseOrders.xml")  
Dim po As XElement = cpo.Root.<PurchaseOrder>.FirstOrDefault  
  
'LINQ to XML query  
Dim el1 As XElement = po.<DeliveryNotes>.FirstOrDefault  
  
' XPath expression  
Dim el2 As XElement = po.XPathSelectElement("DeliveryNotes")  
' same as "child::DeliveryNotes"  
' same as "./DeliveryNotes"  
  
If el1 Is el2 Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
Console.WriteLine(el1)  
```  
  
 В этом примере выводятся следующие данные:  
  
```console
Results are identical  
<DeliveryNotes>Please leave packages in shed by driveway.</DeliveryNotes>  
```  
  
## <a name="see-also"></a>См. также

- [LINQ to XML для пользователей XPath (Visual Basic)](linq-to-xml-for-xpath-users.md)
