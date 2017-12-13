---
title: "OlapDataSource データ型 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/03/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: OlapDataSource Data Type
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: OlapDataSource
helpviewer_keywords: OlapDataSource data type
ms.assetid: cfe8937c-5f73-4773-a1e8-5e3310691966
caps.latest.revision: "34"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 2757d17355c8e35144c50b8ae6d552ce5b304665
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="olapdatasource-data-type-assl"></a>OlapDataSource データ型 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]マルチ ディメンションを表す派生データ型を定義[データソース](../../../analysis-services/scripting/objects/datasource-element-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<OlapDataSource>  
   <!-- Child elements are only those inherited from DataSource -->  
</OlapDataSource>  
```  
  
## <a name="data-type-characteristics"></a>データ型の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|基本データ型|[データ ソース](../../../analysis-services/scripting/data-type/datasource-data-type-assl.md)|  
|派生データ型|なし|  
  
## <a name="data-type-relationships"></a>データ型のリレーションシップ  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|なし|  
|子要素|なし|  
|派生要素|[DataSource](../../../analysis-services/scripting/objects/datasource-element-assl.md) ([DataSources](../../../analysis-services/scripting/collections/datasources-element-assl.md)のコレクション[データベース](../../../analysis-services/scripting/objects/database-element-assl.md))|  
  
## <a name="remarks"></a>解説  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.OlapDataSource>します。  
  
## <a name="see-also"></a>参照  
 [Analysis Services スクリプト言語の XML データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
