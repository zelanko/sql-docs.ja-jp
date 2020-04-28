---
title: ADO メソッド |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- ADO, methods
- methods [ADO]
ms.assetid: a38c5670-ba28-44f3-bd5b-fcb46880e904
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 8df204daeda82f809cf50246590141729e3608e5
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "67920923"
---
# <a name="ado-methods"></a>ADO メソッド

|||  
|-|-|  
|[AddNew](../../../ado/reference/ado-api/addnew-method-ado.md)|更新可能な**レコードセット**オブジェクトの新しいレコードを作成します。|  
|[Append](../../../ado/reference/ado-api/append-method-ado.md)|オブジェクトをコレクションに追加します。 コレクションが**フィールド**の場合は、コレクションに追加する前に新しい**Field**オブジェクトを作成できます。|  
|[AppendChunk](../../../ado/reference/ado-api/appendchunk-method-ado.md)|大きなテキストまたはバイナリデータ**フィールド**、または**パラメーター**オブジェクトにデータを追加します。|  
|[BeginTrans、CommitTrans、RollbackTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md)|は、次のように、**接続**オブジェクト内のトランザクション処理を管理します。<br /><br /> **BeginTrans** -新しいトランザクションを開始します。<br /><br /> **CommitTrans** -変更を保存し、現在のトランザクションを終了します。 また、新しいトランザクションを開始することもできます。<br /><br /> **RollbackTrans** -すべての変更を取り消し、現在のトランザクションを終了します。 また、新しいトランザクションを開始することもできます。|  
|[キャンセル](../../../ado/reference/ado-api/cancel-method-ado.md)|保留中の非同期メソッド呼び出しの実行を取り消します。|  
|[CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md)|保留中のバッチ更新をキャンセルします。|  
|[CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md)|**Update**メソッドを呼び出す前に、**レコードセット**オブジェクトの現在または新しい行、または**レコード**オブジェクトの**Fields**コレクションに対して行われたすべての変更を取り消します。|  
|[クリア](../../../ado/reference/ado-api/clear-method-ado.md)|**エラーコレクションから**すべての**エラー**オブジェクトを削除します。|  
|[複製](../../../ado/reference/ado-api/clone-method-ado.md)|既存の**レコード**セットオブジェクトから、重複する**レコードセット**オブジェクトを作成します。 必要に応じて、複製が読み取り専用であることを指定します。|  
|[閉じる](../../../ado/reference/ado-api/close-method-ado.md)|開いているオブジェクトとすべての依存オブジェクトを閉じます。|  
|[CompareBookmarks](../../../ado/reference/ado-api/comparebookmarks-method-ado.md)|2つのブックマークを比較し、それらの相対値を示す値を返します。|  
|[CopyRecord](../../../ado/reference/ado-api/copyrecord-method-ado.md)|ファイルまたはディレクトリ、およびその内容を別の場所にコピーします。|  
|[CopyTo](../../../ado/reference/ado-api/copyto-method-ado.md)|**ストリーム**内の指定した文字数またはバイト数 (**型**によって異なる) を別の**ストリーム**オブジェクトにコピーします。|  
|[CreateParameter](../../../ado/reference/ado-api/createparameter-method-ado.md)|指定されたプロパティを持つ新しい**パラメーター**オブジェクトを作成します。|  
|[Delete (ADO Parameters コレクション)](../../../ado/reference/ado-api/delete-method-ado-parameters-collection.md)|**Parameters**コレクションからオブジェクトを削除します。|  
|[Delete (ADO Fields コレクション)](../../../ado/reference/ado-api/delete-method-ado-fields-collection.md)|**フィールド**コレクションからオブジェクトを削除します。|  
|[Delete (ADO レコードセット)](../../../ado/reference/ado-api/delete-method-ado-recordset.md)|現在のレコードまたはレコードのグループを削除します。|  
|[DeleteRecord](../../../ado/reference/ado-api/deleterecord-method-ado.md)|ファイルまたはディレクトリ、およびそのすべてのサブディレクトリを削除します。|  
|[Execute (ADO コマンド)](../../../ado/reference/ado-api/execute-method-ado-command.md)|**CommandText**プロパティで指定されたクエリ、SQL ステートメント、またはストアドプロシージャを実行します。|  
|[Execute (ADO Connection)](../../../ado/reference/ado-api/execute-method-ado-connection.md)|指定されたクエリ、SQL ステートメント、ストアドプロシージャ、またはプロバイダー固有のテキストを実行します。|  
|[探す](../../../ado/reference/ado-api/find-method-ado.md)|**レコードセット**内で、指定した条件を満たす行を検索します。|  
|[揃える](../../../ado/reference/ado-api/flush-method-ado.md)|ADO バッファーに残っている**ストリーム**の内容を、**ストリーム**が関連付けられている基になるオブジェクトに強制的に適用します。|  
|[get_OLEDBCommand メソッド](../../../ado/reference/ado-api/get-oledbcommand-method.md)|基になる OLEDB コマンドを返します。最初に ADO コマンドで設定されたパラメーター情報を OLEDB コマンドに反映します。|  
|[GetChildren](../../../ado/reference/ado-api/getchildren-method-ado.md)|この**レコード**によって表されるディレクトリ内のファイルとサブディレクトリを表す行を含む**レコードセット**を返します。|  
|[GetChunk](../../../ado/reference/ado-api/getchunk-method-ado.md)|大きなテキストまたはバイナリデータ**フィールド**オブジェクトの内容のすべて、または一部を返します。|  
|[GetDataProviderDSO メソッド](../../../ado/reference/ado-api/getdataproviderdso-method.md)|基になる OLEDB データソースオブジェクトをシェイププロバイダーから取得します。|  
|[GetRows](../../../ado/reference/ado-api/getrows-method-ado.md)|**レコードセット**オブジェクトの複数のレコードを配列に取得します。|  
|[GetString](../../../ado/reference/ado-api/getstring-method-ado.md)|**レコードセット**を文字列として返します。|  
|[LoadFromFile](../../../ado/reference/ado-api/loadfromfile-method-ado.md)|既存のファイルの内容を**ストリーム**に読み込みます。|  
|[合わせ](../../../ado/reference/ado-api/move-method-ado.md)|**レコードセット**オブジェクト内の現在のレコードの位置を移動します。|  
|[MoveFirst、MoveLast、MoveNext、および MovePrevious](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)|指定したレコード**セット**オブジェクト内の最初、最後、次、または前のレコードに移動し、そのレコードを現在のレコードにします。|  
|[MoveRecord](../../../ado/reference/ado-api/moverecord-method-ado.md)|ファイルまたはディレクトリとその内容を別の場所に移動します。|  
|[NextRecordset](../../../ado/reference/ado-api/nextrecordset-method-ado.md)|一連のコマンドを進めて、現在の**レコードセット**オブジェクトをクリアし、次の**レコードセット**を返します。|  
|[開く (ADO 接続)](../../../ado/reference/ado-api/open-method-ado-connection.md)|データソースへの接続を開きます。|  
|[Open (ADO レコード)](../../../ado/reference/ado-api/open-method-ado-record.md)|既存の**レコード**オブジェクトを開くか、新しいファイルまたはディレクトリを作成します。|  
|[Open (ADO レコードセット)](../../../ado/reference/ado-api/open-method-ado-recordset.md)|カーソルを開きます。|  
|[Open (ADO Stream)](../../../ado/reference/ado-api/open-method-ado-stream.md)|**ストリーム**オブジェクトを開き、バイナリデータまたはテキストデータのストリームを操作します。|  
|[OpenSchema](../../../ado/reference/ado-api/openschema-method.md)|プロバイダーからデータベーススキーマ情報を取得します。|  
|[put_OLEDBCommand メソッド](../../../ado/reference/ado-api/put-oledbcommand-method.md)|このメソッドは操作を実行しません。常に S_OK を返します。|  
|[読み取り](../../../ado/reference/ado-api/read-method.md)|**ストリーム**オブジェクトから指定されたバイト数を読み取ります。|  
|[ReadText](../../../ado/reference/ado-api/readtext-method.md)|テキスト**ストリーム**オブジェクトから指定された数の文字を読み取ります。|  
|[更新](../../../ado/reference/ado-api/refresh-method-ado.md)|プロバイダーによって使用可能なオブジェクトを反映するように、コレクション内のオブジェクトを更新します。|  
|[Requery](../../../ado/reference/ado-api/requery-method.md)|オブジェクトの基になっているクエリを再実行することによって、**レコードセット**オブジェクトのデータを更新します。|  
|[再同期](../../../ado/reference/ado-api/resync-method.md)|基になるデータベースから、現在の**レコードセット**オブジェクトまたは**レコード**オブジェクトの**Fields**コレクションのデータを更新します。|  
|[および](../../../ado/reference/ado-api/save-method.md)|ファイルまたは**ストリーム**オブジェクトに**レコードセット**を保存します。|  
|[SaveToFile](../../../ado/reference/ado-api/savetofile-method.md)|**ストリーム**のバイナリコンテンツをファイルに保存します。|  
|[Seek](../../../ado/reference/ado-api/seek-method.md)|**レコードセット**のインデックスを検索して、指定した値と一致する行をすばやく検索し、現在の行の位置をその行に変更します。|  
|[SetEOS](../../../ado/reference/ado-api/seteos-method.md)|ストリームの末尾である位置を設定します。|  
|[SkipLine](../../../ado/reference/ado-api/skipline-method.md)|テキストストリームを読み取るときに、1行全体をスキップします。|  
|[統計](../../../ado/reference/ado-api/stat-method.md)|開いているストリームに関する統計情報を取得します。|  
|[サポート](../../../ado/reference/ado-api/supports-method.md)|指定した**レコードセット**オブジェクトが特定の種類の機能をサポートするかどうかを判断します。|  
|[Update](../../../ado/reference/ado-api/update-method.md)|レコード**セット**オブジェクトの現在の行、または**レコード**オブジェクトの**Fields**コレクションに対して行ったすべての変更を保存します。|  
|[UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)|すべての保留中のバッチ更新をディスクに書き込みます。|  
|[書き込み](../../../ado/reference/ado-api/write-method.md)|バイナリデータを**ストリーム**オブジェクトに書き込みます。|  
|[WriteText](../../../ado/reference/ado-api/writetext-method.md)|指定したテキスト文字列を**ストリーム**オブジェクトに書き込みます。|  
  
## <a name="see-also"></a>参照  
 [ADO API リファレンス](../../../ado/reference/ado-api/ado-api-reference.md)   
 [ADO コレクション](../../../ado/reference/ado-api/ado-collections.md)   
 [ADO の動的プロパティ](../../../ado/reference/ado-api/ado-dynamic-properties.md)   
 [ADO 列挙定数](../../../ado/reference/ado-api/ado-enumerated-constants.md)   
 [付録 B: ADO エラー](../../../ado/guide/appendixes/appendix-b-ado-errors.md)   
 [ADO イベント](../../../ado/reference/ado-api/ado-events.md)   
 [ADO オブジェクトモデル](../../../ado/reference/ado-api/ado-object-model.md)   
 [ADO オブジェクトとインターフェイス](../../../ado/reference/ado-api/ado-objects-and-interfaces.md)   
 [ADO のプロパティ](../../../ado/reference/ado-api/ado-properties.md)
