---
title: "ProactiveCachingTablesBinding データ型 (ASSL) |Microsoft ドキュメント"
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
- ProactiveCachingTablesBinding Data Type
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- ProactiveCachingTablesBinding data type
ms.assetid: f6b3f6fc-757c-4b1e-bb3a-d26482888d14
caps.latest.revision: 16
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: dd4bde472b49666db19ccd2e7dcc669e98dd2789
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="proactivecachingtablesbinding-data-type-assl"></a>ProactiveCachingTablesBinding データ型 (ASSL)
  情報を表す派生データ型を定義、 [ProactiveCaching](../../../analysis-services/scripting/objects/proactivecaching-element-assl.md)指定されたテーブルおよびビューをキャッシュの再構築を必要とするデータ ソース変更に関して要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<ProactiveCachingTablesBinding>  
   <!-- The following elements extend ProactiveCachingObjectNotificationBinding -->  
   <TableNotification>...</TableNotification>  
</ProactiveCachingTablesBinding>  
```  
  
## <a name="data-type-characteristics"></a>データ型の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|基本データ型|[ProactiveCachingObjectNotificationBinding](../../../analysis-services/scripting/data-type/proactivecachingobjectnotificationbinding-data-type-assl.md)|  
|派生データ型|なし|  
  
## <a name="data-type-relationships"></a>データ型のリレーションシップ  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|なし|  
|子要素|[TableNotification](../../../analysis-services/scripting/objects/tablenotification-element-assl.md)|  
|派生要素|なし|  
  
## <a name="remarks"></a>解説  
 詳細については、 **ProactiveCachingBinding**の継承階層のテーブルを含む型**ProactiveCachingBinding**型を参照してください[ProactiveCachingBinding データ型と #40 です。ASSL &#41;](../../../analysis-services/scripting/data-type/proactivecachingbinding-data-type-assl.md).  
  
 詳細については、**バインド**の Analysis Services スクリプト言語 (ASSL) オブジェクトのテーブルを含む、型、**バインド**型との継承階層**バインド**型を参照してください[バインドのデータ型 & #40 です。ASSL &#41;](../../../analysis-services/scripting/data-type/binding-data-type-assl.md).  
  
 ASSL でのデータ バインドの概要については、次を参照してください。[データ ソースとのバインド & #40 です。SSAS 多次元 &#41;](../../../analysis-services/multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.ProactiveCachingTablesBinding>します。  
  
## <a name="see-also"></a>参照  
 [Analysis Services スクリプト言語の XML データ型 & #40 です。ASSL &#41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  

