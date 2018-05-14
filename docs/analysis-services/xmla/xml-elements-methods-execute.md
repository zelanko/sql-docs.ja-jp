---
title: Execute メソッド (XMLA) |Microsoft ドキュメント
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 56a48ffaf6d290d99503d7c8e1018f17e8d99a33
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="xml-elements---methods---execute"></a>XML 要素のメソッドを実行します。
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  For Analysis (XMLA) コマンドのインスタンスに XML を送信[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]です。 これには、サーバー上のデータの取得や更新など、データ転送に関連した要求が含まれます。  
  
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
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけ出現します|  
  
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
 [XML データ型 & #40 です。XMLA & #41;](../../analysis-services/xmla/xml-data-types/xml-data-types-xmla.md)   
 [Discover メソッド&#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-methods-discover.md)   
 [メソッド&#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-methods.md)   
 [XML 要素 & #40 です。XMLA & #41;](http://msdn.microsoft.com/library/40ab2360-efb6-4ba6-bf23-e84964e51008)   
 [Analysis Services のスキーマ行セット](../../analysis-services/schema-rowsets/analysis-services-schema-rowsets.md)  
  
  
