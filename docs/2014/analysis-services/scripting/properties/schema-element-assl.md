---
title: スキーマ要素 (ASSL) |Microsoft ドキュメント
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
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 130d1363a007fb51db3bc7b39efcae4d9140c368
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36085767"
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
  
  