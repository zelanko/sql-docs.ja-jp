---
title: NullKeyConvertedToUnknown 要素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- NullKeyConvertedToUnknown Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- NullKeyConvertedToUnknown
helpviewer_keywords:
- NullKeyConvertedToUnknown element
ms.assetid: 1a6cde33-01ba-4095-b464-16d1ad3c6905
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6aaf78e4081b0f2fe04bf9b4037639f5b86f5311
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48121722"
---
# <a name="nullkeyconvertedtounknown-element-assl"></a>NullKeyConvertedToUnknown 要素 (ASSL)
  NULL 変換エラーが発生した場合の動作を指定します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<ErrorConfiguration>  
   ...  
      <NullKeyConvertedToUnknown>...</NullKeyConvertedToUnknown>  
   ...  
</ErrorConfiguration>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String (列挙型)|  
|既定値|*IgnoreError*|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[ErrorConfiguration](../objects/errorconfiguration-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 NULL 変換エラーは、NULL 値がキー列で検出され、`Unknown` メンバーとして解釈された場合に発生します。 場合にのみ、ただし、このエラーが発生、 [NullProcessing](nullprocessing-element-assl.md)の要素、 [DataItem](../data-type/dataitem-data-type-assl.md)の先祖である、`ErrorConfiguration`に親要素が設定されている*UnknownMember*します。  
  
 この要素の値は、次の表の一覧に示す文字列のいずれかに限定されています。  
  
|値|説明|  
|-----------|-----------------|  
|*IgnoreError*|処理は、エラーを無視し、続行します。|  
|*ReportAndContinue*|処理は、エラーを報告し、続行します。|  
|*ReportAndStop*|処理は、停止、エラーを報告します。|  
  
 許容された値に対応する列挙体`NullKeyConvertedToUnknown`分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.ErrorOption>します。  
  
## <a name="see-also"></a>参照  
 [ErrorConfiguration 要素&#40;ASSL&#41;](../objects/errorconfiguration-element-assl.md)   
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  
