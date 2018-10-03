---
title: Role 要素 (XMLA) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
ms.assetid: 2b851ad5-cc46-4a2e-8873-d8556faca809
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 40bd787702243bcd85adb05eeb241330e08b63af
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48080412"
---
# <a name="role-element--xmla"></a>Role 要素 (XMLA)
  親で使用される一対多リレーションシップの一方の端を識別する[RelationshipEnd](../../scripting/data-type/relationshipend-data-type-assl.md)します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<RelationshipEnd  
   ...  
   <Role>...</Role>  
   ...  
</RelationshipEnd>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String|  
|既定値|なし|  
|Cardinality|1: 必須要素で、1 回だけ出現可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[RelationshipEnd](../../scripting/data-type/relationshipend-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
  
