---
title: RecordCreateOptionsEnum |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- RecordCreateOptionsEnum
helpviewer_keywords:
- RecordCreateOptionsEnum enumeration [ADO]
ms.assetid: 6d746670-0850-4065-9cd4-168dea1d3ea9
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3109e7e7116fac22e007c65167bb718edf2b29b7
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="recordcreateoptionsenum"></a>RecordCreateOptionsEnum
指定します、既存かどうか**レコード**開くか、新しいにする必要があります**レコード**用に作成された、[レコード](../../../ado/reference/ado-api/record-object-ado.md)オブジェクト[開く](../../../ado/reference/ado-api/open-method-ado-record.md)メソッドです。 値は、AND 演算子と組み合わせることができます。  
  
|定数|値|Description|  
|--------------|-----------|-----------------|  
|**adCreateCollection**|0x2000|新たに作成**レコード**によって指定されたノードに*ソース*既存を開く代わりに、パラメーター**レコード**です。 ソースを指している場合、既存のノードでは、実行時エラーが発生し、しない限り、 **adCreateCollection**と組み合わせる**adOpenIfExists**または**adCreateOverwrite**です。|  
|**adCreateNonCollection**|0|新たに作成**レコード**型の[adSimpleRecord](../../../ado/reference/ado-api/recordtypeenum.md)です。|  
|**adCreateOverwrite**|0x4000000|作成フラグを変更**adCreateCollection**、 **adCreateNonCollection**、および**adCreateStructDoc**です。 ときに元の URL は、既存のノードを指している場合は、この値は、作成フラグの値のいずれかで使用またはまたは**レコード**、既存の**レコード**が上書きされるため、新しい場所に作成されます。 この値と組み合わせて使用することはできません**adOpenIfExists**です。|  
|**adCreateStructDoc**|0x80000000|新たに作成**レコード**型の[adStructDoc](../../../ado/reference/ado-api/recordtypeenum.md)、既存を開く代わりに**レコード**です。|  
|**adFailIfNotExists**|-1|既定値です。 場合、実行時エラーになります*ソース*存在しないノードをポイントします。|  
|**adOpenIfExists**|0x2000000|作成フラグを変更**adCreateCollection**、 **adCreateNonCollection**、および**adCreateStructDoc**です。 ときに元の URL は、既存のノードを指している場合は、この値は、作成フラグの値のいずれかで使用またはまたは**レコード**オブジェクト、プロバイダーは、既存を開く必要があります、**レコード**新たに作成するのではなく1 つです。 この値と組み合わせて使用することはできません**adCreateOverwrite**です。|  
  
## <a name="adowfc-equivalent"></a>該当するショートカットは ADO/WFC  
 これらの定数には、対応する ADO/WFC はありません。  
  
## <a name="applies-to"></a>適用対象  
 [Open メソッド (ADO Record)](../../../ado/reference/ado-api/open-method-ado-record.md)
