---
title: GetChildren メソッド (ADO) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Record::raw_GetChildren
- _Record::GetChildren
helpviewer_keywords:
- GetChildren method [ADO]
ms.assetid: b3f09bac-4f66-49f6-aa5a-6fbb4fb28338
author: rothja
ms.author: jroth
ms.openlocfilehash: 605fb2e2afbd73a8a5509102ae98f348aad90bcb
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2020
ms.locfileid: "82760068"
---
# <a name="getchildren-method-ado"></a>GetChildren メソッド (ADO)
コレクション[レコード](../../../ado/reference/ado-api/record-object-ado.md)の子を表す行を含む[レコードセット](../../../ado/reference/ado-api/recordset-object-ado.md)を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Set recordset = record.GetChildren  
```  
  
## <a name="return-value"></a>戻り値  
 各行が現在の**レコード**オブジェクトの子を表す**Recordset**オブジェクト。 たとえば、ディレクトリを表す**レコード**の子は、親ディレクトリに格納されているファイルおよびサブディレクトリになります。  
  
## <a name="remarks"></a>Remarks  
 プロバイダーは、返された**レコードセット**に存在する列を決定します。 たとえば、ドキュメントソースプロバイダーは常にリソース**レコードセット**を返します。  
  
## <a name="applies-to"></a>適用対象  
  
|||  
|-|-|  
|[Record オブジェクト (ADO)](../../../ado/reference/ado-api/record-object-ado.md)|[Recordset オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)|
