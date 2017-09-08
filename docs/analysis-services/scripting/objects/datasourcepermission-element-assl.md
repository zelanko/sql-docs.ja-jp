---
title: "DataSourcePermission 要素 (ASSL) |Microsoft ドキュメント"
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
- DataSourcePermission Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- DataSourcePermission element
ms.assetid: 6dc6fb13-034e-479a-902e-27f3fb78c33f
caps.latest.revision: 14
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: fd41a100589e86a889698253bbb5f256b3bc788b
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="datasourcepermission-element-assl"></a>DataSourcePermission 要素 (ASSL)
  既定のアクセス許可を定義、[データソース](../../../analysis-services/scripting/data-type/datasource-data-type-assl.md)、特定のデータ型[ロール](../../../analysis-services/scripting/objects/role-element-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<DataSourcePermissions>  
   <DataSourcePermission xsi:type="Permission">  
      <!-- No child elements other than those from Permission are defined -->  
...</DataSourcePermission>  
</DataSourcePermissions>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|[アクセス許可](../../../analysis-services/scripting/data-type/permission-data-type-assl.md)|  
|既定値|なし|  
|Cardinality|0-n : 省略可能な要素で、出現する場合は 1 回または複数回の出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[DataSourcePermissions](../../../analysis-services/scripting/collections/datasourcepermissions-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 **DataSourcePermission** オブジェクトはデータベースに所有されているロールに対してのみ存在し、任意のロールに対して存在できる **DataSourcePermission** オブジェクトは 1 つだけです。  
  
## <a name="see-also"></a>参照  
 [Role 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/objects/role-element-assl.md)   
 [オブジェクト & #40 です。ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
