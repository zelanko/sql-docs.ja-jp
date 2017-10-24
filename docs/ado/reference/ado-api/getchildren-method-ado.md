---
title: "GetChildren メソッド (ADO) |Microsoft ドキュメント"
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
- _Record::raw_GetChildren
- _Record::GetChildren
helpviewer_keywords:
- GetChildren method [ADO]
ms.assetid: b3f09bac-4f66-49f6-aa5a-6fbb4fb28338
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 84f146c110b50cc3c73329dd72feb26f1ebf3858
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="getchildren-method-ado"></a>GetChildren メソッド (ADO)
返します、 [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)コレクションの子を表す行を持つ[レコード](../../../ado/reference/ado-api/record-object-ado.md)です。  
  
## <a name="syntax"></a>構文  
  
```  
  
Set recordset = record.GetChildren  
```  
  
## <a name="return-value"></a>戻り値  
 A **Recordset**オブジェクトの各行が、現在の子を表します**レコード**オブジェクト。 たとえばの子、**レコード**表しますディレクトリことが、ファイルとサブディレクトリの親ディレクトリ内に含まれます。  
  
## <a name="remarks"></a>解説  
 プロバイダーは、どのような列に返された存在によって決定**Recordset**です。 たとえば、ドキュメントのソース プロバイダー常にリソースを返す**Recordset**です。  
  
## <a name="applies-to"></a>適用対象  
  
|||  
|-|-|  
|[Record オブジェクト (ADO)](../../../ado/reference/ado-api/record-object-ado.md)|[レコード セット オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)|

