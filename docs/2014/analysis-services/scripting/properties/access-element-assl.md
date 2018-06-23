---
title: 要素 (ASSL) にアクセス |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Access Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Access
helpviewer_keywords:
- Access element
ms.assetid: 6ad99010-fac5-48e9-a099-ecbca380e127
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: d1eea0d7e8b0d26692c2cc6e0400d4ceaf7aa8ad
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36174245"
---
# <a name="access-element-assl"></a>Access 要素 (ASSL)
  与えられるアクセス レベルを示す、 [CellPermission](../objects/cellpermission-element-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<CellPermission>  
   ...  
   <Access>...</Access>  
   ...  
</CellPermission>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String (列挙型)|  
|既定値|なし|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[CellPermission](../objects/cellpermission-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 この要素の値は、次の表に示す文字列の 1 つに制限されます。  
  
|値|説明|  
|-----------|-----------------|  
|*読み取り*|読み取り専用のアクセスが許可されます。|  
|*ReadContingent*|条件付き読み取りアクセスが許可されます。|  
|*読み取り/書き込み*|読み取り/書き込みアクセスが許可されます。|  
  
 許可される値に対応する列挙`Access`分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.CellPermissionAccess>します。  
  
## <a name="see-also"></a>参照  
 [Role 要素&#40;ASSL&#41;](../objects/role-element-assl.md)   
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  