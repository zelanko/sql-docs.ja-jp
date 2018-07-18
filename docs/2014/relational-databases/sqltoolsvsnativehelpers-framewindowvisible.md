---
title: FrameWindowVisible | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 9091d714-98bc-43ec-b8d1-9c892cb57f19
caps.latest.revision: 6
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 12d0e87d50f96dbd69973b5c196303d4286a5ec5
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37325562"
---
# <a name="framewindowvisible"></a>FrameWindowVisible
  指定されたウィンドウ フレームを表示するかどうかを示すプロパティです。 ヘルパー メソッドは、マネージド コードから使用されます。  
  
## <a name="syntax"></a>構文  
  
```  
  
BOOL WINAPI IsFrameWindowVisible(IVsWindowFrame* frame)  
{  
    if (NULL == frame)  
    {  
        return FALSE;  
    }  
  
    return S_OK == frame->IsVisible();  
}  
```  
  
#### <a name="parameters"></a>パラメーター  
 *frame*  
  
 Visual Studio WindowFrame への IVsWindowFrame* ポインターです。  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 *frame* で指定したウィンドウ フレームを表示するかどうかを指定するブール値です。  
  

<!-- Necessary temporarily. GeneMi, 2018-05-01.
     But 'release-sql2014-migration' should win the Conflict Resolution later in May, because this will then be a good link!
## See Also  
 [SqlToolsVSNativeHelpers](sqltoolsvsnativehelpers.md)  
-->
  
  
