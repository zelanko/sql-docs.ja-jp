---
title: "PositionEnum |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- PositionEnum
helpviewer_keywords:
- PositionEnum enumeration
ms.assetid: e69af0a5-3405-4b72-9c6e-6b188ff746fd
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: c3f317b92d138f020a43f26d71cbadd0f0cd412e
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="positionenum"></a>PositionEnum
内のレコードのポインターの現在位置を示す、 [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)です。  
  
|定数|値|Description|  
|--------------|-----------|-----------------|  
|**adPosBOF**|-2|現在のレコードのポインターが BOF であることを示します (つまり、 [BOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md)プロパティは**True**)。|  
|**adPosEOF**|-3|現在のレコードのポインターが EOF であることを示します (つまり、 [EOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md)プロパティは**True**)。|  
|**adPosUnknown**|-1|示します、 **Recordset**が空で、現在の位置が不明、またはプロバイダーがサポートしていない、[と、AbsolutePage](../../../ado/reference/ado-api/absolutepage-property-ado.md)または[AbsolutePosition](../../../ado/reference/ado-api/absoluteposition-property-ado.md)プロパティです。|  
  
## <a name="adowfc-equivalent"></a>該当するショートカットは ADO/WFC  
 パッケージ: **com.ms.wfc.data**  
  
|定数|  
|--------------|  
|AdoEnums.Position.BOF|  
|AdoEnums.Position.EOF|  
|AdoEnums.Position.UNKNOWN|  
  
## <a name="applies-to"></a>適用対象  
  
|||  
|-|-|  
|[AbsolutePage プロパティ (ADO)](../../../ado/reference/ado-api/absolutepage-property-ado.md)|[AbsolutePosition プロパティ (ADO)](../../../ado/reference/ado-api/absoluteposition-property-ado.md)|

