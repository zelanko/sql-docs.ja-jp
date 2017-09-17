---
title: "MoveFirst、MoveLast、MoveNext、および MovePrevious メソッド (ADO) |Microsoft ドキュメント"
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
- Recordset15::MoveLast
- Recordset15::MoveNext
- Recordset15::raw_MoveNext
- Recordset15::raw_MovePrevious
- Recordset15::MoveFirst
- Recordset15::raw_MoveLast
- Recordset15::MovePrevious
- Recordset15::raw_MoveFirst
helpviewer_keywords:
- MoveNext method [ADO]
- MoveLast method [ADO]
- MoveFirst method [ADO]
- MovePrevious method [ADO]
ms.assetid: a61a01a7-5b33-4150-9126-21dfa63654cb
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: cda6c82147648f35adb80012d0810d514d08de86
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="movefirst-movelast-movenext-and-moveprevious-methods-ado"></a>MoveFirst、MoveLast、MoveNext、および MovePrevious メソッド (ADO)
First、last に移動次、または前のレコードを指定した[Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクトと現在のレコードを記録できるようにします。  
  
## <a name="syntax"></a>構文  
  
```  
  
recordset.{MoveFirst | MoveLast | MoveNext | MovePrevious}  
```  
  
## <a name="remarks"></a>解説  
 使用して、 **MoveFirst**メソッドの最初のレコードを現在のレコードの位置を移動する、 **Recordset**です。  
  
 使用して、 **MoveLast**に最後のレコードの現在位置に移動する方法を記録、 **Recordset**です。 **Recordset**オブジェクトには、ブックマークまたは旧バージョンとカーソルの移動をサポートする必要があります。 それ以外の場合、メソッドの呼び出しでエラーが発生します。  
  
 いずれかへの呼び出し**MoveFirst**または**MoveLast**ときに、 **Recordset**が空 (両方**BOF**と**EOF**True は、)、エラーが発生します。  
  
 使用して、 **MoveNext**を現在のレコードを移動するメソッドが 1 つのレコードをフォワード位置 (の下部に、 **Recordset**)。 最後のレコードが現在のレコードとを呼び出す場合、 **MoveNext**メソッド、ADO、現在のレコードの位置に後で設定の最後のレコード、 **Recordset** ([EOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md)は**True**)。 ときに前方に移動しよう、 **EOF**プロパティが既に**True**でエラーが生成されます。  
  
 ADO で 2.5 以降の場合に、 **Recordset**フィルター選択されたまたは並べ替えられ、現在のレコードのデータが変更され、呼び出し、 **MoveNext**メソッドは、現在のレコードからの 2 つのカーソルのレコードを転送に移動. これは、ため、現在のレコードが変更されたときに、[次へ] レコードが、新しい現在のレコードです。 呼び出す**MoveNext**変更は、新しい現在のレコードからカーソル レコードは 1 つ転送を移動した後です。 これは、ADO 2.1 で動作と異なりますが、以前です。 これらの以前のバージョンでは、並べ替えまたはフィルター選択された現在のレコードのデータを変更する**Recordset**現在のレコードの位置は変更されず**MoveNext**カーソルを次のレコードに移動直後に、現在のレコードです。  
  
 使用して、 **MovePrevious**メソッドを現在のレコードを移動する旧バージョンと 1 つのレコードの位置 (の上部に向かって、**レコード セット**)。 **Recordset**オブジェクトには、ブックマークまたは旧バージョンとカーソルの移動をサポートする必要があります。 それ以外の場合、メソッドの呼び出しでエラーが発生します。 最初のレコードは、現在のレコードとを呼び出す場合、 **MovePrevious**メソッドに設定され、現在のレコードの最初のレコードの前に、の位置、 **Recordset** ([BOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md)は**True**)。 旧バージョンとされる場合に移動しよう、 **BOF**プロパティが既に**True**でエラーが生成されます。 場合、 **Recordset**オブジェクトはブックマークまたは旧バージョンとカーソルの動きのいずれかをサポートしていません、 **MovePrevious**メソッドでエラーが発生します。  
  
 場合、 **Recordset**のみを転送、前方および後方スクロールがサポートする場合は、使用することができます、 [CacheSize](../../../ado/reference/ado-api/cachesize-property-ado.md)旧バージョンとカーソルの移動をサポートするレコードのキャッシュを作成するプロパティを介して、[移動](../../../ado/reference/ado-api/move-method-ado.md)メソッドです。 キャッシュされているレコードがメモリに読み込まれ、ために、必要以上のレコードをキャッシュを回避する必要があります。 呼び出すことができます、 **MoveFirst**順方向専用のメソッド**Recordset**オブジェクト以外のプロバイダーを生成したコマンドを再実行することがありますが、**レコード セット**オブジェクト.  
  
## <a name="applies-to"></a>適用対象  
 [レコード セット オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [MoveFirst、MoveLast、MoveNext、および MovePrevious メソッドの例 (VB)](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-example-vb.md)   
 [MoveFirst、MoveLast、MoveNext、および MovePrevious メソッドの例 (VBScript)](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-example-vbscript.md)   
 [MoveFirst、MoveLast、MoveNext、および MovePrevious メソッドの例 (vc++)](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-example-vc.md)   
 [Move メソッド (ADO)](../../../ado/reference/ado-api/move-method-ado.md)   
 [MoveFirst、MoveLast、MoveNext、および MovePrevious メソッド (RDS)](../../../ado/reference/rds-api/movefirst-movelast-movenext-and-moveprevious-methods-rds.md)   
 [後続のメソッド (ADO)](../../../ado/reference/ado-api/moverecord-method-ado.md)

