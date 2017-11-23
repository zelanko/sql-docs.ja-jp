---
title: "ADO の動的プロパティ インデックス |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: dynamic properties [ADO], index
ms.assetid: 80d389dd-46ef-459f-b0d4-6f712fc4f32d
caps.latest.revision: "15"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.openlocfilehash: f126cc040174725ded02bd320e54a76536c0d516
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="ado-dynamic-property-index"></a>ADO 動的プロパティのインデックス
データ プロバイダー、サービス プロバイダー、およびサービスのコンポーネントが動的なプロパティを追加できます、**プロパティ**、開かれていないのコレクション[接続](../../../ado/reference/ado-api/connection-object-ado.md)と[Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクト。 特定のプロバイダーは、これらのオブジェクトが開かれたときに、追加のプロパティを挿入も可能性があります。 これらのプロパティの一部は、「、 [ADO の動的プロパティ](../../../ado/reference/ado-api/ado-dynamic-properties.md)セクションです。 内の特定のプロバイダーの詳細に表示される、[付録 a: プロバイダー](../../../ado/guide/appendixes/appendix-a-providers.md)セクションです。  
  
 次の表は、ADO および OLE DB プロパティの名前を各標準的な OLE DB プロバイダー動的の cross-indexes です。 プロバイダーは、ここで表示されているより多くのプロパティを追加できます。 プロバイダー固有の動的プロパティに関する特定の情報をプロバイダーのドキュメントを参照してください。  
  
 「説明」という用語によって ADO プロパティ名を参照して、OLE DB プログラマーズ リファレンス これらの標準的なプロパティの詳細については、検索または内のインデックスを参照、 [OLE DB に関するドキュメント](https://msdn.microsoft.com/library/windows/desktop/ms722784.aspx)の OLE DB プロパティの名前を使用しています。  
  
## <a name="connection-dynamic-properties"></a>接続の動的プロパティ  
  
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
|Ref アクセサーを使って渡す|DBPROP_BYREFACCESSORS|  
|Password|DBPROP_AUTH_PASSWORD|  
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
 注意してください、**動的プロパティ**の**Recordset**オブジェクト (使用できなくなります) ときにスコープ外に移動して、**レコード セット**が閉じられます。  
  
|ADO プロパティ名|OLE DB プロパティの名前|  
|-----------------------|--------------------------|  
|IAccessor|DBPROP_IACCESSOR|  
|IChapteredRowset||  
|IColumnsInfo|DBPROP_ICOLUMNSINFO|  
|IColumnsRowset|DBPROP_ICOLUMNSROWSET|  
|IConnectionPointContainer|DBPROP_ICONNECTIONPOINTCONTAINER|  
|IConvertType||  
|ILockBytes|DBPROP_ILOCKBYTES|  
|IRowset|DBPROP_IROWSET|  
|IDBAsynchStatus|DBPROP_IDBASYNCHSTATUS|  
|IParentRowset||  
|IRowsetChange|DBPROP_IROWSETCHANGE|  
|IRowsetExactScroll||  
|IRowsetFind|DBPROP_IROWSETFIND|  
|IRowsetIdentity|DBPROP_IROWSETIDENTITY|  
|IRowsetInfo|DBPROP_IROWSETINFO|  
|IRowsetLocate|DBPROP_IROWSETLOCATE|  
|IRowsetRefresh|DBPROP_IROWSETREFRESH|  
|IRowsetResynch||  
|IRowsetScroll|DBPROP_IROWSETSCROLL|  
|IRowsetUpdate|DBPROP_IROWSETUPDATE|  
|IRowsetView|DBPROP_IROWSETVIEW|  
|IRowsetIndex|DBPROP_IROWSETINDEX|  
|ISequentialStream|DBPROP_ISEQUENTIALSTREAM|  
|IStorage|DBPROP_ISTORAGE|  
|IStream|DBPROP_ISTREAM|  
|ISupportErrorInfo|DBPROP_ISUPPORTERRORINFO|  
|アクセスの順序|DBPROP_ACCESSORDER|  
|追加専用の行セット|DBPROP_APPENDONLY|  
|非同期の行セットの処理|DBPROP_ROWSET_ASYNCH|  
|自動再計算|DBPROP_ADC_AUTORECALC|  
|バック グラウンド フェッチ サイズ|DBPROP_ASYNCHFETCHSIZE|  
|バックグラウンド スレッド優先順位|DBPROP_ASYNCHTHREADPRIORITY|  
|バッチ サイズ|DBPROP_ADC_BATCHSIZE|  
|ブロック記憶域オブジェクト|DBPROP_BLOCKINGSTORAGEOBJECTS|  
|ブックマークの種類|DBPROP_BOOKMARKTYPE|  
|ブックマークを設定|DBPROP_IROWSETLOCATE|  
|ブックマークの順序指定|DBPROP_ORDEREDBOOKMARKS|  
|子の行をキャッシュします。|DBPROP_ADC_CACHECHILDROWS|  
|キャッシュ列の遅延|DBPROP_CACHEDEFERRED|  
|挿入行を変更します。|DBPROP_CHANGEINSERTEDROWS|  
|列権限|DBPROP_COLUMNRESTRICT|  
|列セットの通知|DBPROP_NOTIFYCOLUMNSET|  
|書き込み可能な列|DBPROP_MAYWRITECOLUMN|  
|コマンドのタイムアウト|DBPROP_COMMANDTIMEOUT|  
|カーソル エンジンのバージョン|DBPROP_ADC_CEVER|  
|列を遅延します。|DBPROP_DEFERRED|  
|記憶域オブジェクトの更新を遅延します。|DBPROP_DELAYSTORAGEOBJECTS|  
|後方のフェッチします。|DBPROP_CANFETCHBACKWARDS|  
|フィルター操作|DBPROP_FILTERCOMPAREOPS|  
|検索操作|DBPROP_FINDCOMPAREOPS|  
|非表示の列 (数)|DBPROP_HIDDENCOLUMNS|  
|行を保持します。|DBPROP_CANHOLDROWS|  
|移動不可の行|DBPROP_IMMOBILEROWS|  
|最初のフェッチ サイズ|DBPROP_ASYNCHPREFETCHSIZE|  
|リテラルのブックマーク|DBPROP_LITERALBOOKMARKS|  
|リテラルの行 Id を使用|DBPROP_LITERALIDENTITY|  
|状態の変更を管理します。|DBPROP_ADC_MAINTAINCHANGESTATUS|  
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
|Private1||  
|クイック再起動|DBPROP_QUICKRESTART|  
|再入可能なイベント|DBPROP_REENTRANTEVENTS|  
|削除された行を削除します。|DBPROP_REMOVEDELETED|  
|複数の変更を報告します。|DBPROP_REPORTMULTIPLECHANGES|  
|名前の形状変更します。|DBPROP_ADC_RESHAPENAME|  
|コマンドを再同期します。|DBPROP_ADC_CUSTOMRESYNCH|  
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
|Skip は、ブックマークを削除します。|DBPROP_BOOKMARKSKIPPED|  
|厳密な行 Id を使用|DBPROP_STRONGIDENTITY|  
|固有のカタログ|DBPROP_ADC_UNIQUECATALOG|  
|一意の行|DBPROP_UNIQUEROWS|  
|一意なスキーマ|DBPROP_ADC_UNIQUESCHEMA|  
|一意テーブル|DBPROP_ADC_UNIQUETABLE|  
|更新機能|DBPROP_UPDATABILITY|  
|更新基準|DBPROP_ADC_UPDATECRITERIA|  
|更新プログラムの再同期|DBPROP_ADC_UPDATERESYNC|  
|ブックマークを使用します。|DBPROP_BOOKMARKS|