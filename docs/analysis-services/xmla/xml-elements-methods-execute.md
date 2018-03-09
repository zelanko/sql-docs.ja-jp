---
title: "Execute メソッド (XMLA) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: Execute Method
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- EXECUTE
- urn:schemas-microsoft-com:xml-analysis#
- http://schemas.microsoft.com/analysisservices/2003/engine#
- microsoft.xml.analysis.execute
- urn:schemas-microsoft-com:xml-analysis#Execute
helpviewer_keywords: Execute method
ms.assetid: 0fff5221-7164-4bbc-ab58-49cf04c52664
caps.latest.revision: "34"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 083137b2c739916210113373c709ab04c0e8f4e0
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="xml-elements---methods---execute"></a>XML 要素のメソッドを実行します。
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]For Analysis (XMLA) コマンドのインスタンスに XML を送信[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]です。 これには、サーバー上のデータの取得や更新など、データ転送に関連した要求が含まれます。  
  
 **Namespace** urn: スキーマ-microsoft-{urn:schemas-microsoft-com:xml-sql} の分析  
  
 **SOAP アクション**"urn: スキーマ-microsoft-{urn:schemas-microsoft-com:xml-sql}-分析: 実行"  
  
## <a name="syntax"></a>構文  
  
```  
  
<Execute>  
   <Command>...</Command>  
   <Properties>...</Properties>  
   <Parameters>...</Parameters>  
</Execute>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|Description|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|基数|0-1 : 省略可能な要素で、出現する場合は 1 回だけ出現します|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|なし|  
|子要素|[コマンド](../../analysis-services/xmla/xml-elements-properties/command-element-xmla.md)、[パラメーター](../../analysis-services/xmla/xml-elements-properties/parameters-element-xmla.md)、[プロパティ](../../analysis-services/xmla/xml-elements-properties/properties-element-xmla.md)|  
  
## <a name="remarks"></a>解説  
 **Execute**メソッドで提供される XMLA コマンドの実行、**コマンド**要素を XMLA のいずれかを使用して結果データを返します[行セット](../../analysis-services/xmla/xml-data-types/rowset-data-type-xmla.md)(表形式の結果のデータ型設定します) または XMLA [MDDataSet](../../analysis-services/xmla/xml-data-types/mddataset-data-type-xmla.md)データ型 (多次元結果を設定します)。  
  
## <a name="example"></a>例  
 次のサンプル コードの例に示します、 **Execute**多次元式 (MDX) の SELECT ステートメントを含むメソッドの呼び出しです。  
  
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
 [XML データ型 &#40;です。XMLA &#41;](../../analysis-services/xmla/xml-data-types/xml-data-types-xmla.md)   
 [方法 &#40; を検出します。XMLA &#41;](../../analysis-services/xmla/xml-elements-methods-discover.md)   
 [メソッドと #40 です。XMLA &#41;](../../analysis-services/xmla/xml-elements-methods.md)   
 [XML 要素 &#40;です。XMLA &#41;](http://msdn.microsoft.com/library/40ab2360-efb6-4ba6-bf23-e84964e51008)   
 [Analysis Services のスキーマ行セット](../../analysis-services/schema-rowsets/analysis-services-schema-rowsets.md)  
  
  
