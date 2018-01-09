---
title: "スキーマ要素 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: Schema Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: Schema
helpviewer_keywords: Schema element
ms.assetid: 4b6375fb-7ad8-4d5f-88b1-abd3da2654db
caps.latest.revision: "34"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: f5359475a30fbd0f7caf65eab589b7e64ce3a588
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="schema-element-assl"></a>Schema 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]データ ソース ビューのスキーマが含まれています。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<DataSourceView>  
   ...  
   <Schema>...</Schema>  
   ...  
</DataSourceView>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|Description|  
|--------------------|-----------------|  
|データ型と長さ|スキーマ|  
|既定値|なし|  
|基数|1-1 : 必須要素で、1 回だけ出現します|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[DataSourceView](../../../analysis-services/scripting/objects/datasourceview-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 **スキーマ**のデータセットの XML スキーマ定義 (XSD) 言語形式を使用して表される、[!INCLUDE[msCoName](../../../includes/msconame-md.md)]データセットおよびその他のデータの定義におけるこの使用方法に固有の拡張することで、.NET Framework言語 (DDL)。 データセットは、XSD からリレーショナル スキーマへの柔軟なマッピングを定義しますが、より正規の形式で XSD を返します。 データ ソースでは、この正規の形式だけが有効です。  
  
 親に対応する要素**スキーマ**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.DataSourceView>します。  
  
## <a name="see-also"></a>参照  
 [プロパティ &#40;です。ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
