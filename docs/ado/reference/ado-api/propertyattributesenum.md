---
title: "PropertyAttributesEnum |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- PropertyAttributesEnum
helpviewer_keywords:
- PropertyAttributesEnum enumeration [ADO]
ms.assetid: 96a01955-a6b4-4cbf-9c73-52bcd1e9fb25
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 6614f74546fab23a1e1ce453ac12c10082011a25
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

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
 [属性プロパティ (ADO)](../../../ado/reference/ado-api/attributes-property-ado.md)

