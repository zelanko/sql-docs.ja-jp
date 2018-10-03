---
title: NullProcessing 要素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- NullProcessing Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- NullProcessing
helpviewer_keywords:
- NullProcessing element
ms.assetid: 697be5c6-e9a6-4f74-9ff4-5f31400c2178
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c7fa4c851e6818a3c9607fed0fdb8b9c499a63d0
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48139892"
---
# <a name="nullprocessing-element-assl"></a>NullProcessing Element (ASSL)
  NULL 値の処理方法を定義します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<DataItem>  
   ...  
   <NullProcessing>...</NullProcessing>  
   ...  
</DataItem>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String (列挙型)|  
|既定値|*自動*|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[DataItem](../data-type/dataitem-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 この要素の値は、次の表の一覧に示す文字列のいずれかに限定されています。  
  
|値|説明|  
|-----------|-----------------|  
|*保持します。*|NULL 値を保持します。 **注:** 個別のカウント メジャーは、この値はサポートされていません。|  
|*Error*|NULL キー エラーを発生します。 値[NullKeyNotAllowed](nullkeynotallowed-element-assl.md)インスタンスが、エラーに反応する方法を決定します。 **注:** メジャーにこの値がサポートされていません。|  
|*UnknownMember*|不明なメンバーを生成し、NULL 変換エラーを発生します。 値[NullKeyConvertedToUnknown](nullkeyconvertedtounknown-element-assl.md)インスタンスが、エラーに反応する方法を決定します。 **注:** メジャーに関連する列にこの値がサポートされていません。|  
|*ZeroOrBlank*|数値データ アイテムの場合は NULL 値を 0 に変換し、文字列データ アイテムの場合は NULL 値を空白の文字列に変換します。 **注:** この値は、以前のバージョンの互換性を提供します。 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)][!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]します。|  
|*自動*|要素に適した既定の処理を使用します。<br /><br /> -   *ZeroOrBlank* OLAP データ アイテムの。<br />-   *UnknownMember*データ マイニング データ アイテムです。|  
  
 許容された値に対応する列挙体`NullProcessing`分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.NullProcessing>します。  
  
## <a name="see-also"></a>参照  
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  
