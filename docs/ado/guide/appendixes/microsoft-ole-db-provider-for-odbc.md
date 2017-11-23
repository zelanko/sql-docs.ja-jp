---
title: "Microsoft OLE DB Provider for ODBC |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: guide
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- OLE DB provider for ODBC [ADO]
- providers [ADO], OLE DB provider for ODBC
ms.assetid: 2dc0372d-e74d-4d0f-9c8c-04e5a168c148
caps.latest.revision: "16"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 2b7fe46a54848d16b94919be4ee2ce8987ba167b
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="microsoft-ole-db-provider-for-odbc-overview"></a>Microsoft OLE DB Provider for ODBC の概要
ADO または RDS プログラマでは、理想的な世界がいずれかですべてのデータ ソースは、OLE DB インターフェイスを公開する ADO は、データ ソースに直接呼び出すことができるようにします。 ますます多くのデータベース ベンダーは、OLE DB インターフェイスを実装するは、一部のデータ ソースはこの方法はまだ公開されません。 ただし、現在使用しているほとんどの DBMS システムは、ODBC を通じてアクセスできます。

 ODBC ドライバーでは、Oracle などの Microsoft 以外のデータベース製品に加え、Microsoft SQL Server、Microsoft Access (Jet データベース エンジン) および Microsoft FoxPro を含む現在、使用している各主要な DBMS 利用できます。

 ただし、により、Microsoft ODBC プロバイダーを使用すると、ADO では、ODBC データ ソースに接続します。 プロバイダーは、フリー スレッドは、Unicode に対応します。

 プロバイダーは、トランザクションをサポートする DBMS エンジンの種類がさまざまな種類のトランザクションのサポートを提供します。 たとえば、Microsoft Access では、5 レベルの深さまで入れ子になったトランザクションをサポートしています。

 これは、ADO の既定のプロバイダーと、すべてのプロバイダーに依存する ADO プロパティとメソッドがサポートされます。

## <a name="connection-string-parameters"></a>接続文字列パラメーター
 このプロバイダーに接続するには、設定、**プロバイダー =**の引数、 [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md)プロパティ。

```
MSDASQL
```

 読み取り、[プロバイダー](../../../ado/reference/ado-api/provider-property-ado.md)プロパティは同様に、この文字列を返します。

## <a name="typical-connection-string"></a>一般的な接続文字列
 このプロバイダーの一般的な接続文字列とは。

```
"Provider=MSDASQL;DSN=dsnName;UID=MyUserID;PWD=MyPassword;"
```

 文字列は、これらのキーワードで構成されます。

|Keyword|Description|
|-------------|-----------------|
|**プロバイダー**|OLE DB provider for ODBC を指定します。|
|**DSN**|データ ソース名を指定します。|
|**UID**|ユーザー名を指定します。|
|**PWD**|ユーザーのパスワードを指定します。|
|**[URL]**|ファイルまたは Web フォルダーに発行されるディレクトリの URL を指定します。|

 省略した場合、ADO の既定のプロバイダーは、このため、**プロバイダー =** ADO 接続文字列からのパラメーターは、このプロバイダーへの接続を確立するために試行されます。

> [!NOTE]
>  Windows 認証をサポートするデータ ソース プロバイダーに接続するかどうかは、する必要がありますを指定する**Trusted_Connection = [はい]**または**Integrated Security = SSPI**ユーザー ID とパスワードの代わりに接続文字列の情報です。

 プロバイダーは、ADO で定義されているだけでなく特定の接続パラメーターをサポートしていません。 ただし、プロバイダーは、ODBC ドライバー マネージャーに、ADO 以外の接続パラメーターを渡します。

 省略することができますので、**プロバイダー**パラメーター、ADO 接続文字列を同じデータ ソースの ODBC 接続文字列と同じであるため組み込むことができます。 同じパラメーター名を使用して (**ドライバー =**、**データベース =**、 **DSN =**など)、値、および同様の構文は、ODBC 接続文字列を作成するときにします。 定義済みのデータ ソース名 (DSN) または FileDSN の有無を接続することができます。

## <a name="syntax-with-a-dsn-or-filedsn"></a>DSN、FileDSN の構文:

```
"[Provider=MSDASQL;] { DSN=name | FileDSN=filename } ;
[DATABASE=database;] UID=user; PWD=password"
```

## <a name="syntax-without-a-dsn-dsn-less-connection"></a>DSN (dsn-less connection) を使用しない構文:

```
"[Provider=MSDASQL;] DRIVER=driver; SERVER=server;
DATABASE=database; UID=MyUserID; PWD=MyPassword"
```

## <a name="remarks"></a>解説
 使用する場合、 **DSN**または**FileDSN**、Windows コントロール パネルの ODBC データ ソース アドミニストレーターを定義する必要があります。 Microsoft Windows 2000 では、[管理ツール]、ODBC アドミニストレーターがあります。 Windows の以前のバージョンでは、という名前の ODBC アドミニストレーター アイコン**32 ビット ODBC**または**ODBC**です。

 設定する代わりに、 **DSN**、ODBC ドライバーを指定できます (**ドライバー =**)、"SQL Server;"など、サーバー名 (**サーバー =**); とデータベース名 (**データベース =**)。

 ユーザー アカウント名を指定することも (**UID =**)、およびユーザー アカウントのパスワード (**PWD =**) や、標準 ODBC に固有のパラメーターで ADO 定義*ユーザー*と*パスワード*パラメーター。

 **DSN**定義は既にデータベースを指定してを指定できます*、* *データベース*パラメーターに加え、 **DSN**接続するにはデータベースを変更します。 常に含めることをお勧め*、* *データベース*パラメーターを使用するときに、 **DSN**です。 これにより別のユーザーは、確認した後に既定のデータベース パラメーターを変更した場合、適切なデータベースに接続するよう、 **DSN**定義します。

## <a name="provider-specific-connection-properties"></a>プロバイダー固有の接続プロパティ
 OLE DB provider for ODBC をいくつかのプロパティの追加、[プロパティ](../../../ado/reference/ado-api/properties-collection-ado.md)のコレクション、**接続**オブジェクト。 次の表は、かっこ内に対応する OLE DB プロパティ名でこれらのプロパティを一覧表示します。

|プロパティ名|Description|
|-------------------|-----------------|
|アクセス可能な手順 (KAGPROP_ACCESSIBLEPROCEDURES)|ユーザーがストアド プロシージャへのアクセスを持つかどうかを示します。|
|アクセス可能なテーブル (KAGPROP_ACCESSIBLETABLES)|ユーザーがデータベースのテーブルに対して SELECT ステートメントを実行する権限を持っているかどうかを示します。|
|アクティブなステートメント (KAGPROP_ACTIVESTATEMENTS)|ODBC ドライバーは接続でサポートできるハンドルの数を示します。|
|ドライバー名 (KAGPROP_DRIVERNAME)|ODBC ドライバーのファイル名を示します。|
|ドライバーの ODBC バージョン (KAGPROP_DRIVERODBCVER)|このドライバーをサポートする ODBC のバージョンを示します。|
|ファイルの使用状況 (KAGPROP_FILEUSAGE)|ドライバーがデータ ソース内のファイルを処理する方法を示しますテーブル、またはカタログとして。|
|Like エスケープ句 (KAGPROP_LIKEESCAPECLAUSE)|WHERE 句の LIKE 述語で下線文字 (_) をパーセント文字 (%) に、ドライバーが定義とエスケープ文字の使用をサポートするかどうかを示します。|
|(KAGPROP_MAXCOLUMNSINGROUPBY) によるグループ内の最大列|SELECT ステートメントの GROUP BY 句に指定できる列の最大数を示します。|
|最大インデックス内の列 (KAGPROP_MAXCOLUMNSININDEX)|インデックスに含めることができる列の最大数を示します。|
|(KAGPROP_MAXCOLUMNSINORDERBY) 順での最大列|SELECT ステートメントの ORDER BY 句に指定できる列の最大数を示します。|
|選択 (KAGPROP_MAXCOLUMNSINSELECT) で最大の列|SELECT ステートメントの SELECT 部分に指定できる列の最大数を示します。|
|テーブル (KAGPROP_MAXCOLUMNSINTABLE) の最大列|テーブルで許可されている列の最大数を示します。|
|数値関数 (KAGPROP_NUMERICFUNCTIONS)|数値関数は、ODBC ドライバーでサポートされることを示します。 関数名とこのビットマスクで使用する関連付けられている値の一覧については、次を参照してください。[付録 e: のスカラー関数](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md)、ODBC のドキュメントにします。|
|外部結合機能 (KAGPROP_OJCAPABILITY)|プロバイダーでサポートされている外部結合の種類を示します。|
|外部結合 (KAGPROP_OUTERJOINS)|プロバイダーは外部結合をサポートするかどうかを示します。|
|特殊文字 (KAGPROP_SPECIALCHARACTERS)|ODBC ドライバーの特別な意味を持つ文字を示します。|
|ストアド プロシージャ (KAGPROP_PROCEDURES)|ストアド プロシージャは、この ODBC ドライバーで使用できるかどうかを示します。|
|文字列関数 (KAGPROP_STRINGFUNCTIONS)|文字列関数は、ODBC ドライバーでサポートされることを示します。 関数名とこのビットマスクで使用する関連付けられている値の一覧については、次を参照してください。[付録 e: のスカラー関数](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md)、ODBC のドキュメントにします。|
|システム関数 (KAGPROP_SYSTEMFUNCTIONS)|システム関数は、ODBC ドライバーでサポートされることを示します。 関数名とこのビットマスクで使用する関連付けられている値の一覧については、次を参照してください。[付録 e: のスカラー関数](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md)、ODBC のドキュメントにします。|
|日付/時刻関数 (KAGPROP_TIMEDATEFUNCTIONS)|ODBC ドライバーでどの日付と時刻の関数がサポートされていることを示します。 関数名とこのビットマスクで使用する関連付けられている値の一覧については、次を参照してください。[付録 e: のスカラー関数](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md)、ODBC のドキュメントにします。|
|SQL の文法のサポート (KAGPROP_ODBCSQLCONFORMANCE)|ODBC ドライバーがサポートする SQL 文法を示します。|

## <a name="provider-specific-recordset-and-command-properties"></a>プロバイダー固有のレコード セットとコマンドのプロパティ
 OLE DB provider for ODBC をいくつかのプロパティの追加、**プロパティ**のコレクション、 **Recordset**と**コマンド**オブジェクト。 次の表は、かっこ内に対応する OLE DB プロパティ名でこれらのプロパティを一覧表示します。

|プロパティ名|Description|
|-------------------|-----------------|
|クエリ ベースの更新/削除/挿入 (KAGPROP_QUERYBASEDUPDATES)|SQL クエリを使用して、更新、削除、および挿入を実行することができるかどうかを示します。|
|ODBC の同時実行の種類 (KAGPROP_CONCURRENCY)|データ ソースから、同じデータを同時にアクセスしようとしています。 2 つのユーザーによる潜在的な問題を減らすために使用する方法を示します。|
|順方向専用カーソル (KAGPROP_BLOBSONFOCURSOR) で BLOB のユーザー補助|示すかどうかの BLOB**フィールド**順方向専用カーソルを使用する場合にアクセスできます。|
|QBU WHERE 句 (KAGPROP_INCLUDENONEXACT) では、使用できます、SQL_DOUBLE、および SQL_REAL|QBU WHERE 句で使用できます、SQL_DOUBLE、SQL_REAL の値を含めることがあるかどうかを示します。|
|挿入 (KAGPROP_POSITIONONNEWROW) 後の最後の行の位置|テーブルに新しいレコードが挿入された、テーブルの最後の行があることを示します、現在の行を取得します。|
|IRowsetChangeExtInfo (KAGPROP_IROWSETCHANGEEXTINFO)|示すかどうか、 **IRowsetChange**インターフェイスが拡張情報のサポートを提供します。|
|ODBC カーソルの種類 (KAGPROP_CURSOR)|によって使用されるカーソルの種類を示す、 **Recordset**です。|
|マーシャ リングできる行セットを生成 (KAGPROP_MARSHALLABLE)|ODBC ドライバーがマーシャ リングできるレコード セットを生成することを示します|

## <a name="command-text"></a>コマンド テキスト
 使用する方法、[コマンド](../../../ado/reference/ado-api/command-object-ado.md)オブジェクトは、データ ソースに大きく左右し、クエリまたはコマンドのステートメントの種類を受け入れます。

 ODBC は、ストアド プロシージャを呼び出すための特定の構文を提供します。 [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md)のプロパティ、**コマンド**オブジェクト、 *CommandText*への引数、 **Execute**メソッドを[接続](../../../ado/reference/ado-api/connection-object-ado.md)オブジェクト、または*ソース*への引数、**開いている**メソッドを[レコード セット](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクト、この構文を使用して文字列に渡します。

```
"{ [ ? = ] call procedure [ ( ? [, ? [ , … ]] ) ] }"
```

 各**しますか?** 内のオブジェクトを参照して、[パラメーター](../../../ado/reference/ado-api/parameters-collection-ado.md)コレクション。 最初の**しますか?** 参照**パラメーター**(0)、次へ**しますか?** 参照**パラメーター**(1) などです。

 パラメーターの参照はオプションであり、ストアド プロシージャの構造に依存します。 パラメーターを定義していないストアド プロシージャを呼び出す場合は、文字列は、次のようになります。

```
"{ call procedure }"
```

 2 つのクエリ パラメーターがあれば、文字列は、次のようになります。

```
"{ call procedure ( ?, ? ) }"
```

 ストアド プロシージャは値を返す場合、戻り値は、別のパラメーターとして扱われます。 クエリ パラメーターはありませんが、戻り値が場合、文字列は、次のようになります。

```
"{ ? = call procedure }"
```

 最後に、戻り値があり、クエリ パラメーターを 2 つの場合は、文字列は、次のようになります。

```
"{ ? = call procedure ( ?, ? ) }"
```

## <a name="recordset-behavior"></a>レコード セットの動作
 次の表は、標準の ADO メソッドおよびプロパティで使用できる、**レコード セット**オブジェクトをこのプロバイダーに開きます。

 詳細については**レコード セット**実行、プロバイダーの構成の動作、[サポート](../../../ado/reference/ado-api/supports-method.md)メソッドを列挙し、**プロパティ**のコレクション、**Recordset**をプロバイダーに固有の動的なプロパティが存在するかどうかを判断します。

 標準の ADO の可用性**Recordset**プロパティ。

|プロパティ|ForwardOnly|動的|Keyset|静的|
|--------------|-----------------|-------------|------------|------------|
|[AbsolutePage](../../../ado/reference/ado-api/absolutepage-property-ado.md)|使用不可|使用不可|読み取り/書き込み|読み取り/書き込み|
|[AbsolutePosition](../../../ado/reference/ado-api/absoluteposition-property-ado.md)|使用不可|使用不可|読み取り/書き込み|読み取り/書き込み|
|[ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md)|読み取り/書き込み|読み取り/書き込み|読み取り/書き込み|読み取り/書き込み|
|[BOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md)|読み取り専用|読み取り専用|読み取り専用|読み取り専用|
|[ブックマーク](../../../ado/reference/ado-api/bookmark-property-ado.md)|使用不可|使用不可|読み取り/書き込み|読み取り/書き込み|
|[CacheSize](../../../ado/reference/ado-api/cachesize-property-ado.md)|読み取り/書き込み|読み取り/書き込み|読み取り/書き込み|読み取り/書き込み|
|[CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md)|読み取り/書き込み|読み取り/書き込み|読み取り/書き込み|読み取り/書き込み|
|[カーソル。](../../../ado/reference/ado-api/cursortype-property-ado.md)|読み取り/書き込み|読み取り/書き込み|読み取り/書き込み|読み取り/書き込み|
|[EditMode](../../../ado/reference/ado-api/editmode-property.md)|読み取り専用|読み取り専用|読み取り専用|読み取り専用|
|[Assert](../../../ado/reference/ado-api/filter-property.md)|読み取り/書き込み|読み取り/書き込み|読み取り/書き込み|読み取り/書き込み|
|[ロック。](../../../ado/reference/ado-api/locktype-property-ado.md)|読み取り/書き込み|読み取り/書き込み|読み取り/書き込み|読み取り/書き込み|
|[スレッド](../../../ado/reference/ado-api/marshaloptions-property-ado.md)|読み取り/書き込み|読み取り/書き込み|読み取り/書き込み|読み取り/書き込み|
|[MaxRecords](../../../ado/reference/ado-api/maxrecords-property-ado.md)|読み取り/書き込み|読み取り/書き込み|読み取り/書き込み|読み取り/書き込み|
|[PageCount](../../../ado/reference/ado-api/pagecount-property-ado.md)|読み取り/書き込み|使用不可|読み取り専用|読み取り専用|
|[PageSize](../../../ado/reference/ado-api/pagesize-property-ado.md)|読み取り/書き込み|読み取り/書き込み|読み取り/書き込み|読み取り/書き込み|
|[RecordCount](../../../ado/reference/ado-api/recordcount-property-ado.md)|読み取り/書き込み|使用不可|読み取り専用|読み取り専用|
|[ソース](../../../ado/reference/ado-api/source-property-ado-recordset.md)|読み取り/書き込み|読み取り/書き込み|読み取り/書き込み|読み取り/書き込み|
|[状態](../../../ado/reference/ado-api/state-property-ado.md)|読み取り専用|読み取り専用|読み取り専用|読み取り専用|
|[[状態]](../../../ado/reference/ado-api/status-property-ado-recordset.md)|読み取り専用|読み取り専用|読み取り専用|読み取り専用|

 [AbsolutePosition](../../../ado/reference/ado-api/absoluteposition-property-ado.md)と[と、AbsolutePage](../../../ado/reference/ado-api/absolutepage-property-ado.md) ODBC 用の Microsoft OLE DB プロバイダーのバージョン 1.0 と ADO を使用する場合のプロパティは書き込み専用です。

 標準の ADO の可用性**Recordset**メソッド。

|方法|ForwardOnly|動的|Keyset|静的|
|------------|-----------------|-------------|------------|------------|
|[AddNew](../../../ado/reference/ado-api/addnew-method-ado.md)|可|可|可|可|
|[キャンセル](../../../ado/reference/ado-api/cancel-method-ado.md)|可|可|可|可|
|[CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md)|可|可|可|可|
|[ただし](../../../ado/reference/ado-api/cancelupdate-method-ado.md)|可|可|可|可|
|[複製](../../../ado/reference/ado-api/clone-method-ado.md)|不可|いいえ|はい|可|
|[[閉じる]](../../../ado/reference/ado-api/close-method-ado.md)|可|可|可|可|
|[Del](../../../ado/reference/ado-api/delete-method-ado-recordset.md)|可|可|可|可|
|[GetRows](../../../ado/reference/ado-api/getrows-method-ado.md)|可|可|可|可|
|[[移動]](../../../ado/reference/ado-api/move-method-ado.md)|可|可|可|可|
|[MoveFirst](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)|可|可|可|可|
|[MoveLast](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)|不可|はい|可|可|
|[MoveNext](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)|可|可|可|可|
|[MovePrevious](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)|不可|はい|可|可|
|[NextRecordset](../../../ado/reference/ado-api/nextrecordset-method-ado.md)*|可|可|可|可|
|[開く](../../../ado/reference/ado-api/open-method-ado-recordset.md)|可|可|可|可|
|[クエリを再実行します。](../../../ado/reference/ado-api/requery-method.md)|可|可|可|可|
|[再同期](../../../ado/reference/ado-api/resync-method.md)|不可|いいえ|はい|可|
|[サポートしています](../../../ado/reference/ado-api/supports-method.md)|可|可|可|可|
|[Update](../../../ado/reference/ado-api/update-method.md)|可|可|可|可|
|[UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)|可|可|可|可|

 * Microsoft Access データベースはサポートされていません。

## <a name="dynamic-properties"></a>動的プロパティ
 Microsoft OLE DB Provider for ODBC にいくつかの動的なプロパティを挿入する、**プロパティ**、開かれていないのコレクション[接続](../../../ado/reference/ado-api/connection-object-ado.md)、 [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)、および[コマンド](../../../ado/reference/ado-api/command-object-ado.md)オブジェクト。

 次の表は、各動的プロパティの ADO および OLE DB 名 cross-index です。 語を"Description"ADO プロパティ名を参照して、OLE DB プログラマーズ リファレンス OLE DB プログラマーズ リファレンスの詳細については、これらのプロパティを見つけることができます。 インデックスの OLE DB プロパティ名を検索するかを参照してください[付録 c: OLE DB プロパティ](http://msdn.microsoft.com/en-us/deded3ff-f508-4e1b-b2b1-fd9afd3bd292)です。

## <a name="connection-dynamic-properties"></a>接続の動的プロパティ
 次のプロパティを追加、**接続**オブジェクトの**プロパティ**コレクション。

|ADO プロパティ名|OLE DB プロパティの名前|
|-----------------------|--------------------------|
|Active sessions|DBPROP_ACTIVESESSIONS|
|非同期中止|DBPROP_ASYNCTXNABORT|
|非同期のコミット|DBPROP_ASYNCTNXCOMMIT|
|自動コミットの分離レベル|DBPROP_SESS_AUTOCOMMITISOLEVELS|
|カタログの場所|DBPROP_CATALOGLOCATION と|
|カタログの用語|DBPROP_CATALOGTERM と|
|列の定義|DBPROP_COLUMNDEFINITION と|
|Connect Timeout|DBPROP_INIT_TIMEOUT|
|現在のカタログ|DBPROP_CURRENTCATALOG|
|[データ ソース]|DBPROP_INIT_DATASOURCE|
|Data Source Name|開か|
|データ ソース オブジェクト スレッド モデル|DBPROP_DSOTHREADMODEL|
|DBMS の名前|DBPROP_DBMSNAME と|
|DBMS のバージョン|DBPROP_DBMSVER と|
|Extended Properties|DBPROP_INIT_PROVIDERSTRING|
|グループ化のサポート|DBPROP_GROUPBY と|
|異なるテーブルのサポート|DBPROP_HETEROGENEOUSTABLES と|
|識別子の大文字と小文字の区別|DBPROP_IDENTIFIERCASE|
|Initial Catalog|DBPROP_INIT_CATALOG|
|分離レベル|DBPROP_SUPPORTEDTXNISOLEVELS|
|分離保有期間|DBPROP_SUPPORTEDTXNISORETAIN と|
|[Locale Identifier]|DBPROP_INIT_LCID|
|場所|DBPROP_INIT_LOCATION|
|インデックスの最大サイズ|DBPROP_MAXINDEXSIZE と|
|行の最大サイズ|DBPROP_MAXROWSIZE と|
|最大行サイズには、BLOB が含まれています。|DBPROP_MAXROWSIZEINCLUDESBLOB と|
|SELECT の最大のテーブル|DBPROP_MAXTABLESINSELECT と|
|モード|DBPROP_INIT_MODE|
|複数のパラメーター セット|DBPROP_MULTIPLEPARAMSETS|
|複数の結果|DBPROP_MULTIPLERESULTS|
|複数のストレージ オブジェクト|DBPROP_MULTIPLESTORAGEOBJECTS|
|複数のテーブルの更新|DBPROP_MULTITABLEUPDATE と|
|NULL の照合順序|DBPROP_NULLCOLLATION と|
|NULL を連結した動作|DBPROP_CONCATNULLBEHAVIOR と|
|OLE DB サービス|DBPROP_INIT_OLEDBSERVICES|
|OLE DB バージョン|DBPROP_PROVIDEROLEDBVER|
|OLE オブジェクトのサポート|DBPROP_OLEOBJECTS|
|行セットのサポートを開く|DBPROP_OPENROWSETSUPPORT|
|選択リストの ORDER BY 列|DBPROP_ORDERBYCOLUMNSINSELECT と|
|出力パラメーターの使用状況|DBPROP_OUTPUTPARAMETERAVAILABILITY|
|Password|DBPROP_AUTH_PASSWORD|
|Ref アクセサーを使って渡す|DBPROP_BYREFACCESSORS|
|Persist Security Info|DBPROP_AUTH_PERSIST_SENSITIVE_AUTHINFO|
|永続的な ID 型|DBPROP_PERSISTENTIDTYPE と|
|中止の動作を準備します。|DBPROP_PREPAREABORTBEHAVIOR と|
|コミット動作を準備します。|DBPROP_PREPARECOMMITBEHAVIOR と|
|プロシージャの用語|DBPROP_PROCEDURETERM と|
|[プロンプト]|DBPROP_INIT_PROMPT|
|プロバイダーの表示名|DBPROP_PROVIDERFRIENDLYNAME|
|Provider Name|DBPROP_PROVIDERFILENAME|
|プロバイダーのバージョン|DBPROP_PROVIDERVER|
|読み取り専用のデータ ソース|DBPROP_DATASOURCEREADONLY と|
|行セットの変換|DBPROP_ROWSETCONVERSIONSONCOMMAND|
|スキーマの用語|DBPROP_SCHEMATERM|
|スキーマの使用|DBPROP_SCHEMAUSAGE と|
|SQL のサポート|DBPROP_SQLSUPPORT|
|構造化ストレージ|DBPROP_STRUCTUREDSTORAGE|
|サブクエリのサポート|DBPROP_SUBQUERIES と|
|テーブルの用語|DBPROP_TABLETERM と|
|トランザクション DDL|DBPROP_SUPPORTEDTXNDDL|
|[ユーザー ID]|DBPROP_AUTH_USERID|
|[ユーザー名]|DBPROP_USERNAME と|
|ウィンドウ ハンドル|DBPROP_INIT_HWND|

## <a name="recordset-dynamic-properties"></a>レコード セットの動的プロパティ
 次のプロパティを追加、 **Recordset**オブジェクトの**プロパティ**コレクション。

|ADO プロパティ名|OLE DB プロパティの名前|
|-----------------------|--------------------------|
|アクセスの順序|DBPROP_ACCESSORDER|
|ブロック記憶域オブジェクト|DBPROP_BLOCKINGSTORAGEOBJECTS|
|ブックマークの種類|DBPROP_BOOKMARKTYPE|
|ブックマークを設定|DBPROP_IROWSETLOCATE|
|挿入行を変更します。|DBPROP_CHANGEINSERTEDROWS|
|列権限|DBPROP_COLUMNRESTRICT|
|列セットの通知|DBPROP_NOTIFYCOLUMNSET|
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
|IRowsetResynch||
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
|一意の行|DBPROP_UNIQUEROWS|
|更新機能|DBPROP_UPDATABILITY|
|ブックマークを使用します。|DBPROP_BOOKMARKS|

## <a name="command-dynamic-properties"></a>コマンドの動的プロパティ
 次のプロパティを追加、**コマンド**オブジェクトの**プロパティ**コレクション。

|ADO プロパティ名|OLE DB プロパティの名前|
|-----------------------|--------------------------|
|アクセスの順序|DBPROP_ACCESSORDER|
|ブロック記憶域オブジェクト|DBPROP_BLOCKINGSTORAGEOBJECTS|
|ブックマークの種類|DBPROP_BOOKMARKTYPE|
|ブックマークを設定|DBPROP_IROWSETLOCATE|
|挿入行を変更します。|DBPROP_CHANGEINSERTEDROWS|
|列権限|DBPROP_COLUMNRESTRICT|
|列セットの通知|DBPROP_NOTIFYCOLUMNSET|
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
|IRowsetResynch||
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
|Skip は、ブックマークを削除します。|DBPROP_BOOKMARKSKIP|
|厳密な行 Id を使用|DBPROP_STRONGIDENTITY|
|更新機能|DBPROP_UPDATABILITY|
|ブックマークを使用します。|DBPROP_BOOKMARKS|

 詳細については、特定の実装と機能について、Microsoft OLE DB Provider for ODBC は、次を参照してください。、 [OLE DB プログラマーズ リファレンス](http://msdn.microsoft.com/en-us/3c5e2dd5-35e5-4a93-ac3a-3818bb43bbf8)または MSDN でデータ アクセスおよびストレージ デベロッパー センターの Web サイトを参照してください。

## <a name="see-also"></a>参照
 [コマンド オブジェクト (ADO)](../../../ado/reference/ado-api/command-object-ado.md) [CommandText プロパティ (ADO)](../../../ado/reference/ado-api/commandtext-property-ado.md) [接続オブジェクト (ADO)](../../../ado/reference/ado-api/connection-object-ado.md) [ConnectionString プロパティ (ADO)](../../../ado/reference/ado-api/connectionstring-property-ado.md) [実行メソッド (ADO コマンド)](../../../ado/reference/ado-api/execute-method-ado-command.md) [メソッド (ADO レコード セット) を開く](../../../ado/reference/ado-api/open-method-ado-recordset.md) [Parameters コレクション (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md) [プロパティのコレクション (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md) [プロバイダー プロパティ (ADO)](../../../ado/reference/ado-api/provider-property-ado.md) [Recordset オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md) [メソッドをサポートしています](../../../ado/reference/ado-api/supports-method.md)
