---
title: UName 要素 (XMLA) |Microsoft Docs
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
- UName Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#UName
- urn:schemas-microsoft-com:xml-analysis#UName
- microsoft.xml.analysis.uname
helpviewer_keywords:
- UName element
ms.assetid: b4916d44-cf77-4d4c-b4e5-a0a98192d057
caps.latest.revision: 13
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: fa8df2d964db3c8131b9566e04b05c106638d62e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37185129"
---
# <a name="uname-element-xmla"></a>UName 要素 (XMLA)
  親の一意の名前を含む[HierarchyInfo](hierarchyinfo-element-xmla.md)または[メンバー](member-element-xmla.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<HierarchyInfo> <!-- or Member -->  
   ...  
   <UName>...</UName>  
   ...  
</HierarchyInfo>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String|  
|既定値|なし|  
|Cardinality|1-1 : 必須要素で、1 回だけ出現します|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[HierarchyInfo](hierarchyinfo-element-xmla.md)、[メンバー](member-element-xmla.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 `HierarchyInfo` 要素の場合、`UName` 要素は階層の一意のメンバー名を表すプロパティの名前を含みます。 値は、OLE DB for OLAP 仕様で軸行セットに関して定義される、MEMBER_UNIQUE_NAME プロパティと同等です。  
  
 `Member` 要素の場合、`UName` 要素は親要素 `Member` の一意の名前を含みます。  
  
## <a name="see-also"></a>参照  
 [プロパティ&#40;XMLA&#41;](xml-elements-properties.md)  
  
  
