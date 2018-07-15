---
title: Type 要素 (Dimension) (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Type Element (Dimension)
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- TYPE
helpviewer_keywords:
- Type element
ms.assetid: 6a2798b1-26c7-49d8-b556-e681c69d9574
caps.latest.revision: 36
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c6afa3b273200630a4d36e0c4df679c58efb6bd5
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37283948"
---
# <a name="type-element-dimension-assl"></a>Type 要素 (Dimension) (ASSL)
  ディメンションのコンテンツに関する情報を提供します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Dimension>  
      ...  
   <Type>...</Type>  
   ...  
</Dimension>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String (列挙型)|  
|既定値|*正規表現*|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[Dimension](../objects/dimension-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 値によって`Type`、たとえば*アカウント*、特定の動作を決定します。  
  
 この要素の値は、次の表の一覧に示す文字列のいずれかに限定されています。  
  
|値|説明|  
|-----------|-----------------|  
|*正規表現*|ディメンションは標準ディメンションです。|  
|*[時刻]*|ディメンションは時間ディメンションです。 **注:** この値は、ディメンションが時間ディメンションに固有の機能をサポートしていることを示します。|  
|*Geography*|ディメンションに地域属性が含まれています。|  
|*組織*|ディメンションに組織属性が含まれています。|  
|*BillOfMaterials*|ディメンションに部品表属性が含まれています。|  
|*Accounts*|ディメンションに勘定科目関連の属性が含まれています。 **注:** この値は、ディメンションに勘定科目ディメンションに固有の機能がサポートしていることを示します。|  
|*顧客*|ディメンションに顧客関連の属性が含まれています。|  
|*製品*|ディメンションに製品関連の属性が含まれています。|  
|*シナリオ*|ディメンションにシナリオ関連の属性が含まれています。|  
|*定量的*|ディメンションに数量属性が含まれています。|  
|*Utility*|ディメンションにユーティリティ属性が含まれています。|  
|*通貨*|ディメンションに通貨属性が含まれています。|  
|*料金*|ディメンションに換算レート属性が含まれています。|  
|*Channel*|ディメンションにチャネル属性が含まれています。|  
|*プロモーション*|ディメンションにプロモーション関連の属性が含まれています。|  
  
 許容された値に対応する列挙体`Type`分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.DimensionType>します。  
  
 親に対応する要素`Type`分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.Dimension>します。  
  
## <a name="see-also"></a>参照  
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  
