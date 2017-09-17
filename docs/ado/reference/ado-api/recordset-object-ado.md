---
title: "レコード セット オブジェクト (ADO) |Microsoft ドキュメント"
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
- Recordset
helpviewer_keywords:
- Recordset object [ADO]
ms.assetid: ede1415f-c3df-4cc5-a05b-2576b2b84b60
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 7ad07b3aeaa8428bc5c2dee78a061c511893daef
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="recordset-object-ado"></a>レコード セット オブジェクト (ADO)
ベース テーブル、または実行されたコマンドの結果から、レコードのセット全体を表します。 いつでも、 **Recordset**オブジェクトとして現在のレコード セット内で 1 つのレコードのみを参照します。  
  
## <a name="remarks"></a>解説  
 使用する**Recordset**プロバイダーからデータを操作するオブジェクト。 ほぼすべてを使用してデータを操作する ADO を使用して、 **Recordset**オブジェクト。 すべて**Recordset**オブジェクトは、レコード (行) とフィールド (列)。 プロバイダーによってサポートされている機能に応じていくつか**レコード セット**メソッドまたはプロパティを使用できない可能性があります。  
  
 ADODB です。レコード セットが作成するために使用する必要があります、ProgID、 **Recordset**オブジェクト。 古い ADOR を参照する既存のアプリケーションです。レコード セットの ProgID を再コンパイルせずに作業が続行されますが、新規の開発が ADODB を参照する必要があります。レコード セットです。  
  
 ADO で定義されている 4 つのカーソルのさまざまな種類があります。  
  
-   **動的カーソル**内の移動のすべての型は、追加、変更、およびその他のユーザーによって削除を表示することができます、 **Recordset**をブックマーク; に依存しないでき、ブックマーク、プロバイダーがサポートされている場合します。  
  
-   **キーセット カーソル**ことを防ぎますレコードが表示されるその他のユーザー以外は動的カーソルのような動作の追加、およびその他のユーザーを削除するレコードにアクセスできなくなります。 他のユーザーがデータの変更も表示されます。 常にブックマークをサポートし、すべての種類の内の移動が可能になります、 **Recordset**です。  
  
-   **静的カーソル**は一連のレコードを使用してデータを検索またはレポートを生成するための静的コピーを提供以外の場合は常にによりブックマークでき、したがって内の移動のすべての種類、 **Recordset**です。 追加、変更、または他のユーザーによって削除は表示されません。 これは、クライアント側を開くときに許可されているカーソルの 1 種類しか**Recordset**オブジェクト。  
  
-   **順方向専用カーソル**だけスクロールすることができます、 **Recordset**です。 追加、変更、または他のユーザーによって削除は表示されません。 これを単一のパスのみを作成する必要がある状況でパフォーマンスが向上、 **Recordset**です。  
  
 設定、[カーソル](../../../ado/reference/ado-api/cursortype-property-ado.md)開始する前にプロパティ、 **Recordset** 、カーソルの種類を選択するかを渡す、*カーソル。*引数と、 [を開く](../../../ado/reference/ado-api/open-method-ado-recordset.md)。メソッドです。 一部のプロバイダーは、すべてのカーソルの種類をサポートしません。 プロバイダーのマニュアルを確認してください。 カーソルの種類を指定しない場合、ADO は既定では、順方向専用カーソルを開きます。  
  
 場合、 [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md)プロパティに設定されている**adUseClient**を開くには、 **Recordset**、 **UnderlyingValue** プロパティ[フィールド](../../../ado/reference/ado-api/field-object.md)オブジェクトでは使用できません、返された**Recordset**オブジェクト。 作成することができます (OLE DB と共にで Microsoft SQL Server 用 Microsoft ODBC プロバイダー) などの一部のプロバイダーを併用すると、 **Recordset**以前に定義されたとは別にオブジェクト[接続](../../../ado/reference/ado-api/connection-object-ado.md)オブジェクトを接続文字列を渡すことによって、**開く**メソッドです。 ADO が作成されますが、[接続](../../../ado/reference/ado-api/connection-object-ado.md)オブジェクトを割り当てることはありませんそのオブジェクトをオブジェクト変数にします。 ただし、複数開いている場合**Recordset** 、同じ接続でオブジェクトを明示的に作成し、開く必要があります、**接続**オブジェクトですこの割り当て、**接続**。オブジェクト変数オブジェクト。 開くときに、このオブジェクト変数を使用しないかどうか、 **Recordset**オブジェクト、ADO が新たに作成**接続**ごとに新しいオブジェクト**Recordset**渡した同じ場合でも、接続文字列です。  
  
 数だけ作成できます**レコード セット**オブジェクトを必要とします。  
  
 開いたとき、 **Recordset**、先頭のレコードを現在のレコードが配置されている (該当する場合) および[BOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md)と[EOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md)プロパティに設定されます**False**. レコードが存在しない場合、 **BOF**と**EOF**プロパティ設定が**True**です。  
  
 使用することができます、 [MoveFirst](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)、 **MoveLast**、 **MoveNext**、および**MovePrevious**メソッド以外の場合は、[移動](../../../ado/reference/ado-api/move-method-ado.md)メソッド。および[AbsolutePosition](../../../ado/reference/ado-api/absoluteposition-property-ado.md)、[と、AbsolutePage](../../../ado/reference/ado-api/absolutepage-property-ado.md)、および[フィルター](../../../ado/reference/ado-api/filter-property.md)プロバイダーは、サポート、関連すると仮定すると、現在のレコードの位置を変更するプロパティ機能します。 順方向専用**Recordset**オブジェクトのみをサポート、 [MoveNext](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)メソッドです。 使用する場合、**移動**各レコードにアクセスするメソッド (または列挙、**レコード セット**)、使用することができます、 **BOF**と**EOF**プロパティ先頭または末尾のを越えて移動したかどうかの判断、 **Recordset**です。  
  
 機能を使用する前に、 **Recordset**オブジェクトを呼び出す必要があります、**サポート**機能がサポートされているか使用可能であることを確認するオブジェクトのメソッドです。 機能を使用する必要がありますいないときに、**サポート**false が返されます。 たとえば、使用することができます、 **MovePrevious**場合にのみ、メソッド`Recordset.Supports(adMovePrevious)`返します**True**です。 それ以外の場合、エラーになりますが、ため、 **Recordset**オブジェクトが閉じられている可能性がありますされ、機能が使用不可のインスタンスで表示されます。 興味のある機能がサポートされていない場合**サポート**も false に戻ります。 上の対応するプロパティまたはメソッドの呼び出しを避ける必要があります、ここで、 **Recrodset**オブジェクト。  
  
 **レコード セット**オブジェクトは、2 種類の更新をサポートできます: 即時とバッチです。 即時更新でデータに対するすべての変更が直ちに書き込まれます、基になるデータ ソースを呼び出すと、[更新](../../../ado/reference/ado-api/update-method.md)メソッドです。 パラメーターとして配列の値を渡すことも、 [AddNew](../../../ado/reference/ado-api/addnew-method-ado.md)と**更新**メソッドを同時に、レコードのいくつかのフィールドを更新します。  
  
 プロバイダーは、バッチ更新をサポートする場合、ことができます、プロバイダーが複数のレコードへの変更をキャッシュし、メッセージの送信でデータベースに 1 回の呼び出しで、 [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)メソッドです。 これに加えられた変更に適用されます、 **AddNew**、**更新**、および[削除](../../../ado/reference/ado-api/delete-method-ado-recordset.md)メソッドです。 呼び出した後、 **UpdateBatch**メソッドを使用できます、[ステータス](../../../ado/reference/ado-api/status-property-ado-recordset.md)それらを解決するために、データの競合を確認するプロパティです。  
  
> [!NOTE]
>  使用せず、クエリを実行する、[コマンド](../../../ado/reference/ado-api/command-object-ado.md)オブジェクト、クエリ文字列を渡す、**開く**のメソッド、 **Recordset**オブジェクト。 ただし、**コマンド**コマンド テキストを保持し、再実行するか、またはクエリ パラメーターを使用するときに、オブジェクトが必要です。  
  
 [モード](../../../ado/reference/ado-api/mode-property-ado.md)プロパティ アクセス権限を制御します。  
  
 **フィールド**コレクションの既定のメンバーは、 **Recordset**オブジェクト。 その結果、次の 2 つのコード ステートメントは等価です。  
  
```  
Debug.Print objRs.Fields.Item(0)  ' Both statements print   
Debug.Print objRs(0)              '  the Value of Item(0).  
```  
  
 ときに、**レコード セット**のみ、プロセス間でオブジェクトが渡される、**行セット**値がマーシャ リング、およびのプロパティ、**レコード セット**オブジェクトは無視されます。 います、中に、**行セット**に新しく作成したアンパック**レコード セット**オブジェクトで、またそのプロパティを既定値に設定します。  
  
 **Recordset**オブジェクトにスクリプトを実行しても安全です。  
  
 このセクションには、次のトピックが含まれています。  
  
-   [レコード セット オブジェクトのプロパティ、メソッド、およびイベント](../../../ado/reference/ado-api/recordset-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>参照  
 [接続オブジェクト (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)   
 [Fields コレクション (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)   
 [プロパティのコレクション (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)   
 [付録 a: プロバイダー](../../../ado/guide/appendixes/appendix-a-providers.md)
