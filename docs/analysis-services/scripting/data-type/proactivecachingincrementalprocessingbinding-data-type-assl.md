---
title: ProactiveCachingIncrementalProcessingBinding データ型 (ASSL) |Microsoft ドキュメント
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 133d9cf8ca59b04453ca95ef3956c6c320f5b84b
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="proactivecachingincrementalprocessingbinding-data-type-assl"></a>ProactiveCachingIncrementalProcessingBinding データ型 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  バインドを表す派生データ型を定義、 [ProactiveCaching](../../../analysis-services/scripting/objects/proactivecaching-element-assl.md)キャッシュの再構築プロセスの状態に関する要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<ProactiveCachingIncrementalProcessingBinding>  
   <!-- The following elements extend ProactiveCachingBinding -->  
   <RefreshInterval>...</ RefreshInterval >  
   <IncrementalProcessingNotification>...</ IncrementalProcessingNotification >  
</ProactiveCachingIncrementalProcessingBinding>  
```  
  
## <a name="data-type-characteristics"></a>データ型の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|基本データ型|[ProactiveCachingBinding](../../../analysis-services/scripting/data-type/proactivecachingbinding-data-type-assl.md)|  
|派生データ型|なし|  
  
## <a name="data-type-relationships"></a>データ型のリレーションシップ  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|なし|  
|子要素|[IncrementalProcessingNotification](../../../analysis-services/scripting/objects/incrementalprocessingnotification-element-assl.md)、 [RefreshInterval](../../../analysis-services/scripting/properties/refreshinterval-element-assl.md)|  
|派生要素|なし|  
  
## <a name="remarks"></a>解説  
 詳細については、 **ProactiveCachingBinding**の継承階層のテーブルを含む型**ProactiveCachingBinding**型を参照してください[ProactiveCachingBinding データ型&#40;ASSL&#41;](../../../analysis-services/scripting/data-type/proactivecachingbinding-data-type-assl.md)です。  
  
 詳細については、**バインド**の Analysis Services スクリプト言語 (ASSL) オブジェクトのテーブルを含む、型、**バインド**型との継承階層**バインド**型を参照してください[データ型のバインド&#40;ASSL&#41;](../../../analysis-services/scripting/data-type/binding-data-type-assl.md)です。  
  
 ASSL でのデータ バインドの概要については、次を参照してください。[データ ソースとのバインド & #40 です。SSAS 多次元 & #41;](../../../analysis-services/multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.ProactiveCachingIncrementalProcessingBinding>します。  
  
## <a name="see-also"></a>参照  
 [Analysis Services スクリプト言語の XML データ型 & #40 です。ASSL & #41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
