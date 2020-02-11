---
title: Clear メソッド (ADO) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Errors::raw_Clear
- Errors::Clear
helpviewer_keywords:
- Clear method [ADO]
ms.assetid: 0a61ba7a-20b8-426a-91a0-9040e7c5a98a
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 96bd13f130966b1830d07e49633842e4154b52b4
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67920065"
---
# <a name="clear-method-ado"></a>Clear メソッド (ADO)
[エラーコレクションから](../../../ado/reference/ado-api/errors-collection-ado.md)すべての[エラー](../../../ado/reference/ado-api/error-object.md)オブジェクトを削除します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Errors.Clear  
```  
  
## <a name="remarks"></a>解説  
 コレクションから既存の[エラー](../../../ado/reference/ado-api/error-object.md)オブジェクトをすべて削除するには、 [Errors](../../../ado/reference/ado-api/errors-collection-ado.md)コレクションに対して**Clear**メソッドを使用します。 エラーが発生すると、ADO によってエラーコレクションが自動的にクリア**され、** 新しいエラーに基づいて**エラー**オブジェクトに格納されます。  
  
 一部のプロパティおよびメソッドは、**エラーコレクションに****エラー**オブジェクトとして表示されるが、プログラムの実行を停止しない警告を返します。 [レコードセット](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクトの[Resync](../../../ado/reference/ado-api/resync-method.md)、 [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)、または[CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md)メソッドを呼び出す前に、[接続](../../../ado/reference/ado-api/connection-object-ado.md)オブジェクトの[Open](../../../ado/reference/ado-api/open-method-ado-connection.md)メソッド。または、**レコードセット**オブジェクトの[Filter](../../../ado/reference/ado-api/filter-property.md)プロパティを設定し、 **Errors**コレクションに対して**Clear**メソッドを呼び出します。 これにより、 **Errors**コレクションの[Count](../../../ado/reference/ado-api/count-property-ado.md)プロパティを読み取って、返された警告をテストできます。  
  
## <a name="applies-to"></a>適用対象  
 [Errors コレクション (ADO)](../../../ado/reference/ado-api/errors-collection-ado.md)  
  
## <a name="see-also"></a>参照  
 [Execute、Requery、および Clear メソッドの例 (VB)](../../../ado/reference/ado-api/execute-requery-and-clear-methods-example-vb.md)   
 [Execute、Requery、および Clear メソッドの例 (VBScript)](../../../ado/reference/ado-api/execute-requery-and-clear-methods-example-vbscript.md)   
 [Execute、Requery、および Clear メソッドの例 (VC + +)](../../../ado/reference/ado-api/execute-requery-and-clear-methods-example-vc.md)   
 [CancelBatch メソッド (ADO)](../../../ado/reference/ado-api/cancelbatch-method-ado.md)   
 [Delete メソッド (ADO Fields コレクション)](../../../ado/reference/ado-api/delete-method-ado-fields-collection.md)   
 [Delete メソッド (ADO Parameters コレクション)](../../../ado/reference/ado-api/delete-method-ado-parameters-collection.md)   
 [Delete メソッド (ADO Recordset)](../../../ado/reference/ado-api/delete-method-ado-recordset.md)   
 [Filter プロパティ](../../../ado/reference/ado-api/filter-property.md)   
 [Resync メソッド](../../../ado/reference/ado-api/resync-method.md)   
 [UpdateBatch メソッド](../../../ado/reference/ado-api/updatebatch-method.md)
