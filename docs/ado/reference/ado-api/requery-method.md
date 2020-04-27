---
title: Requery メソッド |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::Requery
- Recordset15::raw_Requery
helpviewer_keywords:
- Requery method [ADO]
ms.assetid: d81ab76f-1aa8-4ccf-92ec-b65254dc3ea1
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c3626f91018714fa4d67304c92ce464d82fb5c8e
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "67917222"
---
# <a name="requery-method"></a>Requery メソッド
オブジェクトの基になっているクエリを再実行することによって、[レコードセット](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクトのデータを更新します。  
  
## <a name="syntax"></a>構文  
  
```  
  
recordset.Requery Options  
```  
  
#### <a name="parameters"></a>パラメーター  
 *[オプション]*  
 任意。 この操作に影響を与える[Executeoptionenum](../../../ado/reference/ado-api/executeoptionenum.md)値および[commandtypeenum](../../../ado/reference/ado-api/commandtypeenum.md)値を含むビットマスク。  
  
> [!NOTE]
>  *オプション*が**adasyncexecute**に設定されている場合、この操作は非同期に実行され、終了時に[RecordsetChangeComplete](../../../ado/reference/ado-api/willchangerecordset-and-recordsetchangecomplete-events-ado.md)イベントが発行されます。 **AdExecuteNoRecords**または**AdExecuteStream**の**executeopenenum**値は、 **Requery**と共に使用することはできません。  
  
## <a name="remarks"></a>Remarks  
 **Requery**メソッドを使用して、元のコマンドを再実行し、データをもう一度取得して、データソースから**レコードセット**オブジェクトの内容全体を更新します。 このメソッドを呼び出すことは、 [Close](../../../ado/reference/ado-api/close-method-ado.md)メソッドと[Open](../../../ado/reference/ado-api/open-method-ado-recordset.md)メソッドを連続して呼び出すことと同じです。 現在のレコードを編集している場合、または新しいレコードを追加している場合は、エラーが発生します。  
  
 **Recordset**オブジェクトが開いている間、カーソルの性質を定義するプロパティ ([CursorType](../../../ado/reference/ado-api/cursortype-property-ado.md)、 [LockType](../../../ado/reference/ado-api/locktype-property-ado.md)、 [MaxRecords](../../../ado/reference/ado-api/maxrecords-property-ado.md)など) は読み取り専用です。 したがって、 **Requery**メソッドで更新できるのは現在のカーソルだけです。 カーソルのプロパティを変更して結果を表示するには、 [Close](../../../ado/reference/ado-api/close-method-ado.md)メソッドを使用して、プロパティが再度読み取り/書き込み可能になるようにする必要があります。 その後、プロパティの設定を変更し、 [Open](../../../ado/reference/ado-api/open-method-ado-recordset.md)メソッドを呼び出してカーソルを再び開くことができます。  
  
## <a name="applies-to"></a>適用対象  
 [Recordset オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [Execute、Requery、および Clear メソッドの例 (VB)](../../../ado/reference/ado-api/execute-requery-and-clear-methods-example-vb.md)   
 [Execute、Requery、および Clear メソッドの例 (VBScript)](../../../ado/reference/ado-api/execute-requery-and-clear-methods-example-vbscript.md)   
 [Execute、Requery、および Clear メソッドの例 (VC + +)](../../../ado/reference/ado-api/execute-requery-and-clear-methods-example-vc.md)   
 [CommandText プロパティ (ADO)](../../../ado/reference/ado-api/commandtext-property-ado.md)
