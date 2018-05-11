---
title: DbSchemaName 要素 (ASSL) |Microsoft ドキュメント
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 6ba82fbaf67e801725c87160486131b2f27cdd83
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="dbschemaname-element-assl"></a>DbSchemaName 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  によって識別されるテーブル内の親要素によって使用されるスキーマの名前を含む、 [DbTableName](../../../analysis-services/scripting/properties/dbtablename-element-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<TableBinding> <!-- or TableNotification -->  
   ...  
   <DbSchemaName>...</DbSchemaName>  
   ...  
</TableBinding>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|文字列|  
|既定値|なし|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[TableBinding](../../../analysis-services/scripting/data-type/tablebinding-data-type-assl.md)、 [TableNotification](../../../analysis-services/scripting/objects/tablenotification-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 親に対応する要素**DbSchemaName**分析管理オブジェクト (AMO) オブジェクト モデルには<xref:Microsoft.AnalysisServices.TableBinding>と<xref:Microsoft.AnalysisServices.TableNotification>です。  
  
## <a name="see-also"></a>参照  
 [プロパティ & #40 です。ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
