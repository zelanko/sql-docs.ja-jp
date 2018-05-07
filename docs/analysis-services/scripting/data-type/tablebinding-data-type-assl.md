---
title: TableBinding データ型 (ASSL) |Microsoft ドキュメント
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: aa4a9b1cd3551ec26c1f20341ec2d08ba106a203
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="tablebinding-data-type-assl"></a>TableBinding データ型 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  テーブルへのバインドを表す派生データ型を定義します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<TableBinding>  
   <!-- The following elements extend TabularBinding -->  
   <DataSourceID>...</DataSourceID>  
   <DbTableName>...</DbTableName>  
   <DbSchemaName>...</DbSchemaName>  
</TableBinding>  
```  
  
## <a name="data-type-characteristics"></a>データ型の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|基本データ型|[TabularBinding](../../../analysis-services/scripting/data-type/tabularbinding-data-type-assl.md)|  
|派生データ型|なし|  
  
## <a name="data-type-relationships"></a>データ型のリレーションシップ  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|なし|  
|子要素|[DataSourceID](../../../analysis-services/scripting/properties/datasourceid-element-assl.md)、 [DbSchemaName](../../../analysis-services/scripting/properties/dbschemaname-element-assl.md)、 [DbTableName](../../../analysis-services/scripting/properties/dbtablename-element-assl.md)|  
|派生要素|参照してください[バインド](../../../analysis-services/scripting/data-type/binding-data-type-assl.md)|  
  
## <a name="remarks"></a>解説  
 一部のデータ ソースでは、サブセレクトを使用してフィルター式で他のテーブルを参照すると、パフォーマンスが影響を受ける場合があります。 ただし、設計者はデータ ソース ビューで名前付きクエリを定義し、それを参照することによって、SQL 式を完全に制御できます。  
  
 パーティションのバインドを定義する方法は、データ ソース ビューでのパーティション テーブルの使用とは関係がありません。  
  
 例として、既定のテーブルが "Sales" で、Date、Product ID、Qty、Price、および Amount の列 (データ ソース ビューで計算) を持つメジャー グループを検討します。 パーティション "Sales97" では、"Year(Sales.Date) = 97" というフィルターと共にテーブル "Sales97" を使用できます。  
  
 効果的なクエリは次のようになります。  
  
```  
SELECT Date, Product ID, Qty, Price, Qty * Price AS Amount   
   FROM Sales97 As Sales  
   WHERE Year(Sales.Date) = 97  
```  
  
 計算される式は、修飾されたテーブル名 (Sales.Qty など) を使用する場合にも適用されます。 代わりにテーブルは、いくつかのクエリ「SELECT...」に置き換えられた場合にも適用します。 上記の FROM 句になります"FROM SELECT.As Sales" になります。  
  
 詳細については、**バインド**の Analysis Services スクリプト言語 (ASSL) オブジェクトの種類のテーブルを含む型**バインド**との継承の階層**のバインド**型を参照してください[データ型のバインド&#40;ASSL&#41;](../../../analysis-services/scripting/data-type/binding-data-type-assl.md)です。  
  
 ASSL でのデータ バインドの概要については、次を参照してください。[データ ソースとのバインド & #40 です。SSAS 多次元 & #41;](../../../analysis-services/multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.TableBinding>します。  
  
## <a name="see-also"></a>参照  
 [バインディング データ型 & #40 です。ASSL & #41;](../../../analysis-services/scripting/data-type/binding-data-type-assl.md)   
 [データ ソースとバインド&#40;SSAS 多次元&#41;](../../../analysis-services/multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md)   
 [Analysis Services スクリプト言語の XML データ型 & #40 です。ASSL & #41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
