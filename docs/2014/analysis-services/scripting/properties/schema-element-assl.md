---
title: Schema 要素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Schema Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Schema
helpviewer_keywords:
- Schema element
ms.assetid: 4b6375fb-7ad8-4d5f-88b1-abd3da2654db
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 5b8f9ab11698c2e0e73436abb3506ca38c45afe6
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48218802"
---
# <a name="schema-element-assl"></a>Schema 要素 (ASSL)
  データ ソース ビューのスキーマを格納します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<DataSourceView>  
   ...  
   <Schema>...</Schema>  
   ...  
</DataSourceView>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|スキーマ|  
|既定値|なし|  
|Cardinality|1-1 : 必須要素で、1 回だけ出現します|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[DataSourceView](../objects/datasourceview-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 `Schema` は、データ定義言語 (DDL) におけるこの使用方法に特有のデータセットなどの拡張機能と共に、[!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework でのデータセットの XML スキーマ定義 (XSD) 言語形式を使用して表されます。 データセットは、XSD からリレーショナル スキーマへの柔軟なマッピングを定義しますが、より正規の形式で XSD を返します。 データ ソースでは、この正規の形式だけが有効です。  
  
 親に対応する要素`Schema`分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.DataSourceView>します。  
  
## <a name="see-also"></a>参照  
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  
