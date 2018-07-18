---
title: CellData 要素 (XMLA) |Microsoft Docs
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
- CellData Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- CellData
- http://schemas.microsoft.com/analysisservices/2003/engine#CellData
- urn:schemas-microsoft-com:xml-analysis#CellData
- microsoft.xml.analysis.celldata
helpviewer_keywords:
- CellData element
ms.assetid: 0ebfb5e1-a674-4b9b-bd8c-c529da105f61
caps.latest.revision: 27
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 370837c78fe1fa49396a5209dd94dd0e7cb4f69d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37330412"
---
# <a name="celldata-element-xmla"></a>CellData 要素 (XMLA)
  含まれるセルのデータを表すセル要素のコレクションを格納する[ルート](root-element-xmla.md)を使用する要素、 [MDDataSet](../xml-data-types/mddataset-data-type-xmla.md)データ型。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<root xmlns="urn:schemas-microsoft-com:xml-analysis:mddataset">  
   ...  
   <CellData>  
      <Cell>...</Cell>  
   </CellData>  
</root>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|Cardinality|0-n : 省略可能な要素で、出現する場合は複数回の出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[root](root-element-xmla.md)|  
|子要素|[たとえば、マトリックスでは、列ヘッダーに並べ替えボタンを追加してマトリックスにバインドされているデータセットの名前として、コンテナー スコープを指定します。](cell-element-mddataset-xmla.md)|  
  
## <a name="remarks"></a>コメント  
 親の root 要素の中では、`Axes` 要素の後に `CellData` 要素が続きます。これは、多次元データセットで返される各セルのセル プロパティ値を含む `Cell` 要素のコレクションです。  
  
## <a name="see-also"></a>参照  
 [プロパティ&#40;XMLA&#41;](xml-elements-properties.md)  
  
  
