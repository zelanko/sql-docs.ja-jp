---
title: オブジェクトの要素 (XMLA) |Microsoft ドキュメント
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f9ef2f645895e567d69d06e4e1383e0c477b6ed1
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/02/2018
ms.locfileid: "34575914"
---
# <a name="object-element-xmla"></a>Object 要素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  親要素によって使用されるオブジェクト参照を含みます。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Alter> <!-- or any of the parent elements in the Element relationships table -->  
...  
   <Object>  
      <!-- One or more object identifiers, depending on the parent element -->  
   </Object>  
...  
</Alter>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|Cardinality|次の表を参照してください。|  
  
|先祖または親|Cardinality|  
|------------------------|-----------------|  
|[Alter](../../../analysis-services/xmla/xml-elements-commands/create-element-xmla.md)|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
|他のすべて|1-1 : 必須要素で、1 回だけ出現します|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[Alter](../../../analysis-services/xmla/xml-elements-commands/alter-element-xmla.md)、[バックアップ](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md)、 [ClearCache](../../../analysis-services/xmla/xml-elements-commands/clearcache-element-xmla.md)、[削除](../../../analysis-services/xmla/xml-elements-commands/delete-element-xmla.md)、 [DesignAggregations](../../../analysis-services/xmla/xml-elements-commands/designaggregations-element-xmla.md)、[ロック](../../../analysis-services/xmla/xml-elements-commands/lock-element-xmla.md)、 [NotifyTableChange](../../../analysis-services/xmla/xml-elements-commands/notifytablechange-element-xmla.md)、[プロセス](../../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md)、[サブスクライブ](../../../analysis-services/xmla/xml-elements-commands/subscribe-element-xmla.md)、[同期](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md)|  
|子要素|必須の Analysis Services Scripting Language (ASSL) 要素。 オブジェクトとその先祖の ID 要素をリストすることによって指定された (を除く、**サーバー**オブジェクトです)。たとえば、次**オブジェクト**要素が、パーティションを識別します。<br /><br /> `<Object>`<br /><br /> `<DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>`<br /><br /> `<CubeID>Adventure Works</CubeID>`<br /><br /> `<MeasureGroupID>Internet Sales</MeasureGroupID>`<br /><br /> `<PartitionID>Inernet_Sales_2001</PartitionID>`<br /><br /> `</Object>`|  
  
## <a name="remarks"></a>コメント  
 識別子の出現順序は重要ではありません。  
  
 **Alter**場合は、要素、Analysis Services のインスタンスを既定のオブジェクトとして使用、**オブジェクト**要素が指定されていません。  
  
## <a name="see-also"></a>参照
 [プロパティ&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
