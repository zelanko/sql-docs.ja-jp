---
title: "HelloData に関するコメント |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- hellodata sample application [ADO]
ms.assetid: a2831d77-7040-4b73-bbae-fe0bf78107ed
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2265e361258ee49a9d387f3cb879f138c196ba8e
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="comments-on-hellodata"></a>HelloData に関するコメント
通常、ADO アプリケーションの基本的な操作手順を HelloData アプリケーション: を取得する、検査、編集、およびデータを更新します。 アプリケーションを起動するときに、最初のボタンをクリックして**データの取得**です。 これは、実行、 **GetData**サブルーチンです。  
  
## <a name="getdata"></a>GetData  
 **GetData**モジュール レベルの変数に有効な接続文字列を配置*m_sConnStr*です。 接続文字列の詳細については、次を参照してください。[接続文字列を作成する](../../../ado/guide/data/creating-a-connection-string.md)です。  
  
 Visual Basic を使用して、エラー ハンドラーを割り当てる**OnError**ステートメントです。 ADO のエラー処理の詳細については、次を参照してください。 [Error Handling](../../../ado/guide/data/error-handling.md)です。 新しい**接続**オブジェクトを作成すると、および**CursorLocation**プロパティに設定されている**adUseClient** HelloData 例では、作成されるため、 *切断されたレコード セット*です。 つまり、データ ソースからデータをフェッチしたが、データ ソースとの物理的な接続が切断がまだ、ローカルにキャッシュされているデータを使用することができ、すぐに、 **Recordset**オブジェクト。  
  
 接続が開かれた後は、SQL 文字列を変数 (sSQL) に割り当てます。 新しいインスタンスを作成し、 **Recordset**オブジェクト、`m_oRecordset1`です。 次のコード行で開く、 **Recordset**既存**接続**を渡して、`sSQL`のソースとして、**レコード セット**です。 SQL の文字列をことを決定する際に ADO をヘルプのソースとして渡されますが、**レコード セット**を渡すことによって、コマンドのテキストの定義は、 **adCmdText** への最終的な引数で**レコード セットを開いて**メソッドです。 この行にも設定、 **LockType**と**カーソル。**に関連付けられている、 **Recordset**です。  
  
 次のコード セットの行、**スレッド**プロパティを等しく**adMarshalModifiedOnly**です。 **スレッド**どのレコードを中間層 (または Web サーバー) にマーシャ リングすることを示します。 マーシャ リングの詳細については、COM のマニュアルを参照してください。 使用すると**adMarshalModifiedOnly**クライアント側カーソル ([CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) = **adUseClient**)、変更されているレコードだけ、クライアントは、中間層に書き戻されます。 設定**スレッド**に**adMarshalModifiedOnly**マーシャ リングする行数が少ないために、パフォーマンスを向上させることができます。  
  
 次に、切断、**レコード セット**を設定してその**ActiveConnection**プロパティを等しく**Nothing**です。 詳細についてを参照してください「の接続を切断および再接続、レコード セット」で[更新およびデータの永続化](../../../ado/guide/data/updating-and-persisting-data.md)です。  
  
 データ ソースへの接続を閉じるし、既存の破棄**接続**オブジェクト。 これは、使用するリソースを解放します。  
  
 最後に、設定、**レコード セット**として、**データソース**からデータを簡単に表示できる Microsoft DataGrid 制御フォームにこれを**レコード セット**で、フォームです。  
  
 2 番目のボタンをクリックして**確認データ**です。 これにより、実行、 **ExamineData**サブルーチンです。  
  
## <a name="examinedata"></a>ExamineData  
 ExamineData 各種のメソッドとプロパティを使用して、 **Recordset**内のデータに関する情報を表示するオブジェクト、**レコード セット**です。 使用してレコードの数を報告、 **RecordCount**プロパティです。 ループ、**レコード セット**の値を表示し、 **AbsolutePosition**フォームの表示のテキスト ボックス内のプロパティです。 ループの値のときに、**ブックマーク**3 番目のレコードのプロパティは、バリアント型の変数に格納されます*vBookmark*、後で使用します。  
  
 ルーチンは、以前に格納するブックマーク変数を使用する 3 番目のレコードに直接移動します。 ルーチンの呼び出し、 **WalkFields**をループ処理するサブルーチン、**フィールド**のコレクション、 **Recordset**それぞれに関する詳細を表示および**フィールド**コレクション内で。  
  
 最後に、 **ExamineData**を使用して、**フィルター**のプロパティ、 **Recordset**高いレコードだけを画面に、 **CategoryId**と等しい2 になります。 このフィルターを適用した結果は、フォームの表示グリッドにすぐに表示されます。  
  
 示すように機能の詳細については、 **ExamineData**サブルーチンを参照してください[データを調べる](../../../ado/guide/data/examining-data.md)です。  
  
 次に、3 番目のボタンをクリックして**データの編集**です。 これは、実行、 **EditData**サブルーチンです。  
  
## <a name="editdata"></a>EditData  
 コードを入力した場合、 **EditData**サブルーチン、**レコード セット**によってフィルター選択をまだ**CategoryId** 2、一致するフィルター条件を満たす項目だけが実行されるように表示されます。 最初のループ、**レコード セット**で表示される各項目の価格になり、**レコード セット**10% です。 値、**価格**フィールドが設定によって、変更、**値**そのフィールドが新しい有効な金額と同等のプロパティです。  
  
 注意して、 **Recordset**データ ソースから切断されています。 行われた変更**EditData**ローカルにキャッシュされたデータのコピーに対してのみ実行されます。 詳細については、次を参照してください。[データを編集](../../../ado/guide/data/editing-data.md)です。  
  
 変更できません。 データ ソースの 4 番目のボタンをクリックするまで**更新データ**です。 これは、実行、 **UpdateData**サブルーチンです。  
  
## <a name="updatedata"></a>UpdateData  
 UpdateData が最初に適用されたフィルターを削除、 **Recordset**です。 コードを削除し、戻します`m_oRecordset1`として、**データソース**Microsoft バインドされた datagrid のフォームにできるように、フィルター選択されていない**レコード セット**グリッドに表示されます。  
  
 コードがさら後方に移動することができるかどうかを確認、 **Recordset**を使用して、**サポート**メソッドを**adMovePrevious**引数。  
  
 ルーチンに最初のレコードを使用して、移動、 **MoveFirst**メソッドを使用してフィールドの元と現在の値を表示し、 **OriginalValue**と**値**プロパティ、**フィールド**オブジェクト。 あると連携して、これらのプロパティ、 **UnderlyingValue**プロパティ (ここを使用していない) では、後ほど[更新およびデータの永続化](../../../ado/guide/data/updating-and-persisting-data.md)です。  
  
 次に、新しい**接続**オブジェクトが作成され、データ ソースへの接続を再確立するために使用します。 再接続する、**レコード セット**するには、新しいデータ ソースに**接続**として、 **ActiveConnection**の**Recordset**です。 コードの呼び出し、サーバーに更新を送信する**UpdateBatch**上、 **Recordset**です。  
  
 バッチ更新が成功すると、モジュール レベルのフラグ変数`m_flgPriceUpdated`が True に設定します。 データベースに対して行われたすべての変更をクリーンアップするには、後でこの通知されます。  
  
 最後に、コードに移動の最初のレコード、 **Recordset**し元と現在の値を表示します。 呼び出し後は、値が同じ**UpdateBatch**です。  
  
 データを更新する方法の詳細については、場合の対処方法を含むサーバーの変更中に上のデータ、**レコード セット**が切断されるを参照してください[更新およびデータの永続化](../../../ado/guide/data/updating-and-persisting-data.md)です。  
  
## <a name="formunload"></a>Form_Unload  
 **Form_Unload**いくつかの理由のサブルーチンは重要です。 最初に、これはサンプル アプリケーションであるため、form_unload をアプリケーションが終了する前に、データベースに加えられた変更します。 次に、コードは、コマンドを実行して、開いているから直接方法**接続**オブジェクトを使用して、 **Execute**メソッドです。 最後に、データ ソースに対する非行を返さないクエリ (UPDATE クエリ) を実行する例を示します。
