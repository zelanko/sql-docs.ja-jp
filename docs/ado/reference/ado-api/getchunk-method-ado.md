---
title: "GetChunk メソッド (ADO) |Microsoft ドキュメント"
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
- Field20::raw_GetChunk
- Field20::GetChunk
helpviewer_keywords:
- GetChunk method [ADO]
ms.assetid: fc268e22-205b-44a3-9038-ffed51e23e10
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 4972e08f1db08bde4cdb1241fa36895f2f33ad7b
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="getchunk-method-ado"></a>GetChunk メソッド (ADO)
大きなテキストまたはバイナリ データの内容の一部、または返します[フィールド](../../../ado/reference/ado-api/field-object.md)オブジェクト。  
  
## <a name="syntax"></a>構文  
  
```  
  
variable = field.GetChunk(Size)  
```  
  
## <a name="return-value"></a>戻り値  
 返します、**バリアント**です。  
  
#### <a name="parameters"></a>パラメーター  
 *サイズ*  
 A**長い**バイトまたは取得する文字の数と同じである式。  
  
## <a name="remarks"></a>解説  
 使用して、 **GetChunk**メソッドを**フィールド**長いバイナリまたは文字データの一部またはすべてを取得するオブジェクト。 システム メモリが限られている状況で使用できます、 **GetChunk**全体ではなく、特定の部分で長い値を操作するメソッド。  
  
 データを**GetChunk**に割り当てられている呼び出しが戻る*変数*です。 場合*サイズ*が残りのデータよりも大きい、 **GetChunk**埋め込みなしで残りのデータのみを返します*変数*空のスペースです。 フィールドが空である場合、 **GetChunk**メソッドは、null 値を返します。  
  
 以降の各**GetChunk**呼び出し場所からデータを取得する前の**GetChunk**呼び出しが中断します。 ただし 1 つのフィールドからを設定したり、現在のレコードの別のフィールドの値を読み取るデータを取得する ADO は最初のフィールドからのデータの取得が完了したらを想定します。 呼び出す場合は、 **GetChunk**番目のフィールドにもう一度、ADO 上のメソッドでは、解釈、新しい呼び出し**GetChunk**操作し、データの先頭からの読み取りを開始します。 他のフィールドにアクセスする[レコード セット](../../../ado/reference/ado-api/recordset-object-ado.md)最初のクローンではないオブジェクトを**Recordset**オブジェクトを妨害しない**GetChunk**操作します。  
  
 場合、 **adFldLong**ビット、[属性](../../../ado/reference/ado-api/attributes-property-ado.md)のプロパティ、**フィールド**にオブジェクトが設定されている**True**、使用することができます、 **GetChunk**そのフィールドのメソッドです。  
  
 使用すると、現在のレコードがない場合、 **GetChunk**メソッドを**フィールド**オブジェクト、3021 (現在のレコードがありません) エラーが発生します。  
  
> [!NOTE]
>  **GetChunk**についてメソッドは動作しません**フィールド**のオブジェクト、[レコード](../../../ado/reference/ado-api/record-object-ado.md)オブジェクト。 任意の操作は実行されませんし、実行時エラーが生成されます。  
  
## <a name="applies-to"></a>適用対象  
 [Field オブジェクト](../../../ado/reference/ado-api/field-object.md)  
  
## <a name="see-also"></a>参照  
 [AppendChunk と GetChunk メソッドの例 (VB)](../../../ado/reference/ado-api/appendchunk-and-getchunk-methods-example-vb.md)   
 [AppendChunk と GetChunk メソッドの例 (vc++)](../../../ado/reference/ado-api/appendchunk-and-getchunk-methods-example-vc.md)   
 [AppendChunk メソッド (ADO)](../../../ado/reference/ado-api/appendchunk-method-ado.md)   
 [属性プロパティ (ADO)](../../../ado/reference/ado-api/attributes-property-ado.md)

