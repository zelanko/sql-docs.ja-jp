---
description: PositionEnum
title: PositionEnum |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- PositionEnum
helpviewer_keywords:
- PositionEnum enumeration
ms.assetid: e69af0a5-3405-4b72-9c6e-6b188ff746fd
author: rothja
ms.author: jroth
ms.openlocfilehash: 326fc4f1b9b77c8a4470fedc7d55f2d379aff6f3
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88442714"
---
# <a name="positionenum"></a>PositionEnum
レコード [セット](../../../ado/reference/ado-api/recordset-object-ado.md)内のレコードポインターの現在位置を指定します。  
  
|定数|値|説明|  
|--------------|-----------|-----------------|  
|**adPosBOF**|-2|現在のレコードポインターが BOF にある (つまり、 [bof](../../../ado/reference/ado-api/bof-eof-properties-ado.md) プロパティが **True**である) ことを示します。|  
|**adPosEOF**|-3|現在のレコードポインターが EOF にあることを示します (つまり、 [eof](../../../ado/reference/ado-api/bof-eof-properties-ado.md) プロパティが **True**であることを示します)。|  
|**adPosUnknown**|-1|**レコードセット**が空であるか、現在の位置が不明であるか、またはプロバイダーが[AbsolutePage](../../../ado/reference/ado-api/absolutepage-property-ado.md)または[AbsolutePosition](../../../ado/reference/ado-api/absoluteposition-property-ado.md)プロパティをサポートしていないことを示します。|  
  
## <a name="adowfc-equivalent"></a>同等の ADO/WFC  
 パッケージ: **com. ms. wfc. データ**  
  
|定数|  
|--------------|  
|AdoEnums|  
|AdoEnums|  
|AdoEnums。不明|  
  
## <a name="applies-to"></a>適用対象  

:::row:::
    :::column:::
        [AbsolutePage プロパティ (ADO)](../../../ado/reference/ado-api/absolutepage-property-ado.md)  
    :::column-end:::
    :::column:::
        [AbsolutePosition プロパティ (ADO)](../../../ado/reference/ado-api/absoluteposition-property-ado.md)  
    :::column-end:::
:::row-end:::
