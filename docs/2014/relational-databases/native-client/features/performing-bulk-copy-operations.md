---
title: 一括コピー操作の実行 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client  - "database-engine" - "docset-sql-devref"
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- bulk copy [SQL Server Native Client]
- data access [SQL Server Native Client], bulk copy operations
- SQL Server Native Client, bulk copy operations
- SQLNCLI, bulk copy operations
ms.assetid: 50d8456b-e6a1-4b25-bc7e-56946ed654a7
caps.latest.revision: 28
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f4d246b79da64177275a01a8a0d2672c8854dcb5
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37408431"
---
# <a name="performing-bulk-copy-operations"></a>一括コピー操作の実行
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の一括コピー機能により、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] テーブルやビューに大量のデータを入出力できます。 SELECT ステートメントを指定してデータを外部に転送することもできます。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] と ASCII ファイルなどのオペレーティング システム データ ファイルとの間でデータを移動できます。 データ ファイルには、さまざまな形式を使用できます。一括コピーの形式は、フォーマット ファイルで定義されます。 必要に応じて、データをプログラム変数に読み込んでから、一括コピー関数や一括コピー メソッドを使用して [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] に転送できます。  
  
 この機能を示すサンプル アプリケーションを参照してください。[一括コピー データを使用して IRowsetFastLoad &#40;OLE DB&#41;](../../native-client-ole-db-interfaces/irowsetfastload-ole-db.md)します。  
  
 アプリケーションでは、通常、次のいずれかの方法で一括コピーを使用します。  
  
-   テーブル、ビュー、または Transact-SQL ステートメントの結果セットからデータ ファイルに一括コピーします。その際、コピー先のデータ ファイルには、テーブルやビューと同じ形式でデータを格納します。  
  
     これをネイティブモード データ ファイルと呼びます。  
  
-   テーブル、ビュー、または Transact-SQL ステートメントの結果セットからデータ ファイルに一括コピーします。その際、コピー先のデータ ファイルには、テーブルやビューとは異なる形式でデータを格納します。  
  
     この場合、データ ファイルに格納される各列の特性 (データ型、位置、長さ、ターミネータなど) を定義するフォーマット ファイルを別に作成します。 すべての列を文字形式に変換する場合、変換後のファイルをキャラクターモード データ ファイルと呼びます。  
  
-   データ ファイルからテーブルやビューに一括コピーします。  
  
     必要に応じて、フォーマット ファイルを使用してデータ ファイルのレイアウトを決定します。  
  
-   プログラム変数にデータを読み込んでから、毎回 1 行ずつ一括コピーを行う一括コピー関数を使用して、データをテーブルやビューにインポートします。  
  
 一括コピー関数で使用するデータ ファイルを、別の一括コピー プログラムで作成する必要はありません。 他のシステムでも、一括コピー定義に従ってデータ ファイルとフォーマット ファイルを作成できます。その後、これらのファイルを [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の一括コピー プログラムで使用して、データを [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] にインポートできます。 たとえば、スプレッドシートからタブ区切り形式のファイルにデータをエクスポートし、タブ区切りファイルの形式を示すフォーマット ファイルを作成した後、一括コピー プログラムを使用して、データを [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] に簡単にインポートできます。 一括コピーで生成されたデータ ファイルを、他のアプリケーションにインポートすることもできます。 たとえば、一括コピー関数を使用して、スプレッドシートに読み込むことができるタブ区切りファイルとして、テーブルやビューからデータをエクスポートできます。  
  
 一括コピー関数を使用するアプリケーションをコーディングするプログラマは、適切なパフォーマンスで一括コピーを行うための一般的な規則に従う必要があります。 バルク コピー操作のサポートの詳細については[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]を参照してください[一括インポートとエクスポートのデータ&#40;SQL Server&#41;](../../import-export/bulk-import-and-export-of-data-sql-server.md)します。  
  
## <a name="limitations-and-restrictions"></a>制限事項と制約事項  
 CLR ユーザー定義型 (UDT) はバイナリ データとしてバインドする必要があります。 フォーマット ファイルで、SQLCHAR がコピー先の UDT 列のデータ型として指定されていたとしても、BCP ユーティリティは、そのデータをバイナリとして扱います。  
  
 一括コピー操作では SET FMTONLY OFF を使用しないでください。 SET FMTONLY OFF を使用すると、一括コピー操作でエラーや予期しない結果が生じることがあります。  
  
## <a name="sql-server-native-client-ole-db-provider"></a>SQL Server Native Client OLE DB プロバイダー  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーで一括コピー操作を実行するための 2 つのメソッドを実装する、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]データベース。 最初の方法を使用して、 [IRowsetFastLoad](../../native-client-ole-db-interfaces/irowsetfastload-ole-db.md)メモリベースの一括コピー操作は、2 番目のインターフェイスは、使用して、 [IBCPSession](../../native-client-ole-db-interfaces/ibcpsession-ole-db.md)ファイルベースの一括コピー操作のインターフェイス。  
  
### <a name="using-memory-based-bulk-copy-operations"></a>メモリ ベースの一括コピー操作の使用  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーの実装、 **IRowsetFastLoad**のサポートを公開するインターフェイス[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]メモリベースの一括コピー操作。 **IRowsetFastLoad**インターフェイスの実装、 [irowsetfastload::commit](../../native-client-ole-db-interfaces/irowsetfastload-commit-ole-db.md)と[irowsetfastload::insertrow](../../native-client-ole-db-interfaces/irowsetfastload-insertrow-ole-db.md)メソッド。  
  
#### <a name="enabling-a-session-for-irowsetfastload"></a>IRowsetFastLoad のセッションの有効化  
 コンシューマーは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダー固有のデータ ソース プロパティである SSPROP_ENABLEFASTLOAD を VARIANT_TRUE に設定することにより、一括コピーを実行する必要があることを [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーに通知します。 コンシューマーはデータ ソースのプロパティ セットを使用して、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダー セッションを作成します。 新しいセッションがするコンシューマーへのアクセスを許可、 **IRowsetFastLoad**インターフェイス。  
  
> [!NOTE]  
>  場合、 **IDataInitialize**インターフェイスは、データ ソースの初期化に使用しで SSPROP_IRowsetFastLoad プロパティを設定する必要があります、 *rgPropertySets*のパラメーター、 **Iopenrowset::openrowset**メソッド。 それ以外の呼び出し、 **OpenRowset**メソッドは E_NOINTERFACE を返します。  
  
 一括コピー用にセッションを有効にすることで、そのセッションのインターフェイスに対する [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーのサポートが制限されます。 一括コピーが可能なセッションは、次のインターフェイスのみを公開します。  
  
-   **IDBSchemaRowset**  
  
-   **IGetDataSource**  
  
-   **IOpenRowset**  
  
-   **ISupportErrorInfo**  
  
-   **ITransactionJoin**  
  
 一括コピー可能な行セットの作成を無効にし、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダー セッションの処理を標準処理に戻すには、SSPROP_ENABLEFASTLOAD を VARIANT_FALSE にリセットします。  
  
#### <a name="irowsetfastload-rowsets"></a>IRowsetFastLoad 行セット  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーの一括コピー行セットは書き込み専用ですが、コンシューマーはこれらの行セットが公開するインターフェイスを使用することで、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] テーブルの構造を決定できます。 一括コピー可能な [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダー行セットは、次のインターフェイスを公開します。  
  
-   **IAccessor**  
  
-   **IColumnsInfo**  
  
-   **IColumnsRowset**  
  
-   **IConvertType**  
  
-   **IRowsetFastLoad**  
  
-   **IRowsetInfo**  
  
-   **ISupportErrorInfo**  
  
 プロバイダー固有のプロパティ SSPROP_FASTLOADOPTIONS、SSPROP_FASTLOADKEEPNULLS、および SSPROP_FASTLOADKEEPIDENTITY により、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーの一括コピー行セットの動作が制御されます。 プロパティがで指定された、 *rgProperties*のメンバー、* rgPropertySets ***IOpenRowset**パラメーター メンバー。  
  
|プロパティ ID|説明|  
|-----------------|-----------------|  
|SSPROP_FASTLOADKEEPIDENTITY|列 : なし<br /><br /> R/W 読み取り/書き込み<br /><br /> 型 : VT_BOOL<br /><br /> 既定値 : VARIANT_FALSE<br /><br /> 説明 : コンシューマーが指定する ID 値を管理します。<br /><br /> VARIANT_FALSE: [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] テーブルの ID 列の値が [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] によって生成されます。 バインドされた値、列は無視されます、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダー。<br /><br /> VARIANT_TRUE: コンシューマーが、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ID 列に値を提供するアクセサーをバインドします。 Identity プロパティが null の場合を受け入れるので、コンシューマーでは、一意の値は各列で使用可能な **:insert**呼び出します。|  
|SSPROP_FASTLOADKEEPNULLS|列 : なし<br /><br /> R/W 読み取り/書き込み<br /><br /> 型 : VT_BOOL<br /><br /> 既定値 : VARIANT_FALSE<br /><br /> 説明 : DEFAULT 制約が適用されている列の NULL 値を管理します。 影響を受けるのは、NULL 値を許容し、DEFAULT 制約が適用されている [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 列だけです。<br /><br /> VARIANT_FALSE: [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーのコンシューマーが列に NULL 値を含む行を挿入すると、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ではその列に既定値が挿入されます。<br /><br /> VARIANT_TRUE: [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーのコンシューマーが列に NULL 値を含む行を挿入すると、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ではその列に NULL 値が挿入されます。|  
|SSPROP_FASTLOADOPTIONS|列 : なし<br /><br /> R/W 読み取り/書き込み<br /><br /> 型 : VT_BSTR<br /><br /> 既定値 : なし<br /><br /> 説明: このプロパティと同じでは、 **-h** "*ヒント*[,...*n*]"のオプション、 **bcp**ユーティリティ。 データをテーブルに一括コピーするときのオプションとして、次の文字列を使用できます。<br /><br /> **順序**(*列*[**ASC** &#124; **DESC**] [,...*n*]): データ ファイル内のデータの並べ替え順。 読み込むデータ ファイルをテーブル上のクラスター化インデックスに従って並べ替えると、一括コピーのパフォーマンスが向上します。<br /><br /> **ROWS_PER_BATCH** = *bb*: バッチごとのデータの行の数 (として*bb*)。 サーバーは、 *bb*の値に応じて一括コピーの負荷を最適化します。 既定では、 **ROWS_PER_BATCH**が不明です。<br /><br /> **KILOBYTES_PER_BATCH** = *cc*: (cc) としてバッチごとのデータのキロバイト (KB) の数。 既定では、 **KILOBYTES_PER_BATCH**が不明です。<br /><br /> **TABLOCK**: 一括コピー操作の実行中のテーブル レベル ロックが取得されます。 一括コピー操作中だけロックを保持することにより、テーブル ロックの競合が少なくなるので、このオプションによりパフォーマンスが大幅に向上します。 テーブルを読み込むことができます複数のクライアントで同時に、テーブルにインデックスがあるない場合、 **TABLOCK**を指定します。 既定では、ロックの動作はテーブル オプションによって決まります**一括読み込みでロックをテーブル**します。<br /><br /> **CHECK_CONSTRAINTS**: に対する制約*table_name*一括コピー操作中にチェックされます。 既定では、制約は無視されます。<br /><br /> **FIRE_TRIGGER**:[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]トリガーに対して行のバージョン管理を使用し、行のバージョンでバージョン ストアを**tempdb**します。 したがって、トリガーが有効になっていても一括ログ記録を最適化できます。 一括のバッチが多数の行をインポートするトリガーを有効にする前にのサイズを拡張する必要があります**tempdb**します。|  
  
### <a name="using-file-based-bulk-copy-operations"></a>ファイル ベースの一括コピー操作の使用  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーの実装、 **IBCPSession**のサポートを公開するインターフェイス[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]ファイルベースの一括コピー操作。 **IBCPSession**インターフェイスの実装、 [ibcpsession::bcpcolfmt](../../native-client-ole-db-interfaces/ibcpsession-bcpcolfmt-ole-db.md)、 [ibcpsession::bcpcolumns](../../native-client-ole-db-interfaces/ibcpsession-bcpcolumns-ole-db.md)、 [ibcpsession::bcpcontrol](../../native-client-ole-db-interfaces/ibcpsession-bcpcontrol-ole-db.md)、 [IBCPSession::BCPDone](../../native-client-ole-db-interfaces/ibcpsession-bcpdone-ole-db.md)、 [:bcpexec](../../native-client-ole-db-interfaces/ibcpsession-bcpexec-ole-db.md)、 [ibcpsession::bcpinit](../../native-client-ole-db-interfaces/ibcpsession-bcpinit-ole-db.md)、 [ibcpsession::bcpreadfmt](../../native-client-ole-db-interfaces/ibcpsession-bcpreadfmt-ole-db.md)、および[ibcpsession::bcpwritefmt](../../native-client-ole-db-interfaces/ibcpsession-bcpwritefmt-ole-db.md)メソッド。  
  
## <a name="sql-server-native-client-odbc-driver"></a>SQL Server Native Client ODBC ドライバー  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーでは、以前のバージョンの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ODBC ドライバーの一部であった一括コピー操作サポートが同様に提供されます。 使用して一括コピー操作については、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーを参照してください[一括コピー操作を実行する&#40;ODBC&#41;](../../native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md)します。  
  
## <a name="see-also"></a>参照  
 [SQL Server Native Client の機能](sql-server-native-client-features.md)   
 [データ ソースのプロパティ&#40;OLE DB&#41;](../../native-client-ole-db-data-source-objects/data-source-properties-ole-db.md)   
 [データの一括インポートと一括エクスポート &#40;SQL Server&#41;](../../import-export/bulk-import-and-export-of-data-sql-server.md)   
 [IRowsetFastLoad &#40;OLE DB&#41;](../../native-client-ole-db-interfaces/irowsetfastload-ole-db.md)   
 [IBCPSession &#40;OLE DB&#41;](../../native-client-ole-db-interfaces/ibcpsession-ole-db.md)   
 [一括インポートのパフォーマンスを最適化します。](http://msdn.microsoft.com/library/ms190421\(SQL.105\).aspx)  
  
  
