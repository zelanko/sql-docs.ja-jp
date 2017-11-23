---
title: "Microsoft OLE DB Provider for Microsoft インテックス サービス |Microsoft ドキュメント"
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
- Indexing Service provider [ADO]
- providers [ADO], OLE DB provider for Microsoft Indexing service
- OLE DB provider for Microsoft Indexing service [ADO]
ms.assetid: f86a0598-5097-471b-8318-d2c859d085f2
caps.latest.revision: "15"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7d0fb1ffdfdd73562aaa5b64ce997e857ae9f213
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="microsoft-ole-db-provider-for-microsoft-indexing-service-overview"></a>Microsoft OLE DB Provider for Microsoft インデックス作成サービスの概要
Microsoft OLE DB Provider for Microsoft インテックス サービスは、ファイル システムと Microsoft Indexing Service でインデックス付けされた Web データにプログラムでの読み取り専用アクセスを提供します。 ADO アプリケーションでは、コンテンツとファイルのプロパティ情報を取得する SQL クエリを発行できます。

 プロバイダーは、フリー スレッドは、UNICODE に対応します。

## <a name="connection-string-parameters"></a>接続文字列パラメーター
 このプロバイダーに接続するには、設定、**プロバイダー =**への引数、 [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md)プロパティ。

```
MSIDXS
```

 読み取り、[プロバイダー](../../../ado/reference/ado-api/provider-property-ado.md)プロパティは同様に、この文字列を返します。

## <a name="typical-connection-string"></a>一般的な接続文字列
 このプロバイダーの一般的な接続文字列とは。

```
"Provider=MSIDXS;Data Source=myCatalog;Locale Identifier=nnnn;"
```

 文字列は、これらのキーワードで構成されます。

|Keyword|Description|
|-------------|-----------------|
|**プロバイダー**|Microsoft インテックス サービス用の OLE DB プロバイダーを指定します。 通常これは、接続文字列で指定された唯一のキーワードです。|
|**[データ ソース]**|インデックス サービス カタログ名を指定します。 このキーワードが指定されていない場合は、既定のシステム カタログが使用されます。|
|**[Locale Identifier]**|32 ビットの一意の番号 (1033 など)、ユーザーの言語に関連する設定を指定するを指定します。 このキーワードが指定されていない、既定のシステムのロケール識別子が使用されます。|

## <a name="command-text"></a>コマンド テキスト
 インデックス作成サービスの SQL クエリ構文では、SQL 92 に拡張機能の**選択**ステートメントとその**FROM**と**場所**句。 ADO で使用およびとして操作可能な OLE DB 行セットを使用して、クエリの結果が返されます[Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクト。

 正確な単語や語句を検索したり、ワイルドカード パターンや単語の語幹検索を使用できます。 検索ロジックは、ブール型の決定、重み付け語句は、またはその他の語に近接に基づいて作成できます。 また、「フリー テキスト」一致する語句ではなく、意味のものによって検索することができます。

 特定のコマンド構文は、インデックス サービスに関するドキュメントのクエリ言語で完全に記載されています。

 プロバイダーはストアド プロシージャの呼び出しまたは単純なテーブル名を受け付けません (たとえば、 [CommandType](../../../ado/reference/ado-api/commandtype-property-ado.md)プロパティが必ず**adCmdText**)。

## <a name="recordset-behavior"></a>レコード セットの動作
 次の表で使用できる機能の一覧、**レコード セット**オブジェクトをこのプロバイダーに開きます。 静的カーソルの種類のみ (**adOpenStatic**) は使用できます。

 詳細については**レコード セット**実行、プロバイダーの構成の動作、[サポート](../../../ado/reference/ado-api/supports-method.md)メソッドを列挙し、[プロパティ](../../../ado/reference/ado-api/properties-collection-ado.md)のコレクション、**Recordset**をプロバイダーに固有の動的なプロパティが存在するかどうかを判断します。

 **標準の ADO レコード セットのプロパティの可用性:**

|プロパティ|可用性|
|--------------|------------------|
|[AbsolutePage](../../../ado/reference/ado-api/absolutepage-property-ado.md)|読み取り/書き込み|
|[AbsolutePosition](../../../ado/reference/ado-api/absoluteposition-property-ado.md)|読み取り/書き込み|
|[ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md)|読み取り専用|
|[BOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md)|読み取り専用|
|[ブックマーク](../../../ado/reference/ado-api/bookmark-property-ado.md)*|読み取り/書き込み|
|[CacheSize](../../../ado/reference/ado-api/cachesize-property-ado.md)|読み取り/書き込み|
|[CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md)|常に**adUseServer**|
|[カーソル。](../../../ado/reference/ado-api/cursortype-property-ado.md)|常に**adOpenStatic**|
|[EditMode](../../../ado/reference/ado-api/editmode-property.md)|常に**adEditNone**|
|[EOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md)|読み取り専用|
|[Assert](../../../ado/reference/ado-api/filter-property.md)|読み取り/書き込み|
|[ロック。](../../../ado/reference/ado-api/locktype-property-ado.md)|読み取り/書き込み|
|[スレッド](../../../ado/reference/ado-api/marshaloptions-property-ado.md)|使用不可|
|[MaxRecords](../../../ado/reference/ado-api/maxrecords-property-ado.md)|読み取り/書き込み|
|[PageCount](../../../ado/reference/ado-api/pagecount-property-ado.md)|読み取り専用|
|[PageSize](../../../ado/reference/ado-api/pagesize-property-ado.md)|読み取り/書き込み|
|[RecordCount](../../../ado/reference/ado-api/recordcount-property-ado.md)|読み取り専用|
|[ソース](../../../ado/reference/ado-api/source-property-ado-recordset.md)|読み取り/書き込み|
|[状態](../../../ado/reference/ado-api/state-property-ado.md)|読み取り専用|
|[[状態]](../../../ado/reference/ado-api/status-property-ado-recordset.md)|読み取り専用|

 \*この機能の順序で上に存在するプロバイダーのブックマークを有効にする必要があります、 **Recordset**です。

 **標準の ADO レコード セット メソッドの可用性:**

|方法|使用できるか。|
|------------|----------------|
|[AddNew](../../../ado/reference/ado-api/addnew-method-ado.md)|不可|
|[キャンセル](../../../ado/reference/ado-api/cancel-method-ado.md)|可|
|[CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md)|不可|
|[ただし](../../../ado/reference/ado-api/cancelupdate-method-ado.md)|不可|
|[複製](../../../ado/reference/ado-api/clone-method-ado.md)|可|
|[[閉じる]](../../../ado/reference/ado-api/close-method-ado.md)|可|
|[Del](../../../ado/reference/ado-api/delete-method-ado-recordset.md)|不可|
|[GetRows](../../../ado/reference/ado-api/getrows-method-ado.md)|可|
|[[移動]](../../../ado/reference/ado-api/move-method-ado.md)|可|
|[MoveFirst](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)|可|
|[NextRecordset](../../../ado/reference/ado-api/nextrecordset-method-ado.md)|可|
|[開く](../../../ado/reference/ado-api/open-method-ado-recordset.md)|可|
|[クエリを再実行します。](../../../ado/reference/ado-api/requery-method.md)|可|
|[再同期](../../../ado/reference/ado-api/resync-method.md)|可|
|[サポートしています](../../../ado/reference/ado-api/supports-method.md)|可|
|[Update](../../../ado/reference/ado-api/update-method.md)|不可|
|[UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)|不可|

 特定の実装の詳細と Microsoft インテックス サービスの機能について、Microsoft OLE DB プロバイダーを参照してください、 [OLE DB プログラマ ガイド](https://msdn.microsoft.com/library/windows/desktop/ms713643.aspx)、または Windows NT Server Web のサービスの Web ページを参照してくださいサイトです。

## <a name="see-also"></a>参照
 [CommandType プロパティ (ADO)](../../../ado/reference/ado-api/commandtype-property-ado.md) [ConnectionString プロパティ (ADO)](../../../ado/reference/ado-api/connectionstring-property-ado.md) [プロパティのコレクション (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md) [プロバイダー プロパティ (ADO)](../../../ado/reference/ado-api/provider-property-ado.md) [レコード セット オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md) [メソッドをサポートしています](../../../ado/reference/ado-api/supports-method.md)
