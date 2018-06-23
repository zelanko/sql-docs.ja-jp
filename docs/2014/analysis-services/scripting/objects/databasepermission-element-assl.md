---
title: DatabasePermission 要素 (ASSL) |Microsoft ドキュメント
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
- DatabasePermission Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- DatabasePermission
helpviewer_keywords:
- DatabasePermission element
ms.assetid: 6dcb9136-a40d-42e3-ad3b-b8ce8c7ca78c
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: e47203616cc76fa09c0fd0658e7dad8a89c90a9b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36085963"
---
# <a name="databasepermission-element-assl"></a>DatabasePermission 要素 (ASSL)
  既定のアクセス許可を定義、[データベース](database-element-assl.md)、特定の要素[ロール](role-element-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<DatabasePermissions>  
      <DatabasePermission xsi:type="Permission">  
      <!-- The following elements extend Permission -->  
      <Administer>...</Administer>  
...</DatabasePermission>  
</DatabasePermissions>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|[アクセス許可](../data-type/permission-data-type-assl.md)|  
|既定値|False|  
|Cardinality|0-n : 省略可能な要素で、出現する場合は複数回の出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[DatabasePermissions](../collections/databasepermissions-element-assl.md)|  
|子要素|[管理します。](../properties/administer-element-assl.md)|  
  
## <a name="remarks"></a>コメント  
 `DatabasePermission` オブジェクトはデータベースに所有されているロールに対してのみ存在し、任意のロールに対して存在できる `DatabasePermission` オブジェクトは 1 つだけです。  
  
 DeploymentMode の値が 2 (Tabular Models) の場合、この要素には次の検証が適用されます。  
  
-   *管理*に属性の既定値が設定されている`False`ユーザーが管理者特権を有する場合を除く。 管理者権限を持つユーザーの属性値は `True` に設定されます。  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.DatabasePermission>します。  
  
## <a name="see-also"></a>参照  
 [Role 要素&#40;ASSL&#41;](role-element-assl.md)   
 [オブジェクト&#40;ASSL&#41;](objects-assl.md)  
  
  