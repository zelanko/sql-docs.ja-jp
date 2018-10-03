---
title: ProactiveCachingQueryBinding データ型 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- ProactiveCachingQueryBinding Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- ProactiveCachingQueryBinding data type
ms.assetid: c1b06e50-9e68-40db-bdab-fc2cb3a8ff64
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d7b9c4aea38bb66277467275d2cf89a04cc3144a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48087632"
---
# <a name="proactivecachingquerybinding-data-type-assl"></a>ProactiveCachingQueryBinding データ型 (ASSL)
  情報を表す派生データ型を定義、 [ProactiveCaching](../objects/proactivecaching-element-assl.md)テーブルおよびビュー、キャッシュの再構築を必要とする指定されたクエリの実行を介して識別されるデータ ソース変更に関して要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<ProactiveCachingQueryBinding>  
   <!-- The following elements extend ProactiveCachingBinding -->  
   <RefreshInterval>...</RefreshInterval>  
   <QueryNotification>...</QueryNotification>  
</ProactiveCachingQueryBinding>  
```  
  
## <a name="data-type-characteristics"></a>データ型の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|基本データ型|[ProactiveCachingBinding](binding-data-type-assl.md)|  
|派生データ型|なし|  
  
## <a name="data-type-relationships"></a>データ型のリレーションシップ  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|なし|  
|子要素|[QueryNotification](../objects/querynotification-element-assl.md)、 [RefreshInterval](../properties/refreshinterval-element-assl.md)|  
|派生要素|なし|  
  
## <a name="remarks"></a>コメント  
 詳細については、`ProactiveCachingBinding`の継承階層のテーブルを含む、型`ProactiveCachingBinding`型を参照してください[ProactiveCachingBinding データ型&#40;ASSL&#41;](binding-data-type-assl.md)します。  
  
 詳細については、`Binding`の Analysis Services スクリプト言語 (ASSL) オブジェクトのテーブルを含む、型、`Binding`型との継承階層`Binding`型を参照してください[データ型のバインド&#40;ASSL&#41;](binding-data-type-assl.md).  
  
 ASSL でのデータ バインドの概要については、次を参照してください。[データ ソースとバインド&#40;SSAS 多次元&#41;](../../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md)します。  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.ProactiveCachingQueryBinding>します。  
  
## <a name="see-also"></a>参照  
 [Analysis Services スクリプト言語の XML データ型&#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
