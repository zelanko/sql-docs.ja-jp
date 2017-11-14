---
title: "NullProcessing 要素 (ASSL) |Microsoft ドキュメント"
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: scripting
ms.reviewer: 
ms.suite: sql
ms.custom: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- NullProcessing Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- NullProcessing
helpviewer_keywords:
- NullProcessing element
ms.assetid: 697be5c6-e9a6-4f74-9ff4-5f31400c2178
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: bc5c99e52f8868251d7d5b581bdefcea6e5d3097
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

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
|親要素|[DataItem](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 この要素の値は、次の表の一覧に示す文字列のいずれかに限定されています。  
  
|値|Description|  
|-----------|-----------------|  
|*保持します。*|NULL 値を保持します。<br /><br /> 注: この値は個別のカウント メジャーはサポートされていません。|  
|*[エラー]*|NULL キー エラーを発生します。 値[NullKeyNotAllowed](../../../analysis-services/scripting/properties/nullkeynotallowed-element-assl.md)インスタンスと、エラーの処理方法が決まります。<br /><br /> 注: この値は、メジャーはサポートされていません。|  
|*UnknownMember*|不明なメンバーを生成し、NULL 変換エラーを発生します。 値[NullKeyConvertedToUnknown](../../../analysis-services/scripting/properties/nullkeyconvertedtounknown-element-assl.md)インスタンスと、エラーの処理方法が決まります。<br /><br /> 注: この値はメジャーに関連付けられている列に対してはサポートされていません。|  
|*ZeroOrBlank*|数値データ アイテムの場合は NULL 値を 0 に変換し、文字列データ アイテムの場合は NULL 値を空白の文字列に変換します。<br /><br /> 注: この値は、以前のバージョンの互換性[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)][!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]です。|  
|*自動*|要素に適した既定の処理を使用します。<br /><br /> OLAP データ アイテムの場合は*ZeroOrBlank* <br /><br /> データ マイニング データ アイテムの場合は*UnknownMember* 。|  
  
 許可される値に対応する列挙**NullProcessing**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.NullProcessing>します。  
  
## <a name="see-also"></a>参照  
 [プロパティ & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

