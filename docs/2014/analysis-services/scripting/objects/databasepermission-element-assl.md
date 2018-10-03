---
title: DatabasePermission 要素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
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
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a904f12b86d6449c11f354a790503dc1bd93ffbe
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48106662"
---
# <a name="databasepermission-element-assl"></a>DatabasePermission 要素 (ASSL)
  既定の権限を定義、[データベース](database-element-assl.md)、特定の要素[ロール](role-element-assl.md)要素。  
  
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
  
-   *管理*属性の既定値に設定されます`False`ユーザーが管理者特権を持つ場合を除く。 管理者権限を持つユーザーの属性値は `True` に設定されます。  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.DatabasePermission>します。  
  
## <a name="see-also"></a>参照  
 [Role 要素&#40;ASSL&#41;](role-element-assl.md)   
 [オブジェクト&#40;ASSL&#41;](objects-assl.md)  
  
  
