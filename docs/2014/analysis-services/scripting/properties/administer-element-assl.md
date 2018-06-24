---
title: Administer 要素 (ASSL) |Microsoft ドキュメント
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
- Administer Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Administer
helpviewer_keywords:
- Administer element
ms.assetid: 52924cd6-6176-47c8-ab17-4ee0e0ce42b1
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 099e5b9283acf8da6268e8b5abaaad73049ca076
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36074673"
---
# <a name="administer-element-assl"></a>Administer 要素 (ASSL)
  関連付けられたアクセス許可を管理する権限が含まれるかどうかを示します、[データベース](../objects/database-element-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<DatabasePermission>  
      ...  
      <Administer>...</Administer>  
   ...  
</DatabasePermission>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|ブール値|  
|既定値|False|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[DatabasePermission](../objects/databasepermission-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 `Administer` 要素は、ユーザーが特定のデータベースにのみ管理機能を実行できるかどうかを示します。 サーバー管理者ロールは、インスタンスに含まれているすべてのデータベースに対して管理機能を実行できます。  
  
 親に対応する要素`Administer`分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.DatabasePermission>します。  
  
## <a name="see-also"></a>参照  
 [Permission データ型&#40;ASSL&#41;](../data-type/permission-data-type-assl.md)   
 [Role 要素&#40;ASSL&#41;](../objects/role-element-assl.md)   
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  