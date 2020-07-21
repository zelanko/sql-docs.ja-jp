---
title: OLE DB カスタム プロパティ | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 13a82d41-dd7a-4708-bc84-4407a536c877
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5307d2507562a9a9957fb2bb7431248b4196954a
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "85431709"
---
# <a name="ole-db-custom-properties"></a>OLE DB カスタム プロパティ
  **変換元のカスタム プロパティ**  
  
 OLE DB ソースには、カスタム プロパティと、すべてのデータ フロー コンポーネントとの共通プロパティの両方があります。  
  
 次の表は、OLE DB ソースのカスタム プロパティを示しています。 すべてのプロパティは読み取り/書き込み可能です。  
  
|プロパティ名|データ型|説明|  
|-------------------|---------------|-----------------|  
|AccessMode|Integer|データベースへのアクセスに使用するモード。 使用できる値は、 **[行セットを開く**]、[**変数から行セットを開く**]、、[ `SQL Command` **変数からの SQL コマンド]** です。 既定値は **OpenRowset**です。|  
|AlwaysUseDefaultCodePage|Boolean|`DefaultCodePage` プロパティの値を各列に使用するか、または各列のロケールからコードページを派生するかを示す値。 このプロパティの既定値は `False` です。|  
|CommandTimeOut|Integer|コマンドのタイムアウトの秒数。値 0 は、タイムアウトしないことを表します。<br /><br /> 注:このプロパティは、**OLE DB ソース エディター**では使用できませんが、**詳細エディター**を使用して設定できます。|  
|DefaultCodePage|Integer|コード ページに関する情報をデータ ソースから取得できない場合に使用するコード ページ。|  
|OpenRowset|String|行セットを開くために使用するデータベース オブジェクトの名前。|  
|OpenRowsetVariable|String|行セットを開くために使用するデータベース オブジェクトの名前を格納する変数。|  
|ParameterMapping|String|SQL コマンド内のパラメーターから変数へのマッピング。|  
|SqlCommand|String|実行する SQL コマンド。|  
|SqlCommandVariable|String|実行する SQL コマンドを格納する変数。|  
  
 OLE DB ソースの出力および出力列には、カスタム プロパティがありません。  
  
 詳細については、「 [OLE DB ソース](ole-db-source.md)」を参照してください。  
  
 **変換先のカスタム プロパティ**  
  
 OLE DB 変換先には、カスタム プロパティと、すべてのデータ フロー コンポーネントとの共通プロパティの両方があります。  
  
 次の表は、OLE DB 変換先のカスタム プロパティを示しています。 すべてのプロパティは読み取り/書き込み可能です。  
  
> [!NOTE]  
>  ここに一覧で示されている FastLoad オプション (FastLoadKeepIdentity、FastLoadKeepNulls、および FastLoadOptions) は、Microsoft OLE DB Provider for SQL Server (SQLOLEDB) が実装する `IRowsetFastLoad` インターフェイスによって公開され、同様の名前が付けられたプロパティに対応します。 詳細については、MSDN ライブラリで、IRowsetFastLoad を検索してください。  
  
|プロパティ名|データ型|説明|  
|-------------------|---------------|-----------------|  
|AccessMode|Integer (列挙)|変換先が変換先となるデータベースにアクセスする方法を指定する値。<br /><br /> このプロパティの値は、次のいずれか 1 つです。<br /><br /> `OpenRowset`(0): テーブルまたはビューの名前を指定します。<br />`OpenRowset from Variable`(1): テーブルまたはビューの名前を含む変数の名前を指定します。<br />`OpenRowset Using Fastload`(3): テーブルまたはビューの名前を指定します。<br />`OpenRowset Using Fastload from Variable`(4): テーブルまたはビューの名前を含む変数の名前を指定します。<br />`SQL Command`(2): SQL ステートメントを指定します。|  
|AlwaysUseDefaultCodePage|Boolean|`DefaultCodePage` プロパティの値を各列に使用するか、または各列のロケールからコードページを派生するかを示す値。 このプロパティの既定値は `False` です。|  
|CommandTimeOut|Integer|SQL コマンドがタイムアウトになるまでの最大秒数。この値に 0 を指定すると、時間は無制限になります。 このプロパティの既定値は 0 です。<br /><br /> 注:このプロパティは、**OLE DB 変換先エディター**では使用できませんが、**詳細エディター**を使用して設定できます。|  
|DefaultCodePage|Integer|OLE DB 変換先に関連付けられた既定のコード ページ。|  
|FastLoadKeepIdentity|Boolean|データが読み込まれるときに ID 値をコピーするかどうかを指定する値。 このプロパティは、高速読み取りオプションのいずれかを使用した場合のみ使用できます。 このプロパティの既定値は `False` です。 このプロパティは、OLE DB の[IRowsetFastLoad &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/irowsetfastload-ole-db.md)プロパティに対応して `SSPROP_FASTLOADKEEPIDENTITY` います。|  
|FastLoadKeepNulls|Boolean|データが読み込まれるときに NULL 値をコピーするかどうかを指定する値。 このプロパティは、高速読み取りオプションのいずれかを使用した場合のみ使用できます。 このプロパティの既定値は `False` です。 このプロパティは、OLE DB の[IRowsetFastLoad &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/irowsetfastload-ole-db.md)プロパティに対応して `SSPROP_FASTLOADKEEPNULLS` います。|  
|FastLoadMaxInsertCommitSize|Integer|高速読み込み操作の実行中に OLE DB 変換先でコミットを試行するバッチ サイズを指定する値。 既定値の **0**は、すべての行が処理された後で、コミット操作が 1 回行われることを示します。|  
|FastLoadOptions|String|高速読み込みオプションのコレクション。 高速読み込みオプションには、テーブルのロックおよび制約のチェックが含まれています。 どちらか 1 つまたは両方を指定することも、どちらも指定しないこともできます。 このプロパティは、OLE DB IRowsetFastLoad プロパティに対応 `SSPROP_FASTLOADOPTIONS` し、やなどの文字列オプションを受け入れ `CHECK_CONSTRAINTS` `TABLOCK` ます。<br /><br /> 注:このプロパティの一部のオプションは、 **[Excel 変換先エディター]** では使用できませんが、 **[詳細エディター]** を使用して設定できます。|  
|OpenRowset|String|AccessMode がの場合 `OpenRowset` 、OLE DB 変換先がアクセスするテーブルまたはビューの名前。|  
|OpenRowsetVariable|String|AccessMode がの場合 `OpenRowset from Variable` 、OLE DB 変換先がアクセスするテーブルまたはビューの名前を含む変数の名前。|  
|SqlCommand|String|AccessMode がの場合 `SQL Command` 、OLE DB 変換先がデータの変換先列を指定するために使用する transact-sql ステートメント。|  
  
 OLE DB 変換先の入力および入力列には、カスタム プロパティはありません。  
  
 詳細については、「 [OLE DB 変換先](ole-db-destination.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [Common Properties](../common-properties.md)  
  
  
