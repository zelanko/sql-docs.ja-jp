---
title: "PropertyAttributesEnum |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- PropertyAttributesEnum
helpviewer_keywords:
- PropertyAttributesEnum enumeration [ADO]
ms.assetid: 96a01955-a6b4-4cbf-9c73-52bcd1e9fb25
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 57c232c27dc538cbbdc8203855a27ee2ff56b7f8
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="propertyattributesenum"></a>PropertyAttributesEnum
属性を指定、[プロパティ](../../../ado/reference/ado-api/property-object-ado.md)オブジェクト。  
  
|定数|[値]|Description|  
|--------------|-----------|-----------------|  
|**adPropNotSupported**|0|プロパティがプロバイダーによってサポートされていないことを示します。|  
|**adPropRequired**|1|データ ソースが初期化される前にユーザーにこのプロパティの値を指定することを示します。|  
|**adPropOptional**|2|ユーザーがデータ ソースが初期化される前に、このプロパティの値を指定する必要がないことを示します。|  
|**adPropRead**|512|ユーザーが、プロパティを読み取ることができることを示します。|  
|**adPropWrite**|1024|ユーザーが、プロパティを設定できますを示します。|  
  
## <a name="adowfc-equivalent"></a>該当するショートカットは ADO/WFC  
 パッケージ: **com.ms.wfc.data**  
  
|定数|  
|--------------|  
|AdoEnums.PropertyAttributes.NOTSUPPORTED|  
|AdoEnums.PropertyAttributes.REQUIRED|  
|AdoEnums.PropertyAttributes.OPTIONAL|  
|AdoEnums.PropertyAttributes.READ|  
|AdoEnums.PropertyAttributes.WRITE|  
  
## <a name="applies-to"></a>適用対象  
 [Attributes プロパティ (ADO)](../../../ado/reference/ado-api/attributes-property-ado.md)
