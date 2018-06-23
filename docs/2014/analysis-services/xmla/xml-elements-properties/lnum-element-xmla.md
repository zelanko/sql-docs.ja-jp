---
title: LNum 要素 (XMLA) |Microsoft ドキュメント
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
- LNum Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.lnum
- urn:schemas-microsoft-com:xml-analysis#LNum
- http://schemas.microsoft.com/analysisservices/2003/engine#LNum
helpviewer_keywords:
- LNum element
ms.assetid: 7b9cc143-0c5e-4a8c-a288-8921bfcfd103
caps.latest.revision: 13
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: affdefb04b94d863faa9a9fb6a9eed8ea5b07606
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36070783"
---
# <a name="lnum-element-xmla"></a>LNum 要素 (XMLA)
  親のレベルの序数位置に関する情報を格納[HierarchyInfo](hierarchyinfo-element-xmla.md)または[メンバー](member-element-xmla.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<HierarchyInfo> <!-- or Member -->  
   ...  
   <LNum>...</LNum>  
   ...  
</HierarchyInfo>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|ssNoversion|  
|既定値|なし|  
|Cardinality|1-1 : 必須要素で、1 回だけ出現します|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[HierarchyInfo](hierarchyinfo-element-xmla.md)、[メンバー](member-element-xmla.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 `HierarchyInfo` 要素の場合、`LNum` 要素は階層のレベルを示す序数のプロパティの名前を含みます。 値は、OLE DB for OLAP 仕様で軸行セットに関して定義されている、LEVEL_NUMBER プロパティと同等です。  
  
 `Member` 、要素、`LNum`要素には、0 から始まる序数の位置、階層のルート レベルから親によって表されるメンバーにはが含まれています。[メンバー](member-element-xmla.md)要素。 値 0 は、階層のルート レベルを表します。  
  
## <a name="see-also"></a>参照  
 [プロパティ&#40;XMLA&#41;](xml-elements-properties.md)  
  
  