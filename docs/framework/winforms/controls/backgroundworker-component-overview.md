---
title: Общие сведения о компоненте BackgroundWorker
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- BackgroundWorker
helpviewer_keywords:
- BackgroundWorker component
- background tasks
- Asynchronous Pattern
- forms [Windows Forms], multithreading
- components [Windows Forms], asynchronous
- forms [Windows Forms], background operations
- threading [Windows Forms], background operations
- background operations
ms.assetid: 64e9b3ab-7443-4a77-ab17-b8b8c0cb3f62
ms.openlocfilehash: e91d74b7ca5515dd63ba17a9111cadf5090dae2a
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046105"
---
# <a name="backgroundworker-component-overview"></a>Общие сведения о компоненте BackgroundWorker
Выполнение многих часто выполняемых операций может занимать длительное время. Например:  
  
- Загрузка изображений  
  
- Вызовы веб-служб  
  
- Скачивание и загрузка файлов (в т. ч. через одноранговые приложения)  
  
- Сложные локальные вычисления  
  
- Транзакции баз данных  
  
- Обращение к локальному диску в случае низкой скорости по сравнению с доступом к памяти  
  
 Такие операции могут привести к блокировке пользовательского интерфейса во время их выполнения. Если вы хотите получить отзывчивый пользовательский интерфейс, но столкнулись с длительными задержками в результате выполнения таких операций, удобным решением станет компонент <xref:System.ComponentModel.BackgroundWorker>.  
  
 Компонент <xref:System.ComponentModel.BackgroundWorker> позволяет выполнять длительные операции асинхронно (в фоновом режиме), т. е. в потоке, отличающемся от основного потока пользовательского интерфейса. Для использование компонента <xref:System.ComponentModel.BackgroundWorker> необходимо только указать, какой рабочий метод обработки длительных операций будет выполняться в фоновом режиме, а затем вызвать метод <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A>. Вызывающий поток продолжает работать нормально, в то время как рабочий метод работает асинхронно. Когда метод закончит работу, компонент <xref:System.ComponentModel.BackgroundWorker> предупредит вызывающий поток событием <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted>, которое может содержать результаты операции.  
  
 Компонент доступен в **области элементов**на вкладке **компоненты.** <xref:System.ComponentModel.BackgroundWorker> Чтобы добавить компонент <xref:System.ComponentModel.BackgroundWorker> в форму, перетащите компонент <xref:System.ComponentModel.BackgroundWorker> в соответствующую форму. Он отображается в области компонентов, и его свойства отображаются в окне **Свойства** .  
  
 Для запуска асинхронной работы используйте метод <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A>. <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A>принимает необязательный `object` параметр, который можно использовать для передачи аргументов в рабочий метод. Класс <xref:System.ComponentModel.BackgroundWorker> показывает событие <xref:System.ComponentModel.BackgroundWorker.DoWork>, к которому обработчик событий <xref:System.ComponentModel.BackgroundWorker.DoWork> прикрепляет рабочий поток.  
  
 Обработчик событий <xref:System.ComponentModel.BackgroundWorker.DoWork> задействует параметр <xref:System.ComponentModel.DoWorkEventArgs> со свойством <xref:System.ComponentModel.DoWorkEventArgs.Argument%2A>. Данное свойство получает параметр из <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> и может быть передано в рабочий метод, который будет вызываться в обработчике событий <xref:System.ComponentModel.BackgroundWorker.DoWork>. В следующем примере показан способ назначения результата из рабочего метода, который называется `ComputeFibonacci`. Он является частью большого примера, который можно найти в [следующих руководствах: Реализуйте форму, которая использует фоновую](how-to-implement-a-form-that-uses-a-background-operation.md)операцию.  
  
 [!code-cpp[System.ComponentModel.BackgroundWorker#5](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#5)]
 [!code-csharp[System.ComponentModel.BackgroundWorker#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#5)]
 [!code-vb[System.ComponentModel.BackgroundWorker#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#5)]  
  
 Дополнительные сведения об использовании обработчиков событий см. в разделе [события](../../../standard/events/index.md).  
  
> [!CAUTION]
> При использовании любой многопоточности существует потенциальная возможность возникновения серьезных ошибок. Перед реализацией любого решения, в котором используется многопоточность, ознакомьтесь с разделом [Рекомендации по работе с потоками](../../../standard/threading/managed-threading-best-practices.md).  
  
 Дополнительные сведения об использовании <xref:System.ComponentModel.BackgroundWorker> класса см. в разделе как [ Фоновое выполнение операции](how-to-run-an-operation-in-the-background.md).  
  
## <a name="see-also"></a>См. также

- [Управляемая поточность](../../../standard/threading/index.md)
- [Обзор асинхронной модели, основанной на событиях](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
- [Практическое руководство. Реализация формы, в которой выполняется фоновая операция](how-to-implement-a-form-that-uses-a-background-operation.md)
