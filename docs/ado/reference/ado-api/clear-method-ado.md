---
title: "Clear メソッド (ADO) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Errors::raw_Clear
- Errors::Clear
helpviewer_keywords:
- Clear method [ADO]
ms.assetid: 0a61ba7a-20b8-426a-91a0-9040e7c5a98a
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 831ec9b295ca4e3d81707cfc2c1cc14169d1527c
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="clear-method-ado"></a>Clear メソッド (ADO)
すべてを削除、[エラー](../../../ado/reference/ado-api/error-object.md)オブジェクトから、[エラー](../../../ado/reference/ado-api/errors-collection-ado.md)コレクション。  
  
## <a name="syntax"></a>構文  
  
```  
  
Errors.Clear  
```  
  
## <a name="remarks"></a>解説  
 使用して、**クリア**メソッドを[エラー](../../../ado/reference/ado-api/errors-collection-ado.md)既存のすべてを削除するコレクション[エラー](../../../ado/reference/ado-api/error-object.md)コレクションからオブジェクト。 エラーが発生すると、ADO は自動的にオフ、**エラー**コレクションを格納および**エラー**オブジェクトは新しいエラーをベースにします。  
  
 プロパティとメソッドの一部として表示される警告を返します**エラー**内のオブジェクト、**エラー**コレクションが、プログラムの実行を停止しないでください。 呼び出す前に、[再同期](../../../ado/reference/ado-api/resync-method.md)、 [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)、または[CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md)メソッドを[Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクト;、 [を開く](../../../ado/reference/ado-api/open-method-ado-connection.md)メソッドを[接続](../../../ado/reference/ado-api/connection-object-ado.md); オブジェクトまたは設定、[フィルター](../../../ado/reference/ado-api/filter-property.md)プロパティを**Recordset**オブジェクトを呼び出す、 **をオフに**メソッドを**エラー**コレクション。 読み取ることができるように、[カウント](../../../ado/reference/ado-api/count-property-ado.md)のプロパティ、**エラー**コレクションをテストするには、警告が返されました。  
  
## <a name="applies-to"></a>適用対象  
 [Errors コレクション (ADO)](../../../ado/reference/ado-api/errors-collection-ado.md)  
  
## <a name="see-also"></a>参照  
 [実行、クエリを再実行、およびメソッドの例 (VB) をオフに](../../../ado/reference/ado-api/execute-requery-and-clear-methods-example-vb.md)   
 [実行、クエリを再実行、およびメソッドの例 (VBScript) をオフに](../../../ado/reference/ado-api/execute-requery-and-clear-methods-example-vbscript.md)   
 [実行、クエリを再実行、およびメソッドの例 (vc++) をオフに](../../../ado/reference/ado-api/execute-requery-and-clear-methods-example-vc.md)   
 [CancelBatch メソッド (ADO)](../../../ado/reference/ado-api/cancelbatch-method-ado.md)   
 [Delete メソッド (ADO フィールドのコレクション)](../../../ado/reference/ado-api/delete-method-ado-fields-collection.md)   
 [Delete メソッド (ADO パラメーターのコレクション)](../../../ado/reference/ado-api/delete-method-ado-parameters-collection.md)   
 [Delete メソッド (ADO レコード セット)](../../../ado/reference/ado-api/delete-method-ado-recordset.md)   
 [プロパティをフィルター処理します。](../../../ado/reference/ado-api/filter-property.md)   
 [メソッドを再同期します。](../../../ado/reference/ado-api/resync-method.md)   
 [UpdateBatch メソッド](../../../ado/reference/ado-api/updatebatch-method.md)

