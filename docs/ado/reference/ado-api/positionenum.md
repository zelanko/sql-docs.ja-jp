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
ms.openlocfilehash: 2d7b443e94f3bea5977aeaf953e84c66c826daeb
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2020
ms.locfileid: "88773171"
---
# <a name="positionenum"></a>PositionEnum
レコード [セット](./recordset-object-ado.md)内のレコードポインターの現在位置を指定します。  
  
|定数|値|説明|  
|--------------|-----------|-----------------|  
|**adPosBOF**|-2|現在のレコードポインターが BOF にある (つまり、 [bof](./bof-eof-properties-ado.md) プロパティが **True**である) ことを示します。|  
|**adPosEOF**|-3|現在のレコードポインターが EOF にあることを示します (つまり、 [eof](./bof-eof-properties-ado.md) プロパティが **True**であることを示します)。|  
|**adPosUnknown**|-1|**レコードセット**が空であるか、現在の位置が不明であるか、またはプロバイダーが[AbsolutePage](./absolutepage-property-ado.md)または[AbsolutePosition](./absoluteposition-property-ado.md)プロパティをサポートしていないことを示します。|  
  
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
        [AbsolutePage プロパティ (ADO)](./absolutepage-property-ado.md)  
    :::column-end:::
    :::column:::
        [AbsolutePosition プロパティ (ADO)](./absoluteposition-property-ado.md)  
    :::column-end:::
:::row-end:::