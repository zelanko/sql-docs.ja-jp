---
title: MDDataSet データ型 (XMLA) |Microsoft ドキュメント
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
- MDDataSet Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#MDDataSet
- MDDataSet
- urn:schemas-microsoft-com:xml-analysis#MDDataSet
helpviewer_keywords:
- MDDataSet data type
ms.assetid: 1a7e0092-f9f0-4ae5-ba27-ad1d8ebe8cb9
caps.latest.revision: 27
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 098a123c28e4a449ad6425d1a74ff8355d074e08
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36072605"
---
# <a name="mddataset-data-type-xmla"></a>MDDataSet データ型 (XMLA)
  によって返される多次元データを表す派生データ型を定義、 [Execute](../xml-elements-methods-execute.md)メソッドです。  
  
 **Namespace** urn: スキーマ-microsoft-{urn:schemas-microsoft-com:xml-sql}-分析: mddataset  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<root xmlns="urn:schemas-microsoft-com:xml-analysis:rowset">  
   <!-- The following elements extend Resultset -->  
   <!-- Optional schema elements -->  
   <OlapInfo>...</OlapInfo>  
   <Axes>...</Axes>  
   <CellData>...</CellData>  
</root>  
```  
  
## <a name="data-type-characteristics"></a>データ型の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|基本データ型|[結果セット](resultset-data-type-xmla.md)|  
|派生データ型|なし|  
  
## <a name="data-type-relationships"></a>データ型のリレーションシップ  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|なし|  
|子要素|[軸](../xml-elements-properties/axes-element-xmla.md)、 [CellData](../xml-elements-properties/celldata-element-xmla.md)、 [OlapInfo](../xml-elements-properties/olapinfo-element-xmla.md)|  
|派生要素|なし|  
  
## <a name="remarks"></a>コメント  
 `MDDataSet` データ型は、OLAP データを XML で表すために必要な OLAP 指向の行セット (またはデータセット) を提供します。 この行セットの内容は、の値によって異なることができます、`Content`と`Format`で提供されるプロパティ、[プロパティ](../xml-elements-properties/properties-element-xmla.md)のコレクション、`Execute`メソッドです。 詳細については、`Content`と`Format`プロパティを参照してください[サポートされる XMLA プロパティ&#40;XMLA&#41;](../xml-elements-properties/propertylist-element-supported-xmla-properties.md)です。  
  
 OLE DB for OLAP データセットの構造に関する基本的な情報については、XML for Analysis 1.1 仕様の「OLE DB への MDDataSet データ型のマッピング」を参照してください。 `MDDataSet` データ型の XML スキーマ定義言語 (XSD) による詳しいサンプルについては、XML for Analysis 1.1 仕様の「Appendix D: MDDataSet Example」を参照してください。  
  
## <a name="see-also"></a>参照  
 [XML データ型&#40;XMLA&#41;](xml-data-types-xmla.md)  
  
  