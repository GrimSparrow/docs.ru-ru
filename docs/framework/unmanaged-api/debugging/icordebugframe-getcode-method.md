---
title: Метод ICorDebugFrame::GetCode
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetCode
helpviewer_keywords:
- GetCode method, ICorDebugFrame interface [.NET Framework debugging]
- ICorDebugFrame::GetCode method [.NET Framework debugging]
ms.assetid: fbaa0794-a031-4015-8beb-2749e47ac340
topic_type:
- apiref
ms.openlocfilehash: c8914ba1090ec5fd6540e9ead302675cb44f37e6
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/12/2020
ms.locfileid: "83208607"
---
# <a name="icordebugframegetcode-method"></a>Метод ICorDebugFrame::GetCode
Возвращает указатель на код, связанный с этим кадром стека.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetCode (  
    [out] ICorDebugCode      **ppCode  
);  
```  
  
## <a name="parameters"></a>Параметры  
 `ppCode`  
 заполняет Указатель на адрес объекта ICorDebugCode, представляющий код, связанный с этим кадром.  
  
## <a name="requirements"></a>Требования  
 **Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).  
  
 **Заголовок:** CorDebug.idl, CorDebug.h  
  
 **Библиотека:** CorGuids.lib  
  
 **.NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
