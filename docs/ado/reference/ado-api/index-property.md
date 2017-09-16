---
title: "Index プロパティ |Microsoft ドキュメント"
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
- Recordset21::Index
helpviewer_keywords:
- Index property
ms.assetid: 1c79e271-21ec-41a8-8163-c5e89f0001a7
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9091e9a65b178806c8695faffa50f11946c6b2ca
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="index-property"></a>Index プロパティ
有効にインデックスを現在の名前を示す、 [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクト。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 取得または設定、**文字列**値で、インデックスの名前を指定します。  
  
## <a name="remarks"></a>解説  
 指定したインデックス、**インデックス**プロパティ必要がありますが事前に宣言して基になるベース テーブルで、 **Recordset**オブジェクト。 つまり、インデックス必要がありますが宣言されているプログラムで ADOX として[インデックス](../../../ado/reference/adox-api/index-object-adox.md)オブジェクトか、ベース テーブルが作成されました。  
  
 インデックスを設定できない場合は、実行時エラーが発生します。 **インデックス**次の条件下でプロパティを設定することはできません。  
  
-   内で、 [WillChangeRecordset](../../../ado/reference/ado-api/willchangerecordset-and-recordsetchangecomplete-events-ado.md)または**RecordsetChangeComplete**イベント ハンドラー。  
  
-   場合、 **Recordset**操作がまだ実行中 (によって判断できます、[状態](../../../ado/reference/ado-api/state-property-ado.md)プロパティ)。  
  
-   フィルターが設定されている場合、 **Recordset**で、[フィルター](../../../ado/reference/ado-api/filter-property.md)プロパティです。  
  
 **インデックス**プロパティが常に正常に設定できる場合、 **Recordset**が閉じている場合ですが、**レコード セット**正常に開くことはありませんか、インデックスが使用するには場合、基になるプロバイダーは、インデックスをサポートしていません。  
  
 インデックスを設定できますが、現在の行位置は変更できます。 これにより、更新プログラムを[AbsolutePosition](../../../ado/reference/ado-api/absoluteposition-property-ado.md)プロパティとをまとめて、 **WillChangeRecordset**、 **RecordsetChangeComplete**、 [WillMove](../../../ado/reference/ado-api/willmove-and-movecomplete-events-ado.md)、および[MoveComplete](../../../ado/reference/ado-api/willmove-and-movecomplete-events-ado.md)イベント。  
  
 インデックスを設定できる場合、 [LockType](../../../ado/reference/ado-api/locktype-property-ado.md)プロパティは**adLockPessimistic**または**adLockOptimistic**、し、暗黙的な[UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)操作を実行します。 これにより、現在および影響を受けるグループが解放されます。 任意の既存のフィルターが解放され、並べ替えられたの最初の行を現在の行位置が変更された**Recordset**です。  
  
 **インデックス**と共にプロパティが使用される、[シーク](../../../ado/reference/ado-api/seek-method.md)メソッドです。 基になるプロバイダーがサポートしていない場合、**インデックス**プロパティ、およびこのインターフェイス、**シーク**メソッドの使用を検討、[検索](../../../ado/reference/ado-api/find-method-ado.md)メソッド代わりにします。 決定するかどうか、**レコード セット**オブジェクトを含むインデックスをサポートしている、[をサポートしている](../../../ado/reference/ado-api/supports-method.md)**(adIndex)**メソッドです。  
  
 組み込み**インデックス**プロパティが動的に関連しない[最適化](../../../ado/reference/ado-api/optimize-property-dynamic-ado.md)プロパティ、インデックスを扱うこれら両方ができます。  
  
## <a name="applies-to"></a>適用対象  
 [レコード セット オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [メソッドとインデックスのプロパティの例 (VB) にシークします。](../../../ado/reference/ado-api/seek-method-and-index-property-example-vb.md)   
 [Index オブジェクト (ADOX)](../../../ado/reference/adox-api/index-object-adox.md)   
 [Seek メソッド](../../../ado/reference/ado-api/seek-method.md)
