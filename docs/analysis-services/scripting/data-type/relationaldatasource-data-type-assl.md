---
title: RelationalDataSource データ型 (ASSL) |Microsoft ドキュメント
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 9046573e26d7e0c53e5cce513fcfce43654af989
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="relationaldatasource-data-type-assl"></a>RelationalDataSource データ型 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  表す派生データ型を定義、[データソース](../../../analysis-services/scripting/objects/datasource-element-assl.md)要素は、リレーショナル データ ソースに基づきます。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<RelationalDataSource>  
   <!-- Child elements are only those inherited from DataSource -->  
</RelationalDataSource>  
```  
  
## <a name="data-type-characteristics"></a>データ型の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|基本データ型|[DataSource](../../../analysis-services/scripting/data-type/datasource-data-type-assl.md)|  
|派生データ型|なし|  
  
## <a name="data-type-relationships"></a>データ型のリレーションシップ  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|なし|  
|子要素|なし|  
|派生要素|[DataSource](../../../analysis-services/scripting/objects/datasource-element-assl.md) ([DataSources](../../../analysis-services/scripting/collections/datasources-element-assl.md)のコレクション[データベース](../../../analysis-services/scripting/objects/database-element-assl.md))|  
  
## <a name="remarks"></a>解説  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.RelationalDataSource>します。  
  
## <a name="see-also"></a>参照  
 [Analysis Services スクリプト言語の XML データ型 & #40 です。ASSL & #41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
