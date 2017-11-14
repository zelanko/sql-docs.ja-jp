---
title: "要素 (ASSL) にアクセス |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: scripting
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- Access Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- Access
helpviewer_keywords:
- Access element
ms.assetid: 6ad99010-fac5-48e9-a099-ecbca380e127
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: f04bafc11cdda8d9c0e82b6cb8dee3e3916099eb
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="access-element-assl"></a>Access 要素 (ASSL)
  与えられるアクセス レベルを示す、 [CellPermission](../../../analysis-services/scripting/objects/cellpermission-element-assl.md)要素。  
  
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
|親要素|[CellPermission](../../../analysis-services/scripting/objects/cellpermission-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 この要素の値は、次の表に示す文字列の 1 つに制限されます。  
  
|値|Description|  
|-----------|-----------------|  
|*読み取り*|読み取り専用のアクセスが許可されます。|  
|*ReadContingent*|条件付き読み取りアクセスが許可されます。|  
|*読み取り/書き込み*|読み取り/書き込みアクセスが許可されます。|  
  
 許可される値に対応する列挙**アクセス**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.CellPermissionAccess>します。  
  
## <a name="see-also"></a>参照  
 [Role 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/objects/role-element-assl.md)   
 [プロパティ & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

