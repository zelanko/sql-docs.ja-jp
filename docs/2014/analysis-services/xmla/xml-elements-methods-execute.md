---
title: Execute メソッド (XMLA) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Execute Method
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- EXECUTE
- urn:schemas-microsoft-com:xml-analysis#
- http://schemas.microsoft.com/analysisservices/2003/engine#
- microsoft.xml.analysis.execute
- urn:schemas-microsoft-com:xml-analysis#Execute
helpviewer_keywords:
- Execute method
ms.assetid: 0fff5221-7164-4bbc-ab58-49cf04c52664
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6d1c3e842c8f859802be1193ca615933877faa1b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48155685"
---
# <a name="execute-method-xmla"></a>Execute メソッド (XMLA)
  For Analysis (XMLA) コマンドのインスタンスに XML を送信します[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]します。 これには、サーバー上のデータの取得や更新など、データ転送に関連した要求が含まれます。  
  
 **Namespace** urn: スキーマ-microsoft-'http://www.w3.org/2001/xmlschema'-分析  
  
 **SOAP アクション**"urn: スキーマ-microsoft-'http://www.w3.org/2001/xmlschema'-分析: 実行"  
  
## <a name="syntax"></a>構文  
  
```  
  
<Execute>  
   <Command>...</Command>  
   <Properties>...</Properties>  
   <Parameters>...</Parameters>  
</Execute>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけ出現します|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|なし|  
|子要素|[Command](xml-elements-properties/command-element-xmla.md)、[Parameters](xml-elements-properties/parameters-element-xmla.md)、[Properties](xml-elements-properties/properties-element-xmla.md)|  
  
## <a name="remarks"></a>コメント  
 `Execute`メソッドが含まれる XMLA コマンドが実行される、`Command`要素を XMLA のいずれかを使用して結果データを返します[行セット](xml-data-types/rowset-data-type-xmla.md)(表形式の結果セット) のデータ型または XMLA [MDDataSet](xml-data-types/mddataset-data-type-xmla.md) (多次元結果を設定します) のデータ型。  
  
## <a name="example"></a>例  
 次のコード サンプルは、多次元式 (MDX) の SELECT ステートメントを含む `Execute` メソッド呼び出しの例です。  
  
```  
<Execute xmlns="urn:schemas-microsoft-com:xml-analysis">  
   <Command>  
      <Statement>  
         SELECT [Measures].MEMBERS ON COLUMNS FROM [Adventure Works]  
      </Statement>  
   </Command>  
   <Properties>  
      <PropertyList>  
         <DataSourceInfo>Provider=MSOLAP;Data Source=local;</DataSourceInfo>  
         <Catalog>Adventure Works DW Multidimensional 2012</Catalog>  
         <Format>Multidimensional</Format>  
         <AxisFormat>ClusterFormat</AxisFormat>  
      </PropertyList>  
   </Properties>  
</Execute>  
```  
  
## <a name="see-also"></a>参照  
 [XML データ型&#40;XMLA&#41;](xml-data-types/xml-data-types-xmla.md)   
 [Discover メソッド&#40;XMLA&#41;](xml-elements-methods-discover.md)   
 [メソッド&#40;XMLA&#41;](xml-elements-methods.md)   
 [XML 要素&#40;XMLA&#41;](../dev-guide/xml-elements-xmla.md)   
 [Analysis Services のスキーマ行セット](../schema-rowsets/analysis-services-schema-rowsets.md)  
  
  
