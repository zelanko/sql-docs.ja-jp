---
title: 要素 (ASSL) にアクセス |Microsoft ドキュメント
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 00bcd1f7cb86e66f521c0dd95c265225f4cf1ef1
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
ms.locfileid: "34036429"
---
# <a name="access-element-assl"></a>Access 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
 [Role 要素 & #40 です。ASSL & #41;](../../../analysis-services/scripting/objects/role-element-assl.md)   
 [プロパティ & #40 です。ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
