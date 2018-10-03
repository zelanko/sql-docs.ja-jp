---
title: ContextualNameRule 要素 (XML) |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
ms.assetid: eb567ef8-f412-4d34-837a-75e53b88b3ce
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 8843e2eafd32ac9e4bdb4cc7e4cbf97a04ea3f51
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48054212"
---
# <a name="contextualnamerule-element-xml"></a>ContextualNameRule 要素 (XML)
  属性の複合名を作成する最良の方法についてのヒントを提供します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<RelationshipEndVisualizationProperties>  
   ...  
   <ContextualNameRule>...</ContextualNameRule>  
   ...  
</RelationshipEndVisualizationProperties>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String (列挙型)|  
|既定値|-1|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけ出現します|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[RelationshipEndVisualizationProperties](../../scripting/data-type/relationshipendvisualizationproperties-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 この属性の明確な名前を作成する方法に関するヒントをクライアント アプリケーションに提供します。  
  
 `ContextualNameRule` 要素の値は、次の表の一覧に示す文字列のいずれかに限定されています。  
  
|値|説明|  
|-----------|-----------------|  
|*なし*|属性の名前を使用します。|  
|*コンテキスト*|入力リレーションシップの名前を使用します。|  
|*Merge*|アプリケーション言語のルールに従って、入力リレーションシップの名前と属性の名前を連結します。|  
  
  
