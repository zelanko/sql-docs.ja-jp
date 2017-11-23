---
title: "GetChildren メソッド (ADO) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- _Record::raw_GetChildren
- _Record::GetChildren
helpviewer_keywords: GetChildren method [ADO]
ms.assetid: b3f09bac-4f66-49f6-aa5a-6fbb4fb28338
caps.latest.revision: "12"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 46f9af9b4cb1b4648acc75389f7d75cccdc46b96
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
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
