---
title: ProactiveCachingIncrementalProcessingBinding データ型 (ASSL) |Microsoft Docs
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
- ProactiveCachingIncrementalProcessingBinding Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- ProactiveCachingIncrementalProcessingBinding data type
ms.assetid: f49c0c96-4277-417b-9660-d77a4faebd00
caps.latest.revision: 15
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ad1107d1ad2e135e65b2ef4f05fd2e85d799123c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37247722"
---
# <a name="proactivecachingincrementalprocessingbinding-data-type-assl"></a>ProactiveCachingIncrementalProcessingBinding データ型 (ASSL)
  バインドを表す派生データ型を定義、 [ProactiveCaching](../objects/proactivecaching-element-assl.md)キャッシュの再構築プロセスの状態についての要素。  
  
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
|基本データ型|[ProactiveCachingBinding](binding-data-type-assl.md)|  
|派生データ型|なし|  
  
## <a name="data-type-relationships"></a>データ型のリレーションシップ  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|なし|  
|子要素|[IncrementalProcessingNotification](../objects/incrementalprocessingnotification-element-assl.md)、 [RefreshInterval](../properties/refreshinterval-element-assl.md)|  
|派生要素|なし|  
  
## <a name="remarks"></a>コメント  
 詳細については、`ProactiveCachingBinding`の継承階層のテーブルを含む、型`ProactiveCachingBinding`型を参照してください[ProactiveCachingBinding データ型&#40;ASSL&#41;](binding-data-type-assl.md)します。  
  
 詳細については、`Binding`の Analysis Services スクリプト言語 (ASSL) オブジェクトのテーブルを含む、型、`Binding`型との継承階層`Binding`型を参照してください[データ型のバインド&#40;ASSL&#41;](binding-data-type-assl.md).  
  
 ASSL でのデータ バインドの概要については、次を参照してください。[データ ソースとバインド&#40;SSAS 多次元&#41;](../../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md)します。  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.ProactiveCachingIncrementalProcessingBinding>します。  
  
## <a name="see-also"></a>参照  
 [Analysis Services スクリプト言語の XML データ型&#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
