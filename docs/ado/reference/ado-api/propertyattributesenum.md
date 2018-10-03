---
title: PropertyAttributesEnum |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- PropertyAttributesEnum
helpviewer_keywords:
- PropertyAttributesEnum enumeration [ADO]
ms.assetid: 96a01955-a6b4-4cbf-9c73-52bcd1e9fb25
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0bb38a73008d86144751ee324eb442bf711d65a5
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47835970"
---
# <a name="propertyattributesenum"></a>PropertyAttributesEnum
属性を指定します、[プロパティ](../../../ado/reference/ado-api/property-object-ado.md)オブジェクト。  
  
|定数|値|説明|  
|--------------|-----------|-----------------|  
|**adPropNotSupported**|0|プロパティがプロバイダーによってサポートされていないことを示します。|  
|**adPropRequired**|1|データ ソースが初期化される前に、ユーザーにこのプロパティの値を指定する必要がありますを示します。|  
|**adPropOptional**|2|ユーザーがデータ ソースが初期化される前に、このプロパティの値を指定する必要がないことを示します。|  
|**adPropRead**|512|ユーザーが、プロパティを読み取ることを示します。|  
|**adPropWrite**|1024|ユーザーが、プロパティを設定できることを示します。|  
  
## <a name="adowfc-equivalent"></a>ADO と WFC と同等  
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
