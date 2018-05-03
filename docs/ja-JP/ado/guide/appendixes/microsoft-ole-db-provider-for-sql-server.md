---
title: Microsoft OLE DB Provider for SQL Server |Microsoft ドキュメント
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
- providers [ADO], OLE DB provider for SQL Server
- OLE DB provider for SQL Server [ADO]
- SQLOLEDB [ADO]
ms.assetid: 99bc40c4-9181-4ca1-a06f-9a1a914a0b7b
caps.latest.revision: 19
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4002e1a8e0975d730d8947b452140665b6778f84
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="microsoft-ole-db-provider-for-sql-server-overview"></a>Microsoft OLE DB Provider for SQL Server の概要
Microsoft OLE DB Provider for SQL Server、SQLOLEDB では、ADO では Microsoft SQL Server にアクセスできます。

**注:** このドライバーを使用して、新規の開発をお勧めできません。 新しい OLE DB プロバイダーが呼び出されて、 [Microsoft OLE DB Driver for SQL Server](../../../connect/oledb/oledb-driver-for-sql-server.md) (MSOLEDBSQL) 今後、最新のサーバー機能が更新されます。

## <a name="connection-string-parameters"></a>接続文字列パラメーター
 このプロバイダーに接続するには、設定、*プロバイダー*への引数、 [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md)プロパティ。

```
SQLOLEDB
```

 この値も設定またはを使用して読み取る、[プロバイダー](../../../ado/reference/ado-api/provider-property-ado.md)プロパティです。

## <a name="typical-connection-string"></a>一般的な接続文字列
 このプロバイダーの一般的な接続文字列とは。

```
"Provider=SQLOLEDB;Data Source=serverName;"
Initial Catalog=databaseName;
User ID=MyUserID;Password=MyPassword;"
```

 文字列は、これらのキーワードで構成されます。

|Keyword|Description|
|-------------|-----------------|
|**プロバイダー**|OLE DB Provider for SQL Server を指定します。|
|**データ ソース**または**サーバー**|サーバーの名前を指定します。|
|**Initial Catalog**または**データベース**|サーバー上のデータベースの名前を指定します。|
|**ユーザー ID**または**uid**|(SQL Server 認証) のユーザー名を指定します。|
|**パスワード**または**pwd**|(SQL Server 認証) のユーザーのパスワードを指定します。|

> [!NOTE]
>  Windows 認証をサポートするデータ ソース プロバイダーに接続するかどうかは、する必要がありますを指定する**Trusted_Connection = [はい]** または**Integrated Security = SSPI**ユーザー ID とパスワードの代わりに接続文字列の情報です。

## <a name="provider-specific-connection-parameters"></a>プロバイダー固有の接続パラメーター
 プロバイダーは、ADO で定義されているだけでなく、いくつかのプロバイダーに固有の接続パラメーターをサポートします。 ADO 接続のプロパティを持つこれらのプロバイダーに固有のプロパティを設定してを使用して、[プロパティ](../../../ado/reference/ado-api/properties-collection-ado.md)のコレクション、[接続](../../../ado/reference/ado-api/connection-object-ado.md)の一部として設定できますまたは、 **ConnectionString**。

|パラメーター|Description|
|---------------|-----------------|
|Trusted_Connection|ユーザーの認証モードを示します。 これに設定できます**はい**または**いいえ**です。 既定値は **いいえ**します。 このプロパティ設定されている場合**はい**、SQLOLEDB では、Microsoft Windows NT の認証モードを使用して、ユーザーによって指定された SQL Server データベースへのアクセスを承認します、**場所**と[データソース](../../../ado/reference/ado-api/datasource-property-ado.md)プロパティの値。 このプロパティ設定されている場合**いいえ**SQLOLEDB では、混在モードを使用して、SQL Server データベースへのユーザー アクセスを承認します。 SQL Server ログインとパスワードが指定されて、**ユーザー Id**と**パスワード**プロパティです。|
|[現在の言語]|SQL Server 言語名を示します。 システム メッセージの選択や書式設定に使われる言語を示します。 SQL Server の言語をインストールする必要がそれ以外の場合の開始が、接続は失敗します。|
|[ネットワーク アドレス]|指定された SQL Server のネットワーク アドレスを示す、**場所**プロパティです。|
|ネットワーク ライブラリ|SQL Server と通信するために使用されるネットワーク ライブラリ (DLL) の名前を示します。 この名前には、パスやファイル拡張子 (.dll) は含めません。 既定値は、SQL Server client の構成によって提供されます。|
|準備の手順に従います|コマンドを準備するときに、SQL Server で一時ストアド プロシージャを作成するかどうかを決定 (によって、 **Prepared**プロパティ)。|
|Auto Translate します。|OEM/ANSI 文字を変換するかどうかを示します。 このプロパティに設定することができます**True**または**False**です。 既定値は **True**です。 このプロパティ設定されている場合**True**SQLOLEDB がマルチ バイト文字の文字列から取得されたまたは SQL Server に送信されるとき、OEM/ANSI 文字変換を実行します。 このプロパティ設定されている場合**False**SQLOLEDB では、マルチバイト文字の文字列データでは、OEM/ANSI 文字変換は行いません。|
|Packet Size|ネットワーク パケット サイズ (バイト単位) を示します。 パケット サイズ プロパティの値は、512 ~ 32767 の間にする必要があります。 既定の SQLOLEDB ネットワーク パケット サイズは 4096 です。|
|Application Name|クライアント アプリケーションの名前を示します。|
|[ワークステーション ID]|ワークステーションを識別する文字列。|

## <a name="command-object-usage"></a>コマンド オブジェクトの使用方法
 SQLOLEDB では、有効な構文として、ODBC、ANSI、および SQL Server に固有の TRANSACT-SQL の融合を受け取ります。 たとえば、次の SQL ステートメントでは、ODBC SQL のエスケープ シーケンスを使用して、LCASE 文字列関数を指定しています。

```
SELECT customerid={fn LCASE(CustomerID)} FROM Customers

```

 LCASE 関数は、大文字をすべて小文字に変換した文字列を返します。 ANSI SQL 文字列関数下は、次の SQL ステートメントは、ANSI の前に示した ODBC ステートメントと同じように、同じ操作を実行します。

```
SELECT customerid=LOWER(CustomerID) FROM Customers

```

 SQLOLEDB では、コマンドのテキストとして指定する場合は、ステートメントのいずれかの形式が正常に処理します。

## <a name="stored-procedures"></a>ストアド プロシージャ
 SQL Server を実行すると、SQLOLEDB コマンドを使用してストアド プロシージャが格納されている、ときに、コマンド テキストで ODBC プロシージャ呼び出しのエスケープ シーケンスを使用します。 SQLOLEDB では、SQL Server のリモート プロシージャ コールのメカニズムを使用して、コマンドの処理を最適化します。 たとえば、次の ODBC SQL ステートメントは、TRANSACT-SQL フォーム上の優先コマンド テキストを示します。

## <a name="odbc-sql"></a>ODBC SQL

```
{call SalesByCategory('Produce', '1995')}

```

## <a name="transact-sql"></a>Transact-SQL

```
EXECUTE SalesByCategory 'Produce', '1995'

```

## <a name="sql-server-features"></a>SQL Server の機能
 ADO と SQL Server の XML を使用できます**コマンド**入力や結果ではなく XML ストリームの形式で取得**Recordset**オブジェクト。 詳細については、次を参照してください。[コマンド入力を使用するストリーム](../../../ado/guide/data/command-streams.md)と[ストリームに結果セットを取得する](../../../ado/guide/data/retrieving-resultsets-into-streams.md)です。

### <a name="accessing-sqlvariant-data-using-mdac-27-mdac-28-or-windows-dac-60"></a>MDAC 2.7、MDAC 2.8、または Windows DAC 6.0 を使用して sql_variant データへのアクセス
 Microsoft SQL Server、あるデータ型と呼ばれる**sql_variant**です。 OLE DB のような**DBTYPE_VARIANT**、 **sql_variant**データ型は、さまざまな種類のデータを格納できます。 ただしのいくつかの主な違いがある**DBTYPE_VARIANT**と**sql_variant**です。 ADO もとして格納されたデータを処理、 **sql_variant**値の他のデータ型を処理する方法とは異なります。 次のように、型の列に格納されている SQL Server データにアクセスするときに考慮すべき問題**sql_variant**です。

-   MDAC 2.7、MDAC 2.8、Windows Data Access Components (Windows DAC) 6.0 では、OLE DB Provider for SQL Server をサポート、 **sql_variant**型です。 OLE DB Provider for ODBC されていません。

-   **Sql_variant**型は完全に一致しない、 **DBTYPE_VARIANT**データ型。  **Sql_variant**型でサポートされていないいくつかの新しいサブタイプをサポートしている**DBTYPE_VARIANT、**など**GUID**、 **ANSI** (UNICODE 以外の)文字列、および**BIGINT**です。 サブタイプを以外を使用して以前に一覧表示、正しく機能します。

-   **Sql_variant**サブタイプ**数値**と一致しません、 **DBTYPE_DECIMAL**サイズ。

-   複数のデータ型の強制変換は、一致しない型になります。 たとえば、強制型変換、 **sql_variant**のサブタイプに**GUID**を**DBTYPE_VARIANT**のサブタイプになります**safearray**(バイト単位). この種類の変換にバックアップ、 **sql_variant**の新しいサブタイプになります**配列**(バイト単位)。

-   **レコード セット**を含むフィールド**sql_variant**データは、リモート処理ができる (マーシャ リング) または保存される場合にのみ、 **sql_variant**特定サブタイプが含まれています。 リモートしようか、サポートされていない次のデータを永続化のサブタイプ、実行時エラーが発生 (サポートされていない変換) から Microsoft 永続化プロバイダー (MSPersist): **VT_VARIANT**、 **VT_RECORD**、 **VT_ILLEGAL**、 **VT_UNKNOWN**、 **VT_BSTR**、および**VT_DISPATCH です。**

-   MDAC 2.7、MDAC 2.8、および Windows DAC 6.0 における SQL Server の OLE DB プロバイダーと呼ばれる動的なプロパティがある**ネイティブ バリアントを許可する**、名前が示すように、開発が可能にアクセスする、 **sql_variant**でネイティブ形式はなく、 **DBTYPE_VARIANT**です。 このプロパティが設定されている場合、 **Recordset**クライアント カーソル エンジンでが開きます (**adUseClient**) では、 **Recordset.Open**呼び出しは失敗します。 このプロパティが設定されている場合、**レコード セット**サーバー カーソルで開かれた (**adUseServer**) では、 **Recordset.Open**呼び出しが成功すると、型の列へのアクセスが、**sql_variant**でエラーが発生します。

-   MDAC 2.5 を使用するクライアント アプリケーションで**sql_variant** Microsoft SQL Server に対するクエリでデータを使用することができます。 ただしの値、 **sql_variant**データは文字列として扱われます。 このようなクライアント アプリケーションは、MDAC 2.7、MDAC 2.8、または Windows DAC 6.0 にアップグレードする必要があります。

## <a name="recordset-behavior"></a>レコード セットの動作
 SQLOLEDB では、多くのコマンドによって生成される複数の結果をサポートするために、SQL Server カーソルを使用できません。 コンシューマーは、SQL Server カーソルのサポートを必要とするレコード セットを要求している場合、結果として使用するコマンド テキストが複数の単一のレコード セットが生成する場合にエラーが発生します。

 スクロール可能な SQLOLEDB レコード セットは、SQL Server カーソルでサポートされます。 SQL Server では、データベースの他のユーザーによって行われた変更影響を受けるカーソルに制限が適用されます。 具体的には、一部のカーソル内の行を並べ替えることができず、および SQL ORDER BY 句を含むコマンドを使用してレコード セットを作成しようとしましたが失敗することができます。

## <a name="dynamic-properties"></a>動的プロパティ
 Microsoft OLE DB Provider for SQL Server にいくつかの動的なプロパティの挿入、**プロパティ**、開かれていないのコレクション[接続](../../../ado/reference/ado-api/connection-object-ado.md)、 [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)、および[コマンド](../../../ado/reference/ado-api/command-object-ado.md)オブジェクト。

 次の表は、各動的プロパティの ADO および OLE DB 名 cross-index です。 「説明」という用語によって ADO プロパティ名を参照して、OLE DB プログラマーズ リファレンス OLE DB プログラマーズ リファレンスの詳細については、これらのプロパティを見つけることができます。 インデックスの OLE DB プロパティ名を検索するかを参照してください[付録 c: OLE DB プロパティ](http://msdn.microsoft.com/en-us/deded3ff-f508-4e1b-b2b1-fd9afd3bd292)です。

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
|Connect Timeout|DBPROP_INIT_TIMEOUT|
|現在のカタログ|DBPROP_CURRENTCATALOG|
|[データ ソース]|DBPROP_INIT_DATASOURCE|
|Data Source Name|DBPROP_DATASOURCENAME|
|データ ソース オブジェクト スレッド モデル|DBPROP_DSOTHREADMODEL|
|DBMS の名前|DBPROP_DBMSNAME|
|DBMS のバージョン|DBPROP_DBMSVER|
|Extended Properties|DBPROP_INIT_PROVIDERSTRING|
|グループ化のサポート|DBPROP_GROUPBY と|
|異なるテーブルのサポート|DBPROP_HETEROGENEOUSTABLES|
|識別子の大文字と小文字の区別|DBPROP_IDENTIFIERCASE|
|Initial Catalog|DBPROP_INIT_CATALOG|
|分離レベル|DBPROP_SUPPORTEDTXNISOLEVELS|
|分離保有期間|DBPROP_SUPPORTEDTXNISORETAIN|
|[Locale Identifier]|DBPROP_INIT_LCID|
|インデックスの最大サイズ|DBPROP_MAXINDEXSIZE|
|行の最大サイズ|DBPROP_MAXROWSIZE|
|最大行サイズには、BLOB が含まれています。|DBPROP_MAXROWSIZEINCLUDESBLOB|
|SELECT の最大のテーブル|DBPROP_MAXTABLESINSELECT|
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
|Persist Security Info|DBPROP_AUTH_PERSIST_SENSITIVE_AUTHINFO|
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
|ブロック記憶域オブジェクト|DBPROP_BLOCKINGSTORAGEOBJECTS|
|ブックマークの種類|DBPROP_BOOKMARKTYPE|
|ブックマークを設定|DBPROP_IROWSETLOCATE|
|挿入行を変更します。|DBPROP_CHANGEINSERTEDROWS|
|列権限|DBPROP_COLUMNRESTRICT|
|列セットの通知|DBPROP_NOTIFYCOLUMNSET|
|コマンドのタイムアウト|DBPROP_COMMANDTIMEOUT|
|列を遅延します。|DBPROP_DEFERRED|
|記憶域オブジェクトの更新を遅延します。|DBPROP_DELAYSTORAGEOBJECTS|
|後方のフェッチします。|DBPROP_CANFETCHBACKWARDS|
|行を保持します。|DBPROP_CANHOLDROWS|
|IAccessor|DBPROP_IAccessor|
|IColumnsInfo|DBPROP_IColumnsInfo|
|IColumnsRowset|DBPROP_IColumnsRowset|
|IConnectionPointContainer|DBPROP_IConnectionPointContainer|
|IConvertType|DBPROP_IConvertType|
|移動不可の行|DBPROP_IMMOBILEROWS|
|IRowset|DBPROP_IRowset|
|IRowsetChange|DBPROP_IRowsetChange|
|IRowsetIdentity|DBPROP_IRowsetIdentity|
|IRowsetInfo|DBPROP_IRowsetInfo|
|IRowsetLocate|DBPROP_IRowsestLocate|
|IRowsetResynch||
|IRowsetScroll|DBPROP_IRowsetScroll|
|IRowsetUpdate|DBPROP_IRowsetUpdate|
|ISequentialStream|DBPROP_ISequentialStream|
|ISupportErrorInfo|DBPROP_ISupportErrorInfo|
|リテラルのブックマーク|DBPROP_LITERALBOOKMARKS|
|リテラルの行 Id を使用|DBPROP_LITERALIDENTITY|
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
|行セットのフェッチ位置の変更通知|DBPROP_NOTIFYROWSETFETCHPOSISIONCHANGE|
|行セットのリリースの通知|DBPROP_NOTIFYROWSETRELEASE|
|逆にスクロールします。|DBPROP_CANSCROLLBACKWARDS|
|サーバー カーソル|DBPROP_SERVERCURSOR|
|Skip は、ブックマークを削除します。|DBPROP_BOOKMARKSKIPPED|
|厳密な行 Id を使用|DBPROP_STRONGITDENTITY|
|一意の行|DBPROP_UNIQUEROWS|
|更新機能|DBPROP_UPDATABILITY|
|ブックマークを使用します。|DBPROP_BOOKMARKS|

## <a name="command-dynamic-properties"></a>コマンドの動的プロパティ
 次のプロパティを追加、**プロパティ**のコレクション、**コマンド**オブジェクト。

|ADO プロパティ名|OLE DB プロパティの名前|
|-----------------------|--------------------------|
|アクセスの順序|DBPROP_ACCESSORDER|
|基本パス|SSPROP_STREAM_BASEPATH|
|ブロック記憶域オブジェクト|DBPROP_BLOCKINGSTORAGEOBJECTS|
|ブックマークの種類|DBPROP_BOOKMARKTYPE|
|ブックマークを設定|DBPROP_IROWSETLOCATE|
|挿入行を変更します。|DBPROP_CHANGEINSERTEDROWS|
|列権限|DBPROP_COLUMNRESTRICT|
|列セットの通知|DBPROP_NOTIFYCOLUMNSET|
|コンテンツの種類|SSPROP_STREAM_CONTENTTYPE|
|カーソル自動のフェッチ|SSPROP_CURSORAUTOFETCH|
|列を遅延します。|DBPROP_DEFERRED|
|準備コマンドの遅延送信|SSPROP_DEFERPREPARE|
|記憶域オブジェクトの更新を遅延します。|DBPROP_DELAYSTORAGEOBJECTS|
|後方のフェッチします。|DBPROP_CANFETCHBACKWARDS|
|行を保持します。|DBPROP_CANHOLDROWS|
|IAccessor|DBPROP_IAccessor|
|IColumnsInfo|DBPROP_IColumnsInfo|
|IColumnsRowset|DBPROP_IColumnsRowset|
|IConnectionPointContainer|DBPROP_IConnectionPointContainer|
|IConvertType|DBPROP_IConvertType|
|移動不可の行|DBPROP_IMMOBILEROWS|
|IRowset|DBPROP_IRowset|
|IRowsetChange|DBPROP_IRowsetChange|
|IRowsetIdentity|DBPROP_IRowsetIdentity|
|IRowsetInfo|DBPROP_IRowsetInfo|
|IRowsetLocate|DBPROP_IRowsetLocate|
|IRowsetResynch|DBPROP_IRowsetResynch|
|IRowsetScroll|DBPROP_IRowsetScroll|
|IRowsetUpdate|DBPROP_IRowsetUpdate|
|ISequentialStream|DBPROP_ISequentialStream|
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
|出力の Encoding プロパティ|DBPROP_OUTPUTENCODING|
|出力ストリームのプロパティ|DBPROP_OUTPUTSTREAM|
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
|サーバー カーソル|DBPROP_SERVERCURSOR|
|挿入時のサーバー データ|DBPROP_SERVERDATAONINSERT|
|Skip は、ブックマークを削除します。|DBPROP_BOOKMARKSKIP|
|厳密な行 Id を使用|DBPROP_STRONGIDENTITY|
|更新機能|DBPROP_UPDATABILITY|
|ブックマークを使用します。|DBPROP_BOOKMARKS|
|XML のルート|SSPROP_STREAM_XMLROOT|
|XSL (XSL)|SSPROP_STREAM_XSL|

 特定の実装の詳細と、Microsoft SQL Server OLE DB プロバイダーの機能については、次を参照してください。、 [SQL Server プロバイダー](http://msdn.microsoft.com/en-us/adf1d6c4-5930-444a-9248-ff1979729635)です。

## <a name="see-also"></a>参照
 [ConnectionString プロパティ (ADO)](../../../ado/reference/ado-api/connectionstring-property-ado.md) [プロバイダー プロパティ (ADO)](../../../ado/reference/ado-api/provider-property-ado.md) [Recordset オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
