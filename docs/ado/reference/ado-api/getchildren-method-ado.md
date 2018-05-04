---
title: GetChildren メソッド (ADO) |Microsoft ドキュメント
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
- _Record::raw_GetChildren
- _Record::GetChildren
helpviewer_keywords:
- GetChildren method [ADO]
ms.assetid: b3f09bac-4f66-49f6-aa5a-6fbb4fb28338
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9f385753f2e9dee3d99e4a6b41891ef69f4b70c0
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
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
|[Record オブジェクト (ADO)](../../../ado/reference/ado-api/record-object-ado.md)|[Recordset オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)|
