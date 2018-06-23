---
title: TableBinding データ型 (ASSL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
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
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: d0790fe5d8567c8ab23e3aaf39430d46675dcbdc
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36178975"
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
  
 計算される式は、修飾されたテーブル名 (Sales.Qty など) を使用する場合にも適用されます。 代わりにテーブルは、いくつかのクエリ「SELECT...」に置き換えられた場合にも適用します。 上記の FROM 句になります"FROM SELECT.As Sales" になります。  
  
 詳細については、`Binding`の Analysis Services スクリプト言語 (ASSL) オブジェクトの種類のテーブルを含む型`Binding`との継承の階層`Binding`型を参照してください[データ型のバインド&#40;ASSL&#41;](binding-data-type-assl.md).  
  
 ASSL でのデータ バインドの概要については、次を参照してください。[データ ソースとバインド&#40;SSAS 多次元&#41;](../../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md)です。  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.TableBinding>します。  
  
## <a name="see-also"></a>参照  
 [Binding データ型&#40;ASSL&#41;](binding-data-type-assl.md)   
 [データ ソースとバインド&#40;SSAS 多次元&#41;](../../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md)   
 [Analysis Services スクリプト言語の XML データ型&#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  