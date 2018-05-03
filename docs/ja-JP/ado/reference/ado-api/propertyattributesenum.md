---
title: PropertyAttributesEnum |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- PropertyAttributesEnum
helpviewer_keywords:
- PropertyAttributesEnum enumeration [ADO]
ms.assetid: 96a01955-a6b4-4cbf-9c73-52bcd1e9fb25
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 019c344caa5ecbf4daee2092d880e95ca612072c
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="propertyattributesenum"></a>PropertyAttributesEnum
属性を指定、[プロパティ](../../../ado/reference/ado-api/property-object-ado.md)オブジェクト。  
  
|定数|値|Description|  
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
