---
title: "NullKeyConvertedToUnknown 要素 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- NullKeyConvertedToUnknown Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- NullKeyConvertedToUnknown
helpviewer_keywords:
- NullKeyConvertedToUnknown element
ms.assetid: 1a6cde33-01ba-4095-b464-16d1ad3c6905
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 77c93a56563f621d357943348cf436846f213068
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

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
 [ErrorConfiguration 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/objects/errorconfiguration-element-assl.md)   
 [プロパティ & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

