---
description: PropertyAttributesEnum
title: Property属性 Enum |Microsoft Docs
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 823505aae912c64c2fd7d3375b3426cb6428bcdd
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2020
ms.locfileid: "88772871"
---
# <a name="propertyattributesenum"></a>PropertyAttributesEnum
[プロパティ](./property-object-ado.md)オブジェクトの属性を指定します。  
  
|定数|値|説明|  
|--------------|-----------|-----------------|  
|**adPropNotSupported**|0|プロパティがプロバイダーによってサポートされていないことを示します。|  
|**adPropRequired**|1|データソースが初期化される前に、ユーザーがこのプロパティの値を指定する必要があることを示します。|  
|**他の adpropop**|2|データソースが初期化される前に、ユーザーがこのプロパティの値を指定する必要がないことを示します。|  
|**adPropRead**|512|ユーザーがプロパティを読み取ることができることを示します。|  
|**adPropWrite**|1024|ユーザーがプロパティを設定できることを示します。|  
  
## <a name="adowfc-equivalent"></a>同等の ADO/WFC  
 パッケージ: **com. ms. wfc. データ**  
  
|定数|  
|--------------|  
|AdoEnums NOTSUPPORTED|  
|AdoEnums。必須|  
|AdoEnums。省略可能|  
|AdoEnums を参照してください。|  
|AdoEnums を作成します。|  
  
## <a name="applies-to"></a>適用対象  
 [Attributes プロパティ (ADO)](./attributes-property-ado.md)