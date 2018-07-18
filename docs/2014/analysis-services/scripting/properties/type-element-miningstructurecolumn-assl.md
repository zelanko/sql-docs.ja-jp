---
title: Type 要素 (MiningStructureColumn) (ASSL) |Microsoft Docs
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
- Type Element (MiningStructureColumn)
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- TYPE
helpviewer_keywords:
- Type element
ms.assetid: ce999716-9487-4348-bc42-270a2026a452
caps.latest.revision: 34
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 30ce9327fb28e9f452e643ded604f2a8dd72a084
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37304242"
---
# <a name="type-element-miningstructurecolumn-assl"></a>Type 要素 (MiningStructureColumn) (ASSL)
  型を含む、 [MiningStructureColumn](../data-type/miningstructurecolumn-data-type-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<MiningStructureColumn>  
   ...  
   <Type>...</Type>  
   ...  
</MiningStructureColumn>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String (列挙型)|  
|既定値|なし|  
|Cardinality|1-1 : 必須要素で、1 回だけ出現します|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[MiningStructureColumn](../data-type/miningstructurecolumn-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 この要素の値は、次の表の一覧に示す文字列のいずれかに限定されています。  
  
|値|説明|  
|-----------|-----------------|  
|*Long*|64 ビットの符号付き整数です。 このデータ型は、[!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework の `Int64` データ型と、OLE DB の DBTYPE_I8 データ型にマップされます。|  
|*ブール値*|ブール値です。 このデータ型は、.NET Framework の `Boolean` データ型と、OLE DB の DBTYPE_BOOL データ型にマップされます。|  
|*テキスト*|Unicode 文字の NULL 終了ストリームです。 このデータ型は、.NET Framework の `String` データ型と、OLE DB の DBTYPE_WSTR データ型にマップされます。|  
|*Double 型*|範囲の倍精度浮動小数点数-1.79 e +308 ~ 1.79 e +308 します。 このデータ型は、.NET Framework の `Double` データ型と、OLE DB の DBTYPE_R8 データ型にマップされます。|  
|*日付*|倍精度浮動小数点数として保存される日付データ。 整数部分は 1899 年 12 月 30 日からの日数で、小数部分は日の端数です。 このデータ型は、.NET Framework の `DateTime` データ型と、OLE DB の DBTYPE_DATE データ型にマップされます。|  
|*Table*|入れ子になったテーブル。 このデータ型は、OLE DB の DBTYPE_HCHAPTER データ型にマップされます。 **注:** 、.NET Framework でのテーブル列が、同等の組み込みデータ型はありませんでサポートされる代わりに、`DataReader`クラス。|  
  
 許容された値に対応する列挙体`Type`分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.MiningStructureColumnTypes>します。  
  
 親に対応する要素`Type`分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.MiningStructureColumn>します。  
  
## <a name="see-also"></a>参照  
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  
