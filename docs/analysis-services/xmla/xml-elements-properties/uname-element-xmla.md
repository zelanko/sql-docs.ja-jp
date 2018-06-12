---
title: UName 要素 (XMLA) |Microsoft ドキュメント
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 2c860bcd21f6c717bae06478ca1ec1194383a75b
ms.sourcegitcommit: cfe5b2af733e7801558b441b4b9427cfe4c26435
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/06/2018
ms.locfileid: "34577984"
---
# <a name="uname-element-xmla"></a>UName 要素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  親の一意の名前を含む[HierarchyInfo](../../../analysis-services/xmla/xml-elements-properties/hierarchyinfo-element-xmla.md)または[メンバー](../../../analysis-services/xmla/xml-elements-properties/member-element-xmla.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<HierarchyInfo> <!-- or Member -->  
   ...  
   <UName>...</UName>  
   ...  
</HierarchyInfo>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String|  
|既定値|なし|  
|Cardinality|1-1 : 必須要素で、1 回だけ出現します|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[HierarchyInfo](../../../analysis-services/xmla/xml-elements-properties/hierarchyinfo-element-xmla.md)、[メンバー](../../../analysis-services/xmla/xml-elements-properties/member-element-xmla.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 **HierarchyInfo** 、要素、 **UName**要素に一意のメンバー、階層の名前を提供するプロパティの名前が含まれています。 値は、OLE DB for OLAP 仕様で軸行セットに関して定義される、MEMBER_UNIQUE_NAME プロパティと同等です。  
  
 **メンバー** 、要素、 **UName**要素には、親の一意の名前が含まれています。**メンバー**要素。  
  
## <a name="see-also"></a>参照
 [プロパティ&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
