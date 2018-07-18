---
title: オブジェクトの要素 (XMLA) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Object Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Object
- urn:schemas-microsoft-com:xml-analysis#Object
- microsoft.xml.analysis.object
helpviewer_keywords:
- Object element
ms.assetid: 99470537-2c4a-4072-9613-940c41c12487
caps.latest.revision: 16
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 678838cd084fb8d3c7905f3e7363059fea28f541
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37229582"
---
# <a name="object-element-xmla"></a>Object 要素 (XMLA)
  親要素によって使用されるオブジェクト参照を含みます。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Alter> <!-- or any of the parent elements in the Element Relationships table -->  
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
|Cardinality|先祖または親: [Alter](../xml-elements-commands/create-element-xmla.md) &#124; 0-1: 省略可能な要素を一度だけ発生することができます。<br /><br /> 先祖または親: 他のすべて&#124;1-1: 必須要素で、1 回だけ出現します。|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[Alter](../xml-elements-commands/alter-element-xmla.md)、[バックアップ](../xml-elements-commands/backup-element-xmla.md)、 [ClearCache](../xml-elements-commands/clearcache-element-xmla.md)、[削除](../xml-elements-commands/delete-element-xmla.md)、 [DesignAggregations](../xml-elements-commands/designaggregations-element-xmla.md)、[ロック](../xml-elements-commands/lock-element-xmla.md)、 [NotifyTableChange](../xml-elements-commands/notifytablechange-element-xmla.md)、[プロセス](../xml-elements-commands/process-element-xmla.md)、[サブスクライブ](../xml-elements-commands/subscribe-element-xmla.md)、[同期](../xml-elements-commands/synchronize-element-xmla.md)|  
|子要素|必須の Analysis Services Scripting Language (ASSL) 要素。 オブジェクトとその先祖 (`Server` オブジェクトを除く) の ID 要素をリストすることによって指定します。たとえば、次の `Object` 要素はパーティションを識別します。<br /><br /> `<Object>`<br /><br /> `<DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>`<br /><br /> `<CubeID>Adventure Works</CubeID>`<br /><br /> `<MeasureGroupID>Internet Sales</MeasureGroupID>`<br /><br /> `<PartitionID>Inernet_Sales_2001</PartitionID>`<br /><br /> `</Object>`|  
  
## <a name="remarks"></a>コメント  
 識別子の出現順序は重要ではありません。  
  
 `Alter` 要素の場合、`Object` 要素が指定されなければ、[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] のインスタンスが既定のオブジェクトとして使用されます。  
  
## <a name="see-also"></a>参照  
 [プロパティ&#40;XMLA&#41;](xml-elements-properties.md)  
  
  
