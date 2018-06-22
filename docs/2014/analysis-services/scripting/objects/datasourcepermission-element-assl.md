---
title: DataSourcePermission 要素 (ASSL) |Microsoft ドキュメント
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
- DataSourcePermission Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- DataSourcePermission element
ms.assetid: 6dc6fb13-034e-479a-902e-27f3fb78c33f
caps.latest.revision: 14
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 9ca326118ce782962b0100c310ddb308af91f21b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36083065"
---
# <a name="datasourcepermission-element-assl"></a>DataSourcePermission 要素 (ASSL)
  既定のアクセス許可を定義、[データソース](../data-type/datasource-data-type-assl.md)、特定のデータ型[ロール](role-element-assl.md)要素。  
  
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
|データ型と長さ|[アクセス許可](../data-type/permission-data-type-assl.md)|  
|既定値|なし|  
|Cardinality|0-n : 省略可能な要素で、出現する場合は 1 回または複数回の出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[DataSourcePermissions](../collections/datasourcepermissions-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 `DataSourcePermission` オブジェクトはデータベースに所有されているロールに対してのみ存在し、任意のロールに対して存在できる `DataSourcePermission` オブジェクトは 1 つだけです。  
  
## <a name="see-also"></a>参照  
 [Role 要素&#40;ASSL&#41;](role-element-assl.md)   
 [オブジェクト&#40;ASSL&#41;](objects-assl.md)  
  
  