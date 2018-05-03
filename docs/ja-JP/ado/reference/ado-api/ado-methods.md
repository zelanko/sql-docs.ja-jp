---
title: ADO のメソッド |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- ADO, methods
- methods [ADO]
ms.assetid: a38c5670-ba28-44f3-bd5b-fcb46880e904
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c94c32ce964f7b8d1501ea30067e81a9d4357bf9
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ado-methods"></a>ADO メソッド
|||  
|-|-|  
|[AddNew](../../../ado/reference/ado-api/addnew-method-ado.md)|作成、更新可能なに対して新しいレコード**Recordset**オブジェクト。|  
|[追加](../../../ado/reference/ado-api/append-method-ado.md)|オブジェクトをコレクションに追加します。 コレクションが場合**フィールド**、新しい**フィールド**をコレクションに追加する前に、オブジェクトを作成することがあります。|  
|[AppendChunk](../../../ado/reference/ado-api/appendchunk-method-ado.md)|大きなテキストまたはバイナリ データへのデータの追加**フィールド**、または、**パラメーター**オブジェクト。|  
|[BeginTrans、CommitTrans、および RollbackTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md)|内のトランザクション処理の管理、**接続**オブジェクトの次のようにします。<br /><br /> **BeginTrans** -新しいトランザクションを開始します。<br /><br /> **CommitTrans** : 変更を保存し、現在のトランザクションを終了します。 新しいトランザクションを開始する場合もします。<br /><br /> **RollbackTrans** — すべての変更をキャンセルし、現在のトランザクションを終了します。 新しいトランザクションを開始する場合もします。|  
|[キャンセル](../../../ado/reference/ado-api/cancel-method-ado.md)|実行をキャンセルする保留中、非同期メソッドの呼び出しです。|  
|[CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md)|保留中のバッチ更新をキャンセルします。|  
|[ただし](../../../ado/reference/ado-api/cancelupdate-method-ado.md)|現在のまたは新しい行に対して行われたすべての変更を取り消します、 **Recordset**オブジェクト、または**フィールド**のコレクション、**レコード**オブジェクトを呼び出す前に、 **更新**メソッドです。|  
|[Clear](../../../ado/reference/ado-api/clear-method-ado.md)|すべてを削除、**エラー**オブジェクトから、**エラー**コレクション。|  
|[複製](../../../ado/reference/ado-api/clone-method-ado.md)|複製を作成**Recordset** 、既存のオブジェクト**Recordset**オブジェクト。 必要に応じて、複製が読み取り専用であることを指定します。|  
|[[閉じる]](../../../ado/reference/ado-api/close-method-ado.md)|開いているオブジェクトとすべての依存オブジェクトを閉じます。|  
|[CompareBookmarks](../../../ado/reference/ado-api/comparebookmarks-method-ado.md)|2 つのブックマークを比較し、これらの相対値を示す値を返します。|  
|[CopyRecord](../../../ado/reference/ado-api/copyrecord-method-ado.md)|ファイルまたはディレクトリとその内容を別の場所にコピーします。|  
|[CopyTo](../../../ado/reference/ado-api/copyto-method-ado.md)|指定した数の文字またはバイトのコピー (に応じて**型**) で、**ストリーム**別**ストリーム**オブジェクト。|  
|[CreateParameter](../../../ado/reference/ado-api/createparameter-method-ado.md)|新たに作成**パラメーター**を指定されたプロパティを持つオブジェクト。|  
|[削除 (ADO パラメーターのコレクション)](../../../ado/reference/ado-api/delete-method-ado-parameters-collection.md)|オブジェクトを削除、**パラメーター**コレクション。|  
|[削除 (ADO Fields コレクション)](../../../ado/reference/ado-api/delete-method-ado-fields-collection.md)|オブジェクトを削除、**フィールド**コレクション。|  
|[削除 (ADO レコード セット)](../../../ado/reference/ado-api/delete-method-ado-recordset.md)|現在のレコードまたはレコードのグループを削除します。|  
|[DeleteRecord](../../../ado/reference/ado-api/deleterecord-method-ado.md)|ファイルまたはディレクトリとそのすべてのサブディレクトリを削除します。|  
|[(ADO コマンド) を実行します。](../../../ado/reference/ado-api/execute-method-ado-command.md)|クエリや、SQL ステートメントで指定されたストアド プロシージャの実行、 **CommandText**プロパティです。|  
|[(ADO 接続) を実行します。](../../../ado/reference/ado-api/execute-method-ado-connection.md)|指定されたクエリ、SQL ステートメント、ストアド プロシージャ、またはプロバイダー固有のテキストを実行します。|  
|[検索](../../../ado/reference/ado-api/find-method-ado.md)|検索、**レコード セット**を指定した条件を満たす行にします。|  
|[フラッシュ](../../../ado/reference/ado-api/flush-method-ado.md)|内容を強制的、**ストリーム**を基になるオブジェクトに ADO バッファーに残っている、**ストリーム**が関連付けられています。|  
|[get_OLEDBCommand メソッド](../../../ado/reference/ado-api/get-oledbcommand-method.md)|最初に、ADO コマンドの設定を ole DB コマンドにパラメーター情報を反映する、基になる ole DB コマンドを返します。|  
|[GetChildren](../../../ado/reference/ado-api/getchildren-method-ado.md)|返します、 **Recordset**ファイルとこれによって表されるディレクトリにサブディレクトリを表す行を持つ**レコード**です。|  
|[GetChunk](../../../ado/reference/ado-api/getchunk-method-ado.md)|大きなテキストまたはバイナリ データの内容の一部またはすべてが返されます**フィールド**オブジェクト。|  
|[GetDataProviderDSO メソッド](../../../ado/reference/ado-api/getdataproviderdso-method.md)|Shape プロバイダーから基になる ole DB データ ソース オブジェクトを取得します。|  
|[GetRows](../../../ado/reference/ado-api/getrows-method-ado.md)|複数のレコードを取得、 **Recordset**オブジェクトを配列にします。|  
|[GetString](../../../ado/reference/ado-api/getstring-method-ado.md)|返します、 **Recordset**を文字列として。|  
|[LoadFromFile](../../../ado/reference/ado-api/loadfromfile-method-ado.md)|既存のファイルの内容を読み込みます、**ストリーム**です。|  
|[[移動]](../../../ado/reference/ado-api/move-method-ado.md)|現在のレコードの位置を移動、 **Recordset**オブジェクト。|  
|[MoveFirst、MoveLast、MoveNext、および MovePrevious](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)|First、last に移動次、または前のレコードを指定した**Recordset**オブジェクトと現在のレコードを記録できるようにします。|  
|[MoveRecord](../../../ado/reference/ado-api/moverecord-method-ado.md)|ファイルまたはディレクトリ、およびその内容を別の場所に移動します。|  
|[NextRecordset](../../../ado/reference/ado-api/nextrecordset-method-ado.md)|現在のクリア**レコード セット**オブジェクトを返します**レコード セット**一連のコマンドを進めることで。|  
|[開く (ADO 接続)](../../../ado/reference/ado-api/open-method-ado-connection.md)|データ ソースへの接続を開きます。|  
|[(ADO レコード) を開きます](../../../ado/reference/ado-api/open-method-ado-record.md)|既存を開く**レコード**オブジェクト、または新しいファイルまたはディレクトリを作成します。|  
|[(ADO レコード セット) を開きます](../../../ado/reference/ado-api/open-method-ado-recordset.md)|カーソルを開きます。|  
|[開く (ADO Stream)](../../../ado/reference/ado-api/open-method-ado-stream.md)|開く、**ストリーム**バイナリまたはテキスト データのストリームを操作するオブジェクト。|  
|[OpenSchema](../../../ado/reference/ado-api/openschema-method.md)|プロバイダーからデータベース スキーマ情報を取得します。|  
|[put_OLEDBCommand メソッド](../../../ado/reference/ado-api/put-oledbcommand-method.md)|このメソッドは操作を行わない - 常に S_OK を返します。|  
|[読み取り](../../../ado/reference/ado-api/read-method.md)|指定したからのバイト数を読み取り、**ストリーム**オブジェクト。|  
|[ReadText](../../../ado/reference/ado-api/readtext-method.md)|テキストから指定数の文字を読み取ります**ストリーム**オブジェクト。|  
|[[更新]](../../../ado/reference/ado-api/refresh-method-ado.md)|プロバイダーをコレクションから、使用可能なオブジェクトを反映するように、固有の仕様内のオブジェクトを更新します。|  
|[クエリを再実行します。](../../../ado/reference/ado-api/requery-method.md)|データが更新、 **Recordset**オブジェクトの基になるクエリを再実行してオブジェクト。|  
|[再同期](../../../ado/reference/ado-api/resync-method.md)|現在のデータを更新**Recordset**オブジェクト、または**フィールド**のコレクション、**レコード**基になるデータベースからのオブジェクト。|  
|[[保存]](../../../ado/reference/ado-api/save-method.md)|保存、 **Recordset**ファイルまたは**ストリーム**オブジェクト。|  
|[SaveToFile](../../../ado/reference/ado-api/savetofile-method.md)|バイナリの内容を保存、**ストリーム**をファイルにします。|  
|[シーク](../../../ado/reference/ado-api/seek-method.md)|インデックスを検索、 **Recordset**に指定した値に一致する行に現在の行位置を変更した行をすばやく検索します。|  
|[SetEOS](../../../ado/reference/ado-api/seteos-method.md)|ストリームの末尾の位置を設定します。|  
|[SkipLine](../../../ado/reference/ado-api/skipline-method.md)|テキスト ストリームを読み取るときに、1 つの行全体をスキップします。|  
|[stat](../../../ado/reference/ado-api/stat-method.md)|開いているストリームに関する統計情報を取得します。|  
|[サポート](../../../ado/reference/ado-api/supports-method.md)|指定したかどうかを決定**Recordset**オブジェクトは、特定の種類の機能をサポートしています。|  
|[Update](../../../ado/reference/ado-api/update-method.md)|現在の行に加えたあらゆる変更を保存、 **Recordset**オブジェクト、または**フィールド**のコレクション、**レコード**オブジェクト。|  
|[UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)|すべての保留中のバッチ更新プログラムをディスクに書き込みます。|  
|[書き込み](../../../ado/reference/ado-api/write-method.md)|バイナリ データを書き込む、**ストリーム**オブジェクト。|  
|[WriteText](../../../ado/reference/ado-api/writetext-method.md)|指定したテキストに文字列を**ストリーム**オブジェクト。|  
  
## <a name="see-also"></a>参照  
 [ADO の API リファレンス](../../../ado/reference/ado-api/ado-api-reference.md)   
 [ADO コレクション](../../../ado/reference/ado-api/ado-collections.md)   
 [ADO の動的プロパティ](../../../ado/reference/ado-api/ado-dynamic-properties.md)   
 [ADO 列挙定数](../../../ado/reference/ado-api/ado-enumerated-constants.md)   
 [付録 b: ADO エラー](../../../ado/guide/appendixes/appendix-b-ado-errors.md)   
 [ADO イベント](../../../ado/reference/ado-api/ado-events.md)   
 [ADO オブジェクト モデル](../../../ado/reference/ado-api/ado-object-model.md)   
 [ADO オブジェクトとインターフェイス](../../../ado/reference/ado-api/ado-objects-and-interfaces.md)   
 [ADO のプロパティ](../../../ado/reference/ado-api/ado-properties.md)
