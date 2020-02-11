---
title: OLE DB カスタム プロパティ | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 13a82d41-dd7a-4708-bc84-4407a536c877
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 996acc5f8e9b47af683c8d8376515f7f59e63120
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "62770992"
---
# <a name="ole-db-custom-properties"></a>OLE DB カスタム プロパティ
  **変換元のカスタム プロパティ**  
  
 OLE DB ソースには、カスタム プロパティと、すべてのデータ フロー コンポーネントとの共通プロパティの両方があります。  
  
 次の表は、OLE DB ソースのカスタム プロパティを示しています。 すべてのプロパティは読み取り/書き込み可能です。  
  
|プロパティ名|データ型|説明|  
|-------------------|---------------|-----------------|  
|AccessMode|整数|データベースへのアクセスに使用するモード。 使用できる値は、 **[行セットを開く**]、[**変数から行セットを開く**]、 `SQL Command`、[**変数からの SQL コマンド]** です。 既定値は **OpenRowset**です。|  
|AlwaysUseDefaultCodePage|Boolean|
  `DefaultCodePage` プロパティの値を各列に使用するか、または各列のロケールからコードページを派生するかを示す値。 このプロパティの既定値は `False` です。|  
|CommandTimeOut|整数|コマンドのタイムアウトの秒数。値 0 は、タイムアウトしないことを表します。<br /><br /> 注:このプロパティは、**OLE DB ソース エディター**では使用できませんが、**詳細エディター**を使用して設定できます。|  
|DefaultCodePage|整数|コード ページに関する情報をデータ ソースから取得できない場合に使用するコード ページ。|  
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
|AlwaysUseDefaultCodePage|Boolean|
  `DefaultCodePage` プロパティの値を各列に使用するか、または各列のロケールからコードページを派生するかを示す値。 このプロパティの既定値は `False` です。|  
|CommandTimeOut|整数|SQL コマンドがタイムアウトになるまでの最大秒数。この値に 0 を指定すると、時間は無制限になります。 このプロパティの既定値は 0 です。<br /><br /> 注:このプロパティは、**OLE DB 変換先エディター**では使用できませんが、**詳細エディター**を使用して設定できます。|  
|DefaultCodePage|整数|OLE DB 変換先に関連付けられた既定のコード ページ。|  
|FastLoadKeepIdentity|Boolean|データが読み込まれるときに ID 値をコピーするかどうかを指定する値。 このプロパティは、高速読み取りオプションのいずれかを使用した場合のみ使用できます。 このプロパティの既定値は `False` です。 このプロパティは、OLE DB の[IRowsetFastLoad &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/irowsetfastload-ole-db.md)プロパティ`SSPROP_FASTLOADKEEPIDENTITY`に対応しています。|  
|FastLoadKeepNulls|Boolean|データが読み込まれるときに NULL 値をコピーするかどうかを指定する値。 このプロパティは、高速読み取りオプションのいずれかを使用した場合のみ使用できます。 このプロパティの既定値は `False` です。 このプロパティは、OLE DB の[IRowsetFastLoad &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/irowsetfastload-ole-db.md)プロパティ`SSPROP_FASTLOADKEEPNULLS`に対応しています。|  
|FastLoadMaxInsertCommitSize|整数|高速読み込み操作の実行中に OLE DB 変換先でコミットを試行するバッチ サイズを指定する値。 既定値の **0**は、すべての行が処理された後で、コミット操作が 1 回行われることを示します。|  
|FastLoadOptions|String|高速読み込みオプションのコレクション。 高速読み込みオプションには、テーブルのロックおよび制約のチェックが含まれています。 どちらか 1 つまたは両方を指定することも、どちらも指定しないこともできます。 このプロパティは、OLE DB IRowsetFastLoad プロパティ`SSPROP_FASTLOADOPTIONS`に対応し、や`CHECK_CONSTRAINTS` `TABLOCK`などの文字列オプションを受け入れます。<br /><br /> 注:このプロパティの一部のオプションは、 **[Excel 変換先エディター]** では使用できませんが、 **[詳細エディター]** を使用して設定できます。|  
|OpenRowset|String|AccessMode が`OpenRowset`の場合、OLE DB 変換先がアクセスするテーブルまたはビューの名前。|  
|OpenRowsetVariable|String|AccessMode が`OpenRowset from Variable`の場合、OLE DB 変換先がアクセスするテーブルまたはビューの名前を含む変数の名前。|  
|SqlCommand|String|AccessMode が`SQL Command`の場合、OLE DB 変換先がデータの変換先列を指定するために使用する transact-sql ステートメント。|  
  
 OLE DB 変換先の入力および入力列には、カスタム プロパティはありません。  
  
 詳細については、「 [OLE DB 変換先](ole-db-destination.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [Common Properties](../common-properties.md)  
  
  
