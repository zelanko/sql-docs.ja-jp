---
title: 一括コピー操作の実行 |Microsoft ドキュメント
description: SQL Server の OLE DB Driver を使用して一括コピー操作の実行
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: oledb|features
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- bulk copy [OLE DB Driver for SQL Server]
- data access [OLE DB Driver for SQL Server], bulk copy operations
- OLE DB Driver for SQL Server, bulk copy operations
- MSOLEDBSQL, bulk copy operations
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 210aa79c589c241056aa6b7e342125553b6257b4
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="performing-bulk-copy-operations"></a>一括コピー操作の実行
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の一括コピー機能により、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] テーブルやビューに大量のデータを入出力できます。 SELECT ステートメントを指定してデータを外部に転送することもできます。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] と ASCII ファイルなどのオペレーティング システム データ ファイルとの間でデータを移動できます。 データ ファイルには、さまざまな形式を使用できます。一括コピーの形式は、フォーマット ファイルで定義されます。 必要に応じて、データをプログラム変数に読み込んでから、一括コピー関数や一括コピー メソッドを使用して [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] に転送できます。  
  
 この機能を示すサンプル アプリケーションを参照してください。[一括コピー データを使用して IRowsetFastLoad &#40;OLE DB&#41;](../../oledb/ole-db-how-to/bulk-copy-data-using-irowsetfastload-ole-db.md)です。  
  
 アプリケーションでは、通常、次のいずれかの方法で一括コピーを使用します。  
  
-   テーブル、ビュー、または Transact-SQL ステートメントの結果セットからデータ ファイルに一括コピーします。その際、コピー先のデータ ファイルには、テーブルやビューと同じ形式でデータを格納します。  
  
     これをネイティブモード データ ファイルと呼びます。  
  
-   テーブル、ビュー、または Transact-SQL ステートメントの結果セットからデータ ファイルに一括コピーします。その際、コピー先のデータ ファイルには、テーブルやビューとは異なる形式でデータを格納します。  
  
     この場合、データ ファイルに格納される各列の特性 (データ型、位置、長さ、ターミネータなど) を定義するフォーマット ファイルを別に作成します。 すべての列を文字形式に変換する場合、変換後のファイルをキャラクターモード データ ファイルと呼びます。  
  
-   データ ファイルからテーブルやビューに一括コピーします。  
  
     必要に応じて、フォーマット ファイルを使用してデータ ファイルのレイアウトを決定します。  
  
-   プログラム変数にデータを読み込んでから、毎回 1 行ずつ一括コピーを行う一括コピー関数を使用して、データをテーブルやビューにインポートします。  
  
 一括コピー関数で使用するデータ ファイルを、別の一括コピー プログラムで作成する必要はありません。 他のシステムでも、一括コピー定義に従ってデータ ファイルとフォーマット ファイルを作成できます。その後、これらのファイルを [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の一括コピー プログラムで使用して、データを [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] にインポートできます。 たとえば、スプレッドシートからタブ区切り形式のファイルにデータをエクスポートし、タブ区切りファイルの形式を示すフォーマット ファイルを作成した後、一括コピー プログラムを使用して、データを [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] に簡単にインポートできます。 一括コピーで生成されたデータ ファイルを、他のアプリケーションにインポートすることもできます。 たとえば、一括コピー関数を使用して、スプレッドシートに読み込むことができるタブ区切りファイルとして、テーブルやビューからデータをエクスポートできます。  
  
 一括コピー関数を使用するアプリケーションをコーディングするプログラマは、適切なパフォーマンスで一括コピーを行うための一般的な規則に従う必要があります。 バルク コピー操作のサポートの詳細については[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]を参照してください[データのエクスポートと一括インポート&#40;SQL Server&#41;](../../../relational-databases/import-export/bulk-import-and-export-of-data-sql-server.md)です。  
  
## <a name="limitations-and-restrictions"></a>制限事項と制約事項  
 CLR ユーザー定義型 (UDT) はバイナリ データとしてバインドする必要があります。 フォーマット ファイルで、SQLCHAR がコピー先の UDT 列のデータ型として指定されていたとしても、BCP ユーティリティは、そのデータをバイナリとして扱います。  
  
 一括コピー操作では SET FMTONLY OFF を使用しないでください。 SET FMTONLY OFF を使用すると、一括コピー操作でエラーや予期しない結果が生じることがあります。  
  
## <a name="ole-db-driver-for-sql-server"></a>OLE DB Driver for SQL Server 
 SQL Server の OLE DB ドライバーで一括コピー操作を実行するための 2 つのメソッドを実装する、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]データベース。 最初のメソッドを使用して、 [IRowsetFastLoad](../../oledb/ole-db-interfaces/irowsetfastload-ole-db.md)メモリベースの一括コピー操作は、2 番目のインターフェイスを使用して、 [IBCPSession](../../oledb/ole-db-interfaces/ibcpsession-ole-db.md)ファイルベースの一括コピー操作のインターフェイスです。  
  
### <a name="using-memory-based-bulk-copy-operations"></a>メモリ ベースの一括コピー操作の使用  
 SQL Server の OLE DB ドライバーを実装して、 **IRowsetFastLoad**のサポートを公開するインターフェイス[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]メモリベースの一括コピー操作します。 **IRowsetFastLoad**インターフェイスを実装して、 [irowsetfastload::commit](../../oledb/ole-db-interfaces/irowsetfastload-commit-ole-db.md)と[irowsetfastload::insertrow](../../oledb/ole-db-interfaces/irowsetfastload-insertrow-ole-db.md)メソッドです。  
  
#### <a name="enabling-a-session-for-irowsetfastload"></a>IRowsetFastLoad のセッションの有効化  
 コンシューマー、OLE DB Driver for SQL Server に固有のデータ ソース プロパティである SSPROP_ENABLEFASTLOAD を VARIANT_TRUE に設定して一括コピーの必要があるの SQL Server の OLE DB Driver に通知します。 プロパティがデータ ソースの設定は、コンシューマーは、SQL Server セッションの OLE DB ドライバーを作成します。 新しいセッションがするコンシューマーへのアクセスを可能、 **IRowsetFastLoad**インターフェイスです。  
  
> [!NOTE]  
>  場合、 **IDataInitialize**インターフェイスは、データ ソースを初期化するために使用しで SSPROP_IRowsetFastLoad プロパティを設定する必要がある、 *rgPropertySets*のパラメーター、 **Iopenrowset::openrowset**メソッド以外の場合への呼び出し、 **OpenRowset**メソッドは E_NOINTERFACE を返します。  
  
 一括コピー セッションを有効にすると、セッションでインターフェイスをサポートします SQL Server の OLE DB ドライバーが制限されます。 一括コピーが可能なセッションは、次のインターフェイスのみを公開します。  
  
-   **IDBSchemaRowset**  
  
-   **IGetDataSource**  
  
-   **IOpenRowset**  
  
-   **ISupportErrorInfo**  
  
-   **ITransactionJoin**  
  
 一括コピーが有効な行セットの作成を無効にして、OLE DB ドライバーにより SQL Server セッションの標準的な処理に戻すには、SSPROP_ENABLEFASTLOAD を VARIANT_FALSE にリセットします。  
  
#### <a name="irowsetfastload-rowsets"></a>IRowsetFastLoad 行セット  
 OLE DB Driver for SQL Server 一括コピー行セットは書き込み専用では、コンシューマーの構造を決定できるようにするインターフェイスを公開している、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]テーブル。 次のインターフェイスは、一括コピーが有効なで公開される OLE DB Driver for SQL Server の行セット。  
  
-   **IAccessor**  
  
-   **IColumnsInfo**  
  
-   **IColumnsRowset**  
  
-   **IConvertType**  
  
-   **IRowsetFastLoad**  
  
-   **IRowsetInfo**  
  
-   **ISupportErrorInfo**  
  
 プロバイダー固有のプロパティ SSPROP_FASTLOADOPTIONS、SSPROP_FASTLOADKEEPNULLS、および SSPROP_FASTLOADKEEPIDENTITY、OLE DB Driver for SQL Server の一括コピー行セットの動作の制御します。 プロパティが指定されて、 *rgProperties*のメンバー、 *rgPropertySets* **IOpenRowset**パラメーター メンバー。  
  
|プロパティ ID|Description|  
|-----------------|-----------------|  
|SSPROP_FASTLOADKEEPIDENTITY|列 : なし<br /><br /> R/W 読み取り/書き込み<br /><br /> 型 : VT_BOOL<br /><br /> 既定値 : VARIANT_FALSE<br /><br /> 説明 : コンシューマーが指定する ID 値を管理します。<br /><br /> VARIANT_FALSE: [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] テーブルの ID 列の値が [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] によって生成されます。 列にバインドされている任意の値は、SQL Server の OLE DB ドライバーによって無視されます。<br /><br /> VARIANT_TRUE: コンシューマーが、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ID 列に値を提供するアクセサーをバインドします。 Identity プロパティは、コンシューマーごとに一意の値を提供するため、NULL を許容する列で使用できません**IRowsetFastLoad::Insert**呼び出します。|  
|SSPROP_FASTLOADKEEPNULLS|列 : なし<br /><br /> R/W 読み取り/書き込み<br /><br /> 型 : VT_BOOL<br /><br /> 既定値 : VARIANT_FALSE<br /><br /> 説明 : DEFAULT 制約が適用されている列の NULL 値を管理します。 影響を受けるのは、NULL 値を許容し、DEFAULT 制約が適用されている [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 列だけです。<br /><br /> VARIANT_FALSE: [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] OLE DB Driver for SQL Server コンシューマーが列の null 値を含む行を挿入するときに、列の既定値を挿入します。<br /><br /> VARIANT_TRUE: [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] OLE DB Driver for SQL Server コンシューマーが列の null 値を含む行を挿入するときに、列の値に対する NULL を挿入します。|  
|SSPROP_FASTLOADOPTIONS|列 : なし<br /><br /> R/W 読み取り/書き込み<br /><br /> 型 : VT_BSTR<br /><br /> 既定値 : なし<br /><br /> 説明: このプロパティと同じでは、 **-h** "*ヒント*[,...*n*]"のオプション、 **bcp**ユーティリティです。 データをテーブルに一括コピーするときのオプションとして、次の文字列を使用できます。<br /><br /> **ORDER**(*column*[**ASC** &#124; **DESC**][,...*n*]): データ ファイル内のデータの並べ替え順。 読み込むデータ ファイルをテーブル上のクラスター化インデックスに従って並べ替えると、一括コピーのパフォーマンスが向上します。<br /><br /> **ROWS_PER_BATCH** = *bb*: バッチごとのデータの行の数 (として*bb*)。 サーバーは、 *bb*の値に応じて一括コピーの負荷を最適化します。 既定では、 **ROWS_PER_BATCH**が不明です。<br /><br /> **KILOBYTES_PER_BATCH** = *cc*: (cc) としてバッチごとのデータのキロバイト (KB) の数。 既定では、 **KILOBYTES_PER_BATCH**が不明です。<br /><br /> **TABLOCK**: 一括コピー操作の実行中、テーブル レベルのロックを取得します。 一括コピー操作中だけロックを保持することにより、テーブル ロックの競合が少なくなるので、このオプションによりパフォーマンスが大幅に向上します。 テーブルを読み込める複数のクライアントで同時に、テーブルにインデックスがあるない場合および**TABLOCK**を指定します。 既定では、ロック動作はテーブル オプションによって決まります**一括読み込みでロックをテーブル**です。<br /><br /> **CHECK_CONSTRAINTS**: に対する制約*table_name*一括コピー操作中にチェックされます。 既定では、制約は無視されます。<br /><br /> **FIRE_TRIGGER**:[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]トリガーに対して行のバージョン管理を使用し、行のバージョンのバージョン ストアを**tempdb**です。 したがって、トリガーが有効になっていても一括ログ記録を最適化できます。 バッチを一括インポートで大量の行の有効なトリガーを使用して前に、のサイズを拡張する必要があります**tempdb**です。|  
  
### <a name="using-file-based-bulk-copy-operations"></a>ファイル ベースの一括コピー操作の使用  
 SQL Server の OLE DB ドライバーを実装して、 **IBCPSession**のサポートを公開するインターフェイス[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]ファイルベースの一括コピー操作します。 **IBCPSession**インターフェイスを実装して、 [ibcpsession::bcpcolfmt](../../oledb/ole-db-interfaces/ibcpsession-bcpcolfmt-ole-db.md)、 [ibcpsession::bcpcolumns](../../oledb/ole-db-interfaces/ibcpsession-bcpcolumns-ole-db.md)、 [ibcpsession::bcpcontrol](../../oledb/ole-db-interfaces/ibcpsession-bcpcontrol-ole-db.md)、 [IBCPSession::BCPDone](../../oledb/ole-db-interfaces/ibcpsession-bcpdone-ole-db.md)、 [:bcpexec](../../oledb/ole-db-interfaces/ibcpsession-bcpexec-ole-db.md)、 [ibcpsession::bcpinit](../../oledb/ole-db-interfaces/ibcpsession-bcpinit-ole-db.md)、 [ibcpsession::bcpreadfmt](../../oledb/ole-db-interfaces/ibcpsession-bcpreadfmt-ole-db.md)、および[ibcpsession::bcpwritefmt](../../oledb/ole-db-interfaces/ibcpsession-bcpwritefmt-ole-db.md)メソッドです。  
  
  
## <a name="see-also"></a>参照  
 [SQL Server 機能の OLE DB ドライバー](../../oledb/features/oledb-driver-for-sql-server-features.md)   
 [データ ソースのプロパティ&#40;OLE DB&#41;](../../oledb/ole-db-data-source-objects/data-source-properties-ole-db.md)   
 [一括データ &#40; のインポートとエクスポートSQL Server と &#41; です。](../../../relational-databases/import-export/bulk-import-and-export-of-data-sql-server.md)   
 [IRowsetFastLoad &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/irowsetfastload-ole-db.md)   
 [IBCPSession &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/ibcpsession-ole-db.md)   
 [一括インポートのパフォーマンスを最適化します。](http://msdn.microsoft.com/library/ms190421\(SQL.105\).aspx)  

