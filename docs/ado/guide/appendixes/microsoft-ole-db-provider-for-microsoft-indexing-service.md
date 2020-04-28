---
title: Microsoft OLE DB Provider for Microsoft インデックスサービス |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/08/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- Indexing Service provider [ADO]
- providers [ADO], OLE DB provider for Microsoft Indexing service
- OLE DB provider for Microsoft Indexing service [ADO]
ms.assetid: f86a0598-5097-471b-8318-d2c859d085f2
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a5a81514fd12117a9f43e2c33bf0cda579fb363d
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "67926663"
---
# <a name="microsoft-ole-db-provider-for-microsoft-indexing-service-overview"></a>Microsoft OLE DB Provider for Microsoft Indexing Service の概要
Microsoft OLE DB Provider for Microsoft Indexing Service は、Microsoft Indexing Service によってインデックス付けされたファイルシステムおよび Web データへのプログラムによる読み取り専用アクセスを提供します。 ADO アプリケーションは、SQL クエリを発行してコンテンツとファイルのプロパティ情報を取得できます。

 プロバイダーは、フリースレッドで、UNICODE が有効になっています。

## <a name="connection-string-parameters"></a>接続文字列パラメーター
 このプロバイダーに接続するには、 **provider =** 引数を[ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md)プロパティに設定します。

```vb
MSIDXS
```

 [プロバイダー](../../../ado/reference/ado-api/provider-property-ado.md)プロパティを読み取ると、この文字列も返されます。

## <a name="typical-connection-string"></a>一般的な接続文字列
 このプロバイダーの一般的な接続文字列は次のとおりです。

```vb
"Provider=MSIDXS;Data Source=myCatalog;Locale Identifier=nnnn;"
```

 文字列は、次のキーワードで構成されています。

|キーワード|説明|
|-------------|-----------------|
|**プロバイダー**|Microsoft インデックスサービスの OLE DB プロバイダーを指定します。 通常、これは接続文字列で指定されている唯一のキーワードです。|
|**データ ソース**|インデックスサービスのカタログ名を指定します。 このキーワードが指定されていない場合は、既定のシステムカタログが使用されます。|
|**[Locale Identifier]**|ユーザーの言語に関連する設定を指定する32ビットの一意の数値 (1033 など) を指定します。 このキーワードが指定されていない場合は、既定のシステムロケール識別子が使用されます。|

## <a name="command-text"></a>コマンド テキスト
 インデックス作成サービスの SQL クエリ構文は、SQL-92 **SELECT**ステートメントの拡張機能と、その**FROM**句および**WHERE**句によって構成されています。 クエリの結果は OLE DB 行セットを介して返されます。これは、ADO によって使用され、[レコードセット](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクトとして操作できます。

 単語や語句を検索したり、ワイルドカードを使用してパターンや単語の語幹を検索したりすることができます。 検索ロジックは、ブール値の決定、重み付けされた用語、または他の単語との距離に基づいて作成できます。 また、"自由なテキスト" で検索することもできます。これにより、正確な単語ではなく、意味に基づいて一致が検出されます。

 特定のコマンド言語の詳細については、インデックスサービスのドキュメントのクエリ言語に関するドキュメントを参照してください。

 プロバイダーは、ストアドプロシージャ呼び出しまたは単純なテーブル名を受け入れません (たとえば、 [CommandType](../../../ado/reference/ado-api/commandtype-property-ado.md)プロパティは常に**adcmdtext**になります)。

## <a name="recordset-behavior"></a>レコードセットの動作
 次の表は、このプロバイダーで開かれた**レコードセット**オブジェクトで使用できる機能を示しています。 静的カーソルの種類 (**Adopenstatic**) のみを使用できます。

 プロバイダー構成の**レコードセット**の動作の詳細については、[サポート](../../../ado/reference/ado-api/supports-method.md)メソッドを実行し、**レコードセット**の[properties](../../../ado/reference/ado-api/properties-collection-ado.md)コレクションを列挙して、プロバイダー固有の動的プロパティが存在するかどうかを判断します。

 **標準の ADO レコードセットプロパティの可用性:**

|プロパティ|可用性|
|--------------|------------------|
|[AbsolutePage](../../../ado/reference/ado-api/absolutepage-property-ado.md)|読み取り/書き込み|
|[AbsolutePosition](../../../ado/reference/ado-api/absoluteposition-property-ado.md)|読み取り/書き込み|
|[ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md)|読み取り専用|
|[BOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md)|読み取り専用|
|[ブックマーク](../../../ado/reference/ado-api/bookmark-property-ado.md)*|読み取り/書き込み|
|[CacheSize](../../../ado/reference/ado-api/cachesize-property-ado.md)|読み取り/書き込み|
|[CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md)|常に**Aduseserver**|
|[CursorType](../../../ado/reference/ado-api/cursortype-property-ado.md)|常に**Adopenstatic**|
|[EditMode](../../../ado/reference/ado-api/editmode-property.md)|常に**adEditNone**|
|[EOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md)|読み取り専用|
|[Assert](../../../ado/reference/ado-api/filter-property.md)|読み取り/書き込み|
|[LockType](../../../ado/reference/ado-api/locktype-property-ado.md)|読み取り/書き込み|
|[MarshalOptions](../../../ado/reference/ado-api/marshaloptions-property-ado.md)|利用不可|
|[数](../../../ado/reference/ado-api/maxrecords-property-ado.md)|読み取り/書き込み|
|[PageCount](../../../ado/reference/ado-api/pagecount-property-ado.md)|読み取り専用|
|[PageSize](../../../ado/reference/ado-api/pagesize-property-ado.md)|読み取り/書き込み|
|[RecordCount](../../../ado/reference/ado-api/recordcount-property-ado.md)|読み取り専用|
|[ソース](../../../ado/reference/ado-api/source-property-ado-recordset.md)|読み取り/書き込み|
|[状態](../../../ado/reference/ado-api/state-property-ado.md)|読み取り専用|
|[状態](../../../ado/reference/ado-api/status-property-ado-recordset.md)|読み取り専用|

 \*この機能が**レコードセット**に存在するためには、プロバイダーでブックマークを有効にする必要があります。

 **標準の ADO レコードセットメソッドの可用性:**

|メソッド|利用可能か|
|------------|----------------|
|[AddNew](../../../ado/reference/ado-api/addnew-method-ado.md)|いいえ|
|[キャンセル](../../../ado/reference/ado-api/cancel-method-ado.md)|はい|
|[CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md)|いいえ|
|[CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md)|いいえ|
|[複製](../../../ado/reference/ado-api/clone-method-ado.md)|はい|
|[閉じる](../../../ado/reference/ado-api/close-method-ado.md)|はい|
|[削除](../../../ado/reference/ado-api/delete-method-ado-recordset.md)|いいえ|
|[GetRows](../../../ado/reference/ado-api/getrows-method-ado.md)|はい|
|[合わせ](../../../ado/reference/ado-api/move-method-ado.md)|はい|
|[MoveFirst](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)|はい|
|[NextRecordset](../../../ado/reference/ado-api/nextrecordset-method-ado.md)|はい|
|[開く](../../../ado/reference/ado-api/open-method-ado-recordset.md)|はい|
|[Requery](../../../ado/reference/ado-api/requery-method.md)|はい|
|[再同期](../../../ado/reference/ado-api/resync-method.md)|はい|
|[サポート](../../../ado/reference/ado-api/supports-method.md)|はい|
|[Update](../../../ado/reference/ado-api/update-method.md)|いいえ|
|[UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)|いいえ|

 Microsoft OLE DB Provider for Microsoft Indexing Service に関する具体的な実装の詳細と機能については、『 [OLE DB プログラマーズガイド』](https://msdn.microsoft.com/library/windows/desktop/ms713643.aspx)を参照するか、Windows NT Server web サイトの web サービスに関するページを参照してください。

## <a name="see-also"></a>参照
 [CommandType property (ado](../../../ado/reference/ado-api/commandtype-property-ado.md) ) [CONNECTIONSTRING プロパティ (Ado)](../../../ado/reference/ado-api/connectionstring-property-ado.md) [Properties Collection (ADO](../../../ado/reference/ado-api/properties-collection-ado.md) ) [Provider PROPERTY (ado](../../../ado/reference/ado-api/provider-property-ado.md) ) [Recordset オブジェクト (ado)](../../../ado/reference/ado-api/recordset-object-ado.md)はメソッドを[サポート](../../../ado/reference/ado-api/supports-method.md)します
