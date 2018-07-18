---
title: DataSourcePermissions 要素 (ASSL) |Microsoft Docs
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
- DataSourcePermissions Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- DataSourcePermissions element
ms.assetid: 6e1cfbec-65b9-4942-a628-f7f7c891e35f
caps.latest.revision: 11
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 42f330e28ac9a8bd349660550cee84df075121f5
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37321182"
---
# <a name="datasourcepermissions-element-assl"></a>DataSourcePermissions 要素 (ASSL)
  コレクションを格納[DataSourcePermission](../objects/datasourcepermission-element-assl.md)要素に関連付けられた、 [DataSource](../data-type/datasource-data-type-assl.md)データ型。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<DataSource>  
   ...  
   <DataSourcePermissions>  
      <DataSourcePermission>...</DataSourcePermission>  
   </DataSourcePermissions>  
   ...  
</DataSource>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[DataSource](../data-type/datasource-data-type-assl.md)|  
|子要素|[DataSourcePermission](../objects/datasourcepermission-element-assl.md)|  
  
## <a name="remarks"></a>コメント  
  
## <a name="see-also"></a>参照  
 [Permission データ型&#40;ASSL&#41;](../data-type/permission-data-type-assl.md)   
 [コレクション&#40;ASSL&#41;](collections-assl.md)  
  
  
