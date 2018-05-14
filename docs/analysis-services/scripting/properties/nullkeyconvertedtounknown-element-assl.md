---
title: NullKeyConvertedToUnknown 要素 (ASSL) |Microsoft ドキュメント
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 95f8a31e4600b73901d692ca7472759a681d9006
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="nullkeyconvertedtounknown-element-assl"></a>NullKeyConvertedToUnknown 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
|親要素|[ErrorConfiguration](../../../analysis-services/scripting/objects/errorconfiguration-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 Null 変換エラーと発生する null 値がキー列で発生したと解釈されます、**不明な**メンバー。 場合にのみ、ただし、このエラーが発生、 [NullProcessing](../../../analysis-services/scripting/properties/nullprocessing-element-assl.md)要素を[DataItem](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md)の先祖、 **ErrorConfiguration**に設定されている親要素*UnknownMember*です。  
  
 この要素の値は、次の表の一覧に示す文字列のいずれかに限定されています。  
  
|値|Description|  
|-----------|-----------------|  
|*IgnoreError*|処理は、エラーを無視し、続行します。|  
|*[Reportandcontinue]*|処理は、エラーを報告し、続行します。|  
|*ReportAndStop*|処理は、停止、エラーを報告します。|  
  
 許可される値に対応する列挙**NullKeyConvertedToUnknown**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.ErrorOption>します。  
  
## <a name="see-also"></a>参照  
 [ErrorConfiguration 要素 & #40 です。ASSL & #41;](../../../analysis-services/scripting/objects/errorconfiguration-element-assl.md)   
 [プロパティ & #40 です。ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
