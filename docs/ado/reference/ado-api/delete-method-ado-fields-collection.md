---
title: Delete メソッド (ADO Fields コレクション) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Fields20::Delete
- Fields20::raw_Delete
helpviewer_keywords:
- Delete method [ADO]
ms.assetid: 25bedc25-c51c-4cab-96ce-930b959965d9
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 9db49905b6548e5cb21cca976683c8b387017d32
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "67919132"
---
# <a name="delete-method-ado-fields-collection"></a>Delete メソッド (ADO Fields コレクション)
[フィールド](../../../ado/reference/ado-api/fields-collection-ado.md)コレクションからオブジェクトを削除します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Fields.Delete Field  
```  
  
#### <a name="parameters"></a>パラメーター  
 *フィールド*  
 削除する[フィールド](../../../ado/reference/ado-api/field-object.md)オブジェクトを指定する**バリアント**です。 このパラメーターには、**フィールド**オブジェクトの名前、または**フィールド**オブジェクト自体の序数位置を指定できます。  
  
## <a name="remarks"></a>Remarks  
 開いている[レコードセット](../../../ado/reference/ado-api/recordset-object-ado.md)で**Fields. Delete**メソッドを呼び出すと、実行時エラーが発生します。  
  
## <a name="applies-to"></a>適用対象  
 [Fields コレクション (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)  
  
## <a name="see-also"></a>参照  
 [Delete メソッド (ADO Parameters コレクション)](../../../ado/reference/ado-api/delete-method-ado-parameters-collection.md)   
 [Delete メソッド (ADO Recordset)](../../../ado/reference/ado-api/delete-method-ado-recordset.md)   
 [DeleteRecord メソッド (ADO)](../../../ado/reference/ado-api/deleterecord-method-ado.md)
