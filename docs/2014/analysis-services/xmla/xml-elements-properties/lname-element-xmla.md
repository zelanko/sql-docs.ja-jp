---
title: LName 要素 (XMLA) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- LName Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#LName
- http://schemas.microsoft.com/analysisservices/2003/engine#LName
- microsoft.xml.analysis.lname
helpviewer_keywords:
- LName element
ms.assetid: 2c8c2fa9-cb2d-44ea-b253-5e6ff61f1b66
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ba25e2c379c4049e34e7586e0574332720403c9e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48168382"
---
# <a name="lname-element-xmla"></a>LName 要素 (XMLA)
  親の一意のレベル名に関する情報を格納[HierarchyInfo](hierarchyinfo-element-xmla.md)または[メンバー](member-element-xmla.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<HierarchyInfo> <!-- or Member -->  
   ...  
   <LName>...</LName>  
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
 `HierarchyInfo` 要素の場合、この要素は階層の一意のレベル名を表すプロパティの名前を含みます。 値は、OLE DB for OLAP 仕様で軸行セットに関して定義される LEVEL_UNIQUE_NAME プロパティと同等です。  
  
 `Member` 要素の場合、この要素は、親要素 `Member` によって表されるメンバーを含む階層内での、レベルの一意の名前を含みます。  
  
## <a name="see-also"></a>参照  
 [プロパティ&#40;XMLA&#41;](xml-elements-properties.md)  
  
  
