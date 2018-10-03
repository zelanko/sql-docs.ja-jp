---
title: TableBinding データ型 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- TableBinding Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- TableBinding
helpviewer_keywords:
- TableBinding data type
ms.assetid: 3195dca4-82bf-46b7-a31f-5383586e3573
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ab697a42fa489152801a98fb9791fcd657bc5762
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48059521"
---
# <a name="tablebinding-data-type-assl"></a>TableBinding データ型 (ASSL)
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
|基本データ型|[TabularBinding](binding-data-type-assl.md)|  
|派生データ型|なし|  
  
## <a name="data-type-relationships"></a>データ型のリレーションシップ  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|なし|  
|子要素|[DataSourceID](../properties/id-element-assl.md)、 [DbSchemaName](../properties/name-element-assl.md)、 [DbTableName](../properties/dbtablename-element-assl.md)|  
|派生要素|参照してください[バインド](binding-data-type-assl.md)|  
  
## <a name="remarks"></a>コメント  
 一部のデータ ソースでは、サブセレクトを使用してフィルター式で他のテーブルを参照すると、パフォーマンスが影響を受ける場合があります。 ただし、設計者はデータ ソース ビューで名前付きクエリを定義し、それを参照することによって、SQL 式を完全に制御できます。  
  
 パーティションのバインドを定義する方法は、データ ソース ビューでのパーティション テーブルの使用とは関係がありません。  
  
 例として、既定のテーブルが "Sales" で、Date、Product ID、Qty、Price、および Amount の列 (データ ソース ビューで計算) を持つメジャー グループを検討します。 パーティション "Sales97" では、"Year(Sales.Date) = 97" というフィルターと共にテーブル "Sales97" を使用できます。  
  
 効果的なクエリは次のようになります。  
  
```  
SELECT Date, Product ID, Qty, Price, Qty * Price AS Amount   
   FROM Sales97 As Sales  
   WHERE Year(Sales.Date) = 97  
```  
  
 計算される式は、修飾されたテーブル名 (Sales.Qty など) を使用する場合にも適用されます。 これは、テーブルが "SELECT..." で始まるクエリに置換される場合にも適用されます。上の例の FROM 句は、"FROM SELECT ...As Sales" になります。  
  
 詳細については、`Binding`型、型の Analysis Services スクリプト言語 (ASSL) オブジェクトのテーブルを含む`Binding`の継承階層し`Binding`型を参照してください[データ型のバインド&#40;ASSL&#41;](binding-data-type-assl.md).  
  
 ASSL でのデータ バインドの概要については、次を参照してください。[データ ソースとバインド&#40;SSAS 多次元&#41;](../../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md)します。  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.TableBinding>します。  
  
## <a name="see-also"></a>参照  
 [Binding データ型&#40;ASSL&#41;](binding-data-type-assl.md)   
 [データ ソースとバインド&#40;SSAS 多次元&#41;](../../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md)   
 [Analysis Services スクリプト言語の XML データ型&#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
