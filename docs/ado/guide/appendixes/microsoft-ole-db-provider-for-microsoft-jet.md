---
title: "Microsoft OLE DB Provider for Microsoft Jet |Microsoft ドキュメント"
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
- Jet provider for OLE DB [ADO]
- providers [ADO], OLE DB provider for Microsoft Jet
- OLE DB provider for Microsoft Jet [ADO]
ms.assetid: fd956da1-5203-40af-aa7e-fc13a6c6581f
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 5d703eff7e65b590961a4bc78a70032050e1b395
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="microsoft-ole-db-provider-for-microsoft-jet-overview"></a>Microsoft OLE DB Provider for Jet の概要
OLE DB Provider for Jet は、Microsoft Jet データベースにアクセスする ADO できます。

## <a name="connection-string-parameters"></a>接続文字列パラメーター
 このプロバイダーに接続するには、設定、*プロバイダー*の引数、 [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md)には、次のプロパティ。

```
Microsoft.Jet.OLEDB.4.0
```

 読み取り、[プロバイダー](../../../ado/reference/ado-api/provider-property-ado.md)プロパティは、この文字列でも返されます。

## <a name="typical-connection-string"></a>一般的な接続文字列
 このプロバイダーの一般的な接続文字列とは。

```
"Provider=Microsoft.Jet.OLEDB.4.0;Data Source=databaseName;User ID=MyUserID;Password=MyPassword;"
```

 文字列は、これらのキーワードで構成されます。

|Keyword|Description|
|-------------|-----------------|
|**プロバイダー**|Microsoft Jet 用の OLE DB プロバイダーを指定します。|
|**[データ ソース]**|データベースのパスとファイル名を指定します (たとえば、 `c:\Northwind.mdb`)。|
|**[ユーザー ID]**|ユーザー名を指定します。 このキーワードが指定されていない場合、文字列"`admin`"は既定で使用します。|
|**Password**|ユーザーのパスワードを指定します。 このキーワードが指定されていない場合、空の文字列 ("")、既定で使用します。|

> [!NOTE]
>  Windows 認証をサポートするデータ ソース プロバイダーに接続するかどうかは、する必要がありますを指定する**Trusted_Connection = [はい]**または**Integrated Security = SSPI**ユーザー ID とパスワードの代わりに接続文字列の情報です。

## <a name="provider-specific-connection-parameters"></a>プロバイダー固有の接続パラメーター
 OLE DB Provider for Jet は、ADO で定義されたものだけでなく、いくつかのプロバイダーに固有の動的のプロパティをサポートします。 他のすべてのと同様に**接続**パラメーターを設定できますを使用して、**プロパティ**のコレクション、**接続**オブジェクト、または接続文字列の一部として。

 次の表は、かっこ内の対応する OLE DB プロパティ名と共にこれらのプロパティを一覧表示します。

|パラメーター|Description|
|---------------|-----------------|
|Jet OLEDB:Compact 回収された領域の量 (DBPROP_JETOLEDB_COMPACTFREESPACESIZE)|データベースを圧縮することで再利用できるが、バイト単位での領域の量の推定値を示します。 この値は、データベース接続が確立された後にのみ有効です。|
|Jet OLEDB:Connection コントロール (DBPROP_JETOLEDB_CONNECTIONCONTROL)|ユーザーがデータベースに接続できるかどうかを示します。|
|Jet OLEDB: システム データベース (DBPROP_JETOLEDB_CREATESYSTEMDATABASE) を作成します。|新しいデータ ソースを作成するときに、システム データベースを作成するかどうかを示します。|
|Jet OLEDB:Database ロック モード (DBPROP_JETOLEDB_DATABASELOCKMODE)|このデータベースのロック モードを示します。 開くには、データベースの最初のユーザーは、データベースが開いているときに使用されるモードを決定します。|
|Jet OLEDB:Database パスワード (DBPROP_JETOLEDB_DATABASEPASSWORD)|データベース パスワードを示します。|
|Jet OLEDB: Compact (DBPROP_JETOLEDB_COMPACT_DONTCOPYLOCALE) のロケールをコピーしないでください|データベースを圧縮する場合に、Jet がロケール情報をコピーするかどうかを示します。|
|Jet OLEDB: データベース (DBPROP_JETOLEDB_ENCRYPTDATABASE) の暗号化|最適化されたデータベースを暗号化するかどうかを示します。 このプロパティが設定されていない場合は、元のデータベースが暗号化されても場合に最適化されたデータベースが暗号化されます。|
|Jet OLEDB:Engine 型 (DBPROP_JETOLEDB_ENGINE)|現在のデータ ストアにアクセスするために使用するストレージ エンジンを示します。|
|Jet OLEDB:Exclusive Async 遅延 (DBPROP_JETOLEDB_EXCLUSIVEASYNCDELAY)|時間 (ミリ秒)、データベースが排他的に開かれたときにディスクに非同期の書き込み遅延の最大長を示します。<br /><br /> しない限り、このプロパティは無視されます**Jet OLEDB:Flush トランザクション タイムアウト**は 0 に設定します。|
|Jet OLEDB:Flush トランザクションのタイムアウト (DBPROP_JETOLEDB_FLUSHTRANSACTIONTIMEOUT)|非同期の書き込み用のキャッシュに格納されたデータが実際に書き込まれる前に待機する時間の割合をディスクにします。 この設定は、の値を上書きします。 **Jet OLEDB: 共有 Async 遅延**と**Jet OLEDB:Exclusive Async 遅延**です。|
|Jet OLEDB: グローバル一括トランザクション (DBPROP_JETOLEDB_GLOBALBULKNOTRANSACTIONS)|SQL 一括トランザクションが処理されるかどうかを示します。|
|Jet OLEDB: グローバルの部分的な一括 Ops (DBPROP_JETOLEDB_GLOBALBULKPARTIAL)|データベースを開くために使用するパスワードを示します。|
|Jet OLEDB: 暗黙的なコミットの同期 (DBPROP_JETOLEDB_IMPLICITCOMMITSYNC)|内部の暗黙のトランザクションで行われた変更が同期または非同期モードで書き込まれるかどうかを示します。|
|Jet OLEDB:Lock 遅延 (DBPROP_JETOLEDB_LOCKDELAY)|前回の試みが失敗した後、ロックの取得を試みる前に待機するミリ秒数を示します。|
|Jet OLEDB:Lock 再試行 (DBPROP_JETOLEDB_LOCKRETRY)|ロックされたページにアクセスしようとするが繰り返される回数を示します。|
|Jet OLEDB:Max バッファー サイズ (DBPROP_JETOLEDB_MAXBUFFERSIZE)|最大の量を示す、メモリ (キロバイト単位)、Jet を使用できるの変更をディスクにフラッシュを開始する前にします。|
|ファイル (DBPROP_JETOLEDB_MAXLOCKSPERFILE) ごとの jet OLEDB:Max ロック|データベースに配置できるロックの最大数を示します。 既定値は、9500 です。|
|Jet OLEDB: 新しいデータベースのパスワード (DBPROP_JETOLEDB_NEWDATABASEPASSWORD)|このデータベース用に設定する新しいパスワードを示します。 古いパスワードは保存**Jet OLEDB:Database パスワード**です。|
|Jet OLEDB:ODBC コマンド タイムアウト (DBPROP_JETOLEDB_ODBCCOMMANDTIMEOUT)|Jet からリモート ODBC クエリの前に時間をミリ秒単位はタイムアウトになったことを示します。|
|Jet OLEDB:Page のロックをテーブル ロック (DBPROP_JETOLEDB_PAGELOCKSTOTABLELOCK)|Jet ロックがテーブル ロックに昇格しようとする前に、トランザクション内でページ数をロックする必要がありますを示します。 この値が 0 の場合、ロックは昇格されません。|
|Jet OLEDB:Page タイムアウト (DBPROP_JETOLEDB_PAGETIMEOUT)|Jet は、キャッシュがデータベース ファイルと最新でないかどうかをチェックする前に待機するミリ秒数を示します。|
|Jet OLEDB:Recycle 時間の長い値ページ (DBPROP_JETOLEDB_RECYCLELONGVALUEPAGES)|Jet は必要がありますが解放された場合に、BLOB のページを再利用を積極的に試みるかどうかを示します。|
|Jet OLEDB:Registry パス (DBPROP_JETOLEDB_REGPATH)|Jet データベース エンジンの値を含む Windows レジストリ キーを示します。|
|Jet OLEDB:Reset ISAM 統計 (DBPROP_JETOLEDB_RESETISAMSTATS)|示すかどうか、スキーマ**Recordset** DBSCHEMA_JETOLEDB_ISAMSTATS はパフォーマンス情報が返った後にそのパフォーマンス カウンターをリセットする必要があります。|
|Jet OLEDB: 非同期遅延 (DBPROP_JETOLEDB_SHAREDASYNCDELAY) を共有|最大の量を示す Jet 時間をミリ秒単位でデータベースがマルチ ユーザー モードで開かれたときにディスクへの非同期書き込みを遅らせることができます。|
|Jet OLEDB:System Database (DBPROP_JETOLEDB_SYSDBPATH)|ワークグループ情報ファイル (システム データベース) のパスとファイル名を示します。|
|Jet OLEDB:Transaction コミット モード (DBPROP_JETOLEDB_TXNCOMMITMODE)|Jet が同期的にディスクにデータを書き込むかどうかまたは非同期的に、トランザクションがコミットされることを示します。|
|Jet OLEDB:User コミット同期 (DBPROP_JETOLEDB_USERCOMMITSYNC)|同期または非同期モードでのトランザクションで行われた変更を書き込むかどうかを示します。|

## <a name="provider-specific-recordset-and-command-properties"></a>プロバイダー固有のレコード セットとコマンドのプロパティ
 Jet プロバイダーは、プロバイダーに固有のいくつかもサポートしています。 **Recordset**と**コマンド**プロパティです。 これらのプロパティにアクセスしてを使用して設定、**プロパティ**のコレクション、 **Recordset**または**コマンド**オブジェクト。 テーブルには、ADO プロパティ名とかっこ内に対応する OLE DB プロパティ名が一覧表示します。

|プロパティ名|Description|
|-------------------|-----------------|
|Jet OLEDB:Bulk トランザクション (DBPROP_JETOLEDB_BULKNOTRANSACTIONS)|SQL 一括操作が処理されるかどうかを示します。 リソースの遅延のため、トランザクション、大量の一括操作が失敗します。|
|Jet OLEDB:Enable Fat カーソル (DBPROP_JETOLEDB_ENABLEFATCURSOR)|リモート行ソースのレコード セットを作成するときに、複数の行をキャッシュするかどうかを示します。|
|Jet OLEDB:Fat カーソルのキャッシュ サイズ (DBPROP_JETOLEDB_FATCURSORMAXROWS)|リモート データ ストアの行のキャッシュを使用する場合は、キャッシュする行の数を示します。 しない限り、この値は無視されます**Jet OLEDB:Enable Fat カーソル**true を指定します。|
|Jet OLEDB: 整合性がありません (DBPROP_JETOLEDB_INCONSISTENT)|クエリの結果が不整合な更新を許可するかどうかを示します。|
|Jet OLEDB: ロック粒度 (DBPROP_JETOLEDB_LOCKGRANULARITY)|行レベルのロックを使用して、テーブルを開いたかどうかを示します。|
|Jet OLEDB:ODBC パススルー ステートメント (DBPROP_JETOLEDB_ODBCPASSTHROUGH)|Jet が内の SQL テキストを渡すことを示す、**コマンド**オブジェクトを変更せずに、バックエンドにします。|
|Jet OLEDB:Partial 一括 Ops (DBPROP_JETOLEDB_BULKPARTIAL)|SQL DML 操作が失敗した場合は、Jet の動作を示します。|
|クエリ一括 Op (DBPROP_JETOLEDB_PASSTHROUGHBULKOP) を通じて jet OLEDB:Pass|かどうかクエリをしないことを示しますを返す、 **Recordset**データ ソースに変更されていないに渡されます。|
|クエリによって jet OLEDB:Pass 接続文字列 (DBPROP_JETOLEDB_ODBCPASSTHROUGHCONNECTSTRING)|使用する Jet 接続文字列を示すリモート データ ストアに接続します。 しない限り、この値は無視されます**Jet OLEDB:ODBC パススルー ステートメント**true を指定します。|
|Jet OLEDB: クエリ (DBPROP_JETOLEDB_STOREDQUERY) が格納されています。|SQL コマンドの代わりに、ストアド クエリとして、コマンド テキストを解釈するかどうかを示します。|
|Jet OLEDB: セット (DBPROP_JETOLEDB_VALIDATEONSET) 上のルールを検証|列のデータが設定されている場合、または変更をデータベースにコミットするときに、Jet の検証規則を評価するかどうかを示します。|

 既定は、OLE DB Provider for Jet は、Microsoft Jet データベースを読み取り/書き込みモードで開きます。 データベースは、読み取り専用モードで開き、次のように設定します。、[モード](../../../ado/reference/ado-api/mode-property-ado.md)プロパティを ADO**接続**オブジェクトを**adModeRead**です。

## <a name="command-object-usage"></a>コマンド オブジェクトの使用方法
 コマンドのテキスト、[コマンド](../../../ado/reference/ado-api/command-object-ado.md)オブジェクトでの Microsoft Jet SQL 構文を使用します。 コマンド テキストで行を返すクエリ、処理クエリ、およびテーブル名を指定できます。ただし、ストアド プロシージャはサポートされていません、指定することはできません。

## <a name="recordset-behavior"></a>レコード セットの動作
 Microsoft Jet データベース エンジンは、動的カーソルをサポートしていません。 したがって、OLE DB Provider for Jet はできません、 **adLockDynamic**カーソルの種類。 動的カーソルが要求されたときに、プロバイダーは、キーセット カーソルを返すし、リセット、[カーソル。](../../../ado/reference/ado-api/cursortype-property-ado.md)プロパティの型を示す[Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)が返されます。 さらに場合、更新可能な**Recordset**が要求された (**LockType**は**adLockOptimistic**、 **adLockBatchOptimistic**、または**adLockPessimistic**) プロバイダーによっても、キーセット カーソルを返すされをリセット、**カーソル。**プロパティです。

## <a name="dynamic-properties"></a>動的プロパティ
 OLE DB Provider for Jet にいくつかの動的なプロパティの挿入、**プロパティ**、開かれていないのコレクション[接続](../../../ado/reference/ado-api/connection-object-ado.md)、[レコード セット](../../../ado/reference/ado-api/recordset-object-ado.md)、および[コマンド](../../../ado/reference/ado-api/command-object-ado.md)オブジェクト。

 次の表は、各動的プロパティの ADO および OLE DB 名 cross-index です。 語を"Description"ADO プロパティ名を参照して、OLE DB プログラマーズ リファレンス OLE DB プログラマーズ リファレンスの詳細については、これらのプロパティを見つけることができます。

## <a name="connection-dynamic-properties"></a>接続の動的プロパティ
 次のプロパティを追加、**プロパティ**のコレクション、**接続**オブジェクト。

|ADO プロパティ名|OLE DB プロパティの名前|
|-----------------------|--------------------------|
|Active sessions|DBPROP_ACTIVESESSIONS|
|非同期中止|DBPROP_ASYNCTXNABORT|
|非同期のコミット|DBPROP_ASYNCTNXCOMMIT|
|自動コミットの分離レベル|DBPROP_SESS_AUTOCOMMITISOLEVELS|
|カタログの場所|DBPROP_CATALOGLOCATION|
|カタログの用語|DBPROP_CATALOGTERM|
|列の定義|DBPROP_COLUMNDEFINITION|
|現在のカタログ|DBPROP_CURRENTCATALOG|
|[データ ソース]|DBPROP_INIT_DATASOURCE|
|Data Source Name|DBPROP_DATASOURCENAME|
|データ ソース オブジェクト スレッド モデル|DBPROP_DSOTHREADMODEL|
|DBMS の名前|DBPROP_DBMSNAME|
|DBMS のバージョン|DBPROP_DBMSVER|
|グループ化のサポート|DBPROP_GROUPBY|
|異なるテーブルのサポート|DBPROP_HETEROGENEOUSTABLES|
|識別子の大文字と小文字の区別|DBPROP_IDENTIFIERCASE|
|分離レベル|DBPROP_SUPPORTEDTXNISOLEVELS|
|分離保有期間|DBPROP_SUPPORTEDTXNISORETAIN|
|[Locale Identifier]|DBPROP_INIT_LCID|
|インデックスの最大サイズ|DBPROP_MAXINDEXSIZE|
|行の最大サイズ|DBPROP_MAXROWSIZE|
|最大行サイズには、BLOB が含まれています。|DBPROP_MAXROWSIZEINCLUDESBLOB|
|SELECT の最大のテーブル|DBPROP_MAXTABLESINSELECT|
|[モード]|DBPROP_INIT_MODE|
|複数のパラメーター セット|DBPROP_MULTIPLEPARAMSETS|
|複数の結果|DBPROP_MULTIPLERESULTS|
|複数のストレージ オブジェクト|DBPROP_MULTIPLESTORAGEOBJECTS|
|複数のテーブルの更新|DBPROP_MULTITABLEUPDATE|
|NULL の照合順序|DBPROP_NULLCOLLATION|
|NULL を連結した動作|DBPROP_CONCATNULLBEHAVIOR|
|OLE DB バージョン|DBPROP_PROVIDEROLEDBVER|
|OLE オブジェクトのサポート|DBPROP_OLEOBJECTS|
|行セットのサポートを開く|DBPROP_OPENROWSETSUPPORT|
|選択リストの ORDER BY 列|DBPROP_ORDERBYCOLUMNSINSELECT|
|出力パラメーターの使用状況|DBPROP_OUTPUTPARAMETERAVAILABILITY|
|Ref アクセサーを使って渡す|DBPROP_BYREFACCESSORS|
|Password|DBPROP_AUTH_PASSWORD|
|永続的な ID 型|DBPROP_PERSISTENTIDTYPE|
|中止の動作を準備します。|DBPROP_PREPAREABORTBEHAVIOR|
|コミット動作を準備します。|DBPROP_PREPARECOMMITBEHAVIOR|
|プロシージャの用語|DBPROP_PROCEDURETERM|
|[プロンプト]|DBPROP_INIT_PROMPT|
|プロバイダーの表示名|DBPROP_PROVIDERFRIENDLYNAME|
|Provider Name|DBPROP_PROVIDERFILENAME|
|プロバイダーのバージョン|DBPROP_PROVIDERVER|
|読み取り専用のデータ ソース|DBPROP_DATASOURCEREADONLY|
|行セットの変換|DBPROP_ROWSETCONVERSIONSONCOMMAND|
|スキーマの用語|DBPROP_SCHEMATERM|
|スキーマの使用|DBPROP_SCHEMAUSAGE|
|SQL のサポート|DBPROP_SQLSUPPORT|
|構造化ストレージ|DBPROP_STRUCTUREDSTORAGE|
|サブクエリのサポート|DBPROP_SUBQUERIES|
|テーブルの用語|DBPROP_TABLETERM|
|トランザクション DDL|DBPROP_SUPPORTEDTXNDDL|
|[ユーザー ID]|DBPROP_AUTH_USERID|
|[ユーザー名]|DBPROP_USERNAME|
|ウィンドウ ハンドル|DBPROP_INIT_HWND|

## <a name="recordset-dynamic-properties"></a>レコード セットの動的プロパティ
 次のプロパティを追加、**プロパティ**のコレクション、 **Recordset**オブジェクト。

|ADO プロパティ名|OLE DB プロパティの名前|
|-----------------------|--------------------------|
|アクセスの順序|DBPROP_ACCESSORDER|
|追加専用の行セット|DBPROP_APPENDONLY|
|ブロック記憶域オブジェクト|DBPROP_BLOCKINGSTORAGEOBJECTS|
|ブックマークの種類|DBPROP_BOOKMARKTYPE|
|ブックマークを設定|DBPROP_IROWSETLOCATE|
|ブックマークの順序指定|DBPROP_ORDEREDBOOKMARKS|
|キャッシュ列の遅延|DBPROP_CACHEDEFERRED|
|挿入行を変更します。|DBPROP_CHANGEINSERTEDROWS|
|列権限|DBPROP_COLUMNRESTRICT|
|列セットの通知|DBPROP_NOTIFYCOLUMNSET|
|書き込み可能な列|DBPROP_MAYWRITECOLUMN|
|列を遅延します。|DBPROP_DEFERRED|
|記憶域オブジェクトの更新を遅延します。|DBPROP_DELAYSTORAGEOBJECTS|
|後方のフェッチします。|DBPROP_CANFETCHBACKWARDS|
|行を保持します。|DBPROP_CANHOLDROWS|
|IAccessor|DBPROP_IAccessor|
|IColumnsInfo|DBPROP_IColumnsInfo|
|IColumnsRowset|DBPROP_IColumnsRowset|
|IConnectionPointContainer|DBPROP_IConnectionPointContainer|
|IConvertType|DBPROP_IConvertType|
|ILockBytes|DBPROP_ILockBytes|
|移動不可の行|DBPROP_IMMOBILEROWS|
|IRowset|DBPROP_IRowset|
|IRowsetChange|DBPROP_IRowsetChange|
|IRowsetIdentity|DBPROP_IRowsetIdentity|
|IRowsetIndex|DBPROP_IRowsetIndex|
|IRowsetInfo|DBPROP_IRowsetInfo|
|IRowsetLocate|DBPROP_IRowsestLocate|
|IRowsetResynch||
|IRowsetScroll|DBPROP_IRowsetScroll|
|IRowsetUpdate|DBPROP_IRowsetUpdate|
|ISequentialStream|DBPROP_ISequentialStream|
|IStorage|DBPROP_IStorage|
|IStream|DBPROP_IStream|
|ISupportErrorInfo|DBPROP_ISupportErrorInfo|
|リテラルのブックマーク|DBPROP_LITERALBOOKMARKS|
|リテラルの行 Id を使用|DBPROP_LITERALIDENTITY|
|開いている行の最大数|DBPROP_MAXOPENROWS|
|保留中の行の最大数|DBPROP_MAXPENDINGROWS|
|行の最大数|DBPROP_MAXROWS|
|メモリ使用量|DBPROP_MEMORYUSAGE|
|通知の粒度|DBPROP_NOTIFICATIONGRANULARITY|
|通知フェーズ|DBPROP_NOTIFICATIONPHASES|
|トランザクション化されたオブジェクト|DBPROP_TRANSACTEDOBJECT|
|その他の変更の表示|DBPROP_OTHERUPDATEDELETE|
|その他の挿入の表示|DBPROP_OTHERINSERT|
|独自の変更の表示|DBPROP_OWNUPDATEDELETE|
|独自の挿入の表示|DBPROP_OWNINSERT|
|中止時に保存します。|DBPROP_ABORTPRESERVE|
|コミット時に保存します。|DBPROP_COMMITPRESERVE|
|クイック再起動|DBPROP_QUICKRESTART|
|再入可能なイベント|DBPROP_REENTRANTEVENTS|
|削除された行を削除します。|DBPROP_REMOVEDELETED|
|複数の変更を報告します。|DBPROP_REPORTMULTIPLECHANGES|
|保留中の挿入を返す|DBPROP_RETURNPENDINGINSERTS|
|行の削除通知|DBPROP_NOTIFYROWDELETE|
|行の最初の変更通知|DBPROP_NOTIFYROWFIRSTCHANGE|
|行挿入の通知|DBPROP_NOTIFYROWINSERT|
|行の特権|DBPROP_ROWRESTRICT|
|行の再同期の通知|DBPROP_NOTIFYROWRESYNCH|
|スレッド処理モデルの行|DBPROP_ROWTHREADMODEL|
|行の変更の取り消し通知|DBPROP_NOTIFYROWUNDOCHANGE|
|行の削除の取り消し通知|DBPROP_NOTIFYROWUNDODELETE|
|行の挿入の取り消し通知|DBPROP_NOTIFYROWUNDOINSERT|
|行の更新通知|DBPROP_NOTIFYROWUPDATE|
|行セットのフェッチ位置の変更通知|DBPROP_NOTIFYROWSETFETCHPOSISIONCHANGE|
|行セットのリリースの通知|DBPROP_NOTIFYROWSETRELEASE|
|逆にスクロールします。|DBPROP_CANSCROLLBACKWARDS|
|Skip は、ブックマークを削除します。|DBPROP_BOOKMARKSKIPPED|
|厳密な行 Id を使用|DBPROP_STRONGITDENTITY|
|更新機能|DBPROP_UPDATABILITY|
|ブックマークを使用します。|DBPROP_BOOKMARKS|

## <a name="command-dynamic-properties"></a>コマンドの動的プロパティ
 次のプロパティを追加、**プロパティ**のコレクション、**コマンド**オブジェクト。

|ADO プロパティ名|OLE DB プロパティの名前|
|-----------------------|--------------------------|
|アクセスの順序|DBPROP_ACCESSORDER|
|追加専用の行セット|DBPROP_APPENDONLY|
|ブロック記憶域オブジェクト|DBPROP_BLOCKINGSTORAGEOBJECTS|
|ブックマークの種類|DBPROP_BOOKMARKTYPE|
|ブックマークを設定|DBPROP_IROWSETLOCATE|
|挿入行を変更します。|DBPROP_CHANGEINSERTEDROWS|
|列権限|DBPROP_COLUMNRESTRICT|
|列セットの通知|DBPROP_NOTIFYCOLUMNSET|
|列を遅延します。|DBPROP_DEFERRED|
|記憶域オブジェクトの更新を遅延します。|DBPROP_DELAYSTORAGEOBJECTS|
|後方のフェッチします。|DBPROP_CANFETCHBACKWARDS|
|行を保持します。|DBPROP_CANHOLDROWS|
|IAccessor|DBPROP_IAccessor|
|IColumnsInfo|DBPROP_IColumnsInfo|
|IColumnsRowset|DBPROP_IColumnsRowset|
|IConnectionPointContainer|DBPROP_IConnectionPointContainer|
|IConvertType|DBPROP_IConvertType|
|ILockBytes|DBPROP_ILockBytes|
|移動不可の行|DBPROP_IMMOBILEROWS|
|IRowset|DBPROP_IRowset|
|IRowsetChange|DBPROP_IRowsetChange|
|IRowsetIdentity|DBPROP_IRowsetIdentity|
|IRowsetIndex|DBPROP_IRowsetIndex|
|IRowsetInfo|DBPROP_IRowsetInfo|
|IRowsetLocate|DBPROP_IRowsetLocate|
|IRowsetResynch||
|IRowsetScroll|DBPROP_IRowsetScroll|
|IRowsetUpdate|DBPROP_IRowsetUpdate|
|ISequentialStream|DBPROP_ISequentialStream|
|IStorage|DBPROP_IStorage|
|IStream|DBPROP_IStream|
|ISupportErrorInfo|DBPROP_ISupportErrorInfo|
|リテラルのブックマーク|DBPROP_LITERALBOOKMARKS|
|リテラルの行 Id を使用|DBPROP_LITERALIDENTITY|
|ロック モード|DBPROP_LOCKMODE|
|開いている行の最大数|DBPROP_MAXOPENROWS|
|保留中の行の最大数|DBPROP_MAXPENDINGROWS|
|行の最大数|DBPROP_MAXROWS|
|通知の粒度|DBPROP_NOTIFICATIONGRANULARITY|
|通知フェーズ|DBPROP_NOTIFICATIONPHASES|
|トランザクション化されたオブジェクト|DBPROP_TRANSACTEDOBJECT|
|その他の変更の表示|DBPROP_OTHERUPDATEDELETE|
|その他の挿入の表示|DBPROP_OTHERINSERT|
|独自の変更の表示|DBPROP_OWNUPDATEDELETE|
|独自の挿入の表示|DBPROP_OWNINSERT|
|中止時に保存します。|DBPROP_ABORTPRESERVE|
|コミット時に保存します。|DBPROP_COMMITPRESERVE|
|クイック再起動|DBPROP_QUICKRESTART|
|再入可能なイベント|DBPROP_REENTRANTEVENTS|
|削除された行を削除します。|DBPROP_REMOVEDELETED|
|複数の変更を報告します。|DBPROP_REPORTMULTIPLECHANGES|
|保留中の挿入を返す|DBPROP_RETURNPENDINGINSERTS|
|行の削除通知|DBPROP_NOTIFYROWDELETE|
|行の最初の変更通知|DBPROP_NOTIFYROWFIRSTCHANGE|
|行挿入の通知|DBPROP_NOTIFYROWINSERT|
|行の特権|DBPROP_ROWRESTRICT|
|行の再同期の通知|DBPROP_NOTIFYROWRESYNCH|
|スレッド処理モデルの行|DBPROP_ROWTHREADMODEL|
|行の変更の取り消し通知|DBPROP_NOTIFYROWUNDOCHANGE|
|行の削除の取り消し通知|DBPROP_NOTIFYROWUNDODELETE|
|行の挿入の取り消し通知|DBPROP_NOTIFYROWUNDOINSERT|
|行の更新通知|DBPROP_NOTIFYROWUPDATE|
|行セットのフェッチ位置の変更通知|DBPROP_NOTIFYROWSETFETCHPOSITIONCHANGE|
|行セットのリリースの通知|DBPROP_NOTIFYROWSETRELEASE|
|逆にスクロールします。|DBPROP_CANSCROLLBACKWARDS|
|挿入時のサーバー データ|DBPROP_SERVERDATAONINSERT|
|Skip は、ブックマークを削除します。|DBPROP_BOOKMARKSKIP|
|厳密な行 Id を使用|DBPROP_STRONGIDENTITY|
|更新機能|DBPROP_UPDATABILITY|
|ブックマークを使用します。|DBPROP_BOOKMARKS|

 特定の実装の詳細と、OLE DB Provider for Jet の機能については、次を参照してください。 [Jet プロバイダー](https://msdn.microsoft.com/library/windows/desktop/ms722791.aspx) 、OLE DB のドキュメントにします。
