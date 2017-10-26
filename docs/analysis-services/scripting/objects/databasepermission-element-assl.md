---
title: "DatabasePermission 要素 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- DatabasePermission Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- DatabasePermission
helpviewer_keywords:
- DatabasePermission element
ms.assetid: 6dcb9136-a40d-42e3-ad3b-b8ce8c7ca78c
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b33711fc326cf8256cc9c641c047c90a1686505a
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="databasepermission-element-assl"></a>DatabasePermission 要素 (ASSL)
  既定のアクセス許可を定義、[データベース](../../../analysis-services/scripting/objects/database-element-assl.md)、特定の要素[ロール](../../../analysis-services/scripting/objects/role-element-assl.md)要素。  
  
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
|データ型と長さ|[アクセス許可](../../../analysis-services/scripting/data-type/permission-data-type-assl.md)|  
|既定値|False|  
|Cardinality|0-n : 省略可能な要素で、出現する場合は複数回の出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[DatabasePermissions](../../../analysis-services/scripting/collections/databasepermissions-element-assl.md)|  
|子要素|[管理します。](../../../analysis-services/scripting/properties/administer-element-assl.md)|  
  
## <a name="remarks"></a>解説  
 **DatabasePermission** オブジェクトはデータベースに所有されているロールに対してのみ存在し、任意のロールに対して存在できる **DatabasePermission** オブジェクトは 1 つだけです。  
  
 DeploymentMode の値が 2 (Tabular Models) の場合、この要素には次の検証が適用されます。  
  
-   *Administer* 属性の既定値は、ユーザーが管理者特権を持っている場合を除き、 **False**に設定されます。 管理者権限を持つユーザーの属性値は **True**に設定されます。  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.DatabasePermission>します。  
  
## <a name="see-also"></a>参照  
 [Role 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/objects/role-element-assl.md)   
 [オブジェクト & #40 です。ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  

