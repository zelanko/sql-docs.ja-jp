---
title: "TableNotification 要素 (ASSL) |Microsoft ドキュメント"
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
- TableNotification Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- TableNotification element
ms.assetid: 3afd075a-74f9-428c-b527-ee497cbe71e7
caps.latest.revision: 15
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: a1d225682b831caf1e988f79372f1fa34df22815
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="tablenotification-element-assl"></a>TableNotification 要素 (ASSL)
  情報が含まれています、 [ProactiveCaching](../../../analysis-services/scripting/objects/proactivecaching-element-assl.md)テーブルまたはビューが変更されているデータ ソース内の要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<TableNotifications>  
   <TableNotification>  
      <DbTableName>...</DbTableName>  
      <DbSchemaName>...</DbSchemaName>  
...</TableNotification>  
</TableNotifications>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|Cardinality|1-n : 必須要素で、複数回の出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[TableNotifications](../../../analysis-services/scripting/collections/tablenotifications-element-assl.md)|  
|子要素|[DbSchemaName](../../../analysis-services/scripting/properties/dbschemaname-element-assl.md)、 [DbTableName](../../../analysis-services/scripting/properties/dbtablename-element-assl.md)|  
  
## <a name="remarks"></a>解説  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.TableNotification>します。  
  
## <a name="see-also"></a>参照  
 [ProactiveCachingTablesBinding データ型 & #40 です。ASSL &#41;](../../../analysis-services/scripting/data-type/proactivecachingtablesbinding-data-type-assl.md)   
 [ProactiveCachingObjectNotificationBinding データ型 & #40 です。ASSL &#41;](../../../analysis-services/scripting/data-type/proactivecachingobjectnotificationbinding-data-type-assl.md)   
 [ProactiveCachingBinding データ型 & #40 です。ASSL &#41;](../../../analysis-services/scripting/data-type/proactivecachingbinding-data-type-assl.md)   
 [オブジェクト & #40 です。ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  

