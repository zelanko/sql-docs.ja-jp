---
title: "一括挿入 (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- BULK_TSQL
- BULK INSERT
- BULK_INSERT_TSQL
- BULK
dev_langs:
- TSQL
helpviewer_keywords:
- tables [SQL Server], importing data into
- inserting files
- views [SQL Server], importing data into
- BULK INSERT statement
- views [SQL Server], exporting data from
- importing data, bulk import
- bulk importing [SQL Server], BULK INSERT statement
- file importing [SQL Server]
ms.assetid: be3984e1-5ab3-4226-a539-a9f58e1e01e2
caps.latest.revision: 153
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 80b16fd446ff72c6a673a576d9a8deb9514be8b2
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="bulk-insert-transact-sql"></a>BULK INSERT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で、ユーザーが指定した形式で、データベース テーブルまたはビューにデータ ファイルをインポートします。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
BULK INSERT   
   [ database_name . [ schema_name ] . | schema_name . ] [ table_name | view_name ]   
      FROM 'data_file'   
     [ WITH   
    (   
   [ [ , ] BATCHSIZE = batch_size ]   
   [ [ , ] CHECK_CONSTRAINTS ]   
   [ [ , ] CODEPAGE = { 'ACP' | 'OEM' | 'RAW' | 'code_page' } ]   
   [ [ , ] DATAFILETYPE =   
      { 'char' | 'native'| 'widechar' | 'widenative' } ]   
   [ [ , ] DATASOURCE = 'data_source_name' ]
   [ [ , ] ERRORFILE = 'file_name' ]
   [ [ , ] ERRORFILE_DATASOURCE = 'data_source_name' ]   
   [ [ , ] FIRSTROW = first_row ]   
   [ [ , ] FIRE_TRIGGERS ]   
   [ [ , ] FORMATFILE_DATASOURCE = 'data_source_name' ]
   [ [ , ] KEEPIDENTITY ]   
   [ [ , ] KEEPNULLS ]   
   [ [ , ] KILOBYTES_PER_BATCH = kilobytes_per_batch ]   
   [ [ , ] LASTROW = last_row ]   
   [ [ , ] MAXERRORS = max_errors ]   
   [ [ , ] ORDER ( { column [ ASC | DESC ] } [ ,...n ] ) ]   
   [ [ , ] ROWS_PER_BATCH = rows_per_batch ]   
   [ [ , ] ROWTERMINATOR = 'row_terminator' ]   
   [ [ , ] TABLOCK ]   

   -- input file format options
   [ [ , ] FORMAT = 'CSV' ]
   [ [ , ] FIELDQUOTE = 'quote_characters']
   [ [ , ] FORMATFILE = 'format_file_path' ]   
   [ [ , ] FIELDTERMINATOR = 'field_terminator' ]   
   [ [ , ] ROWTERMINATOR = 'row_terminator' ]   
    )]   
```  
  
## <a name="arguments"></a>引数  
 *database_name*  
 指定のテーブルまたはビューが含まれているデータベース名を指定します。 指定しない場合、現在のデータベースが使用されます。  
  
 *schema_name*  
 テーブルまたはビューのスキーマの名前を指定します。 *schema_name*場合は、一括インポート操作を実行するユーザーの既定のスキーマは、指定したテーブルまたはビューのスキーマは省略します。 場合*スキーマ*が指定されていないと、一括インポート操作を実行するユーザーの既定のスキーマは、指定したテーブルまたはビューから、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エラー メッセージ、および一括インポート操作が取り消されるを返します。  
  
 *table_name*  
 データの一括インポート先のテーブル名またはビュー名を指定します。 指定できるビューは、すべての列が同じベース テーブルを参照するビューだけです。 ビューにデータの読み込みの制限に関する詳細については、次を参照してください。 [INSERT &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/insert-transact-sql.md).  
  
 **'** *data_file* **'**  
 指定のテーブルまたはビューにインポートするデータが含まれているデータ ファイルの完全なパスを指定します。 BULK INSERT を使用して、ディスク (ネットワーク、フロッピー ディスク、ハード ディスクなど) からデータをインポートすることができます。   
 
 *data_file*をサーバーから有効なパスを指定する必要があります[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]が実行されています。 場合*data_file*がリモート ファイル、汎用名前付け規則 (UNC) 名を指定します。 UNC 名の形式\\ \\ *Systemname*\\*ShareName*\\*パス*\\ *FileName*です。 たとえば、 `\\SystemX\DiskZ\Sales\update.txt`のようにします。   
**適用対象:** [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1.   
以降で[!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)]CTP1.1、data_file は、Azure blob ストレージにすることができます。

**'** *data_source_name* **'**   
**適用対象:** [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1.   
名前付きの外部データ ソースがインポートされるファイルの Azure Blob ストレージの場所を指しています。 使用して、外部データ ソースを作成する必要があります、`TYPE = BLOB_STORAGE`オプションで追加された[!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)]CTP 1.1 です。 詳細については、次を参照してください。 [CREATE EXTERNAL DATA SOURCE](../../t-sql/statements/create-external-data-source-transact-sql.md)です。    
  
 BATCHSIZE  **=**  *batch_size*  
 1 つのバッチに含まれている行の数を指定します。 それぞれのバッチは、1 回のトランザクションでサーバーにコピーされます。 コピーに失敗した場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では各バッチのトランザクションがコミットまたはロールバックされます。 既定では、指定のデータ ファイル内にあるすべてのデータが 1 つのバッチになります。 パフォーマンスに関する考慮事項については、後の「解説」を参照してください。  
  
 CHECK_CONSTRAINTS  
 一括インポート操作中、対象テーブルまたはビューに対するすべての制約を検証します。 CHECK_CONSTRAINTS オプションを指定しない場合、CHECK 制約および FOREIGN KEY 制約は無視され、操作の後でテーブルの制約は信頼されていないものとしてマークされます。  
  
> [!NOTE]  
>  UNIQUE および PRIMARY KEY 制約は常に適用されます。 NOT NULL 制約で定義された文字型列にインポートする場合、テキスト ファイルに値がなければ BULK INSERT は空白文字列を挿入します。  
  
 ある時点で、テーブル全体に対する制約を確認する必要があります。 一括インポート操作の実行時にテーブルが空でなかった場合は、制約の再検証を行うと、追加データに CHECK 制約を適用するよりもコストがかかる可能性があります。  
  
 入力データに制約違反の行が含まれている場合などは、制約を無効 (既定の動作) にできます。 CHECK 制約を無効になっているには、データをインポートし、使用することができます[!INCLUDE[tsql](../../includes/tsql-md.md)]を無効なデータを削除してステートメントです。  
  
> [!NOTE]  
>  MAXERRORS オプションは制約チェックには適用されません。  
  
 CODEPAGE  **=**  { **'**ACP**'** | **'**OEM**'**  | **'**RAW**'** | **'***code_page***'** }  
 データ ファイル内のデータのコード ページを指定します。 CODEPAGE は、データが含まれている場合にのみ関連する**char**、 **varchar**、または**テキスト**文字の値よりも大きい列**127**以下**32**です。  
  
> [!NOTE]  
>  [!INCLUDE[msCoName](../../includes/msconame-md.md)]内の各列の照合順序名を指定することをお勧め、[フォーマット ファイル](../../relational-databases/import-export/use-a-format-file-to-bulk-import-data-sql-server.md)です。  
  
|CODEPAGE の値|Description|  
|--------------------|-----------------|  
|ACP|列の**char**、 **varchar**、または**テキスト**からデータ型を変換、 [!INCLUDE[vcpransi](../../includes/vcpransi-md.md)] / [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows コード ページ (ISO 1252) を[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]コード ページです。|  
|OEM (既定値)|列の**char**、 **varchar**、または**テキスト**システム OEM コード ページからデータ型を変換、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]コード ページです。|  
|RAW|1 つのコード ページから別のコード ページへの変換は行われません。このオプションを使用すると、最も高速に操作を完了できます。|  
|*code_page*|850 など、特定のコード ページ番号を指定します。<br /><br /> **\*\*重要な\* \*** より前のバージョン[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]コード ページ 65001 (utf-8 エンコード) をサポートしていません。|  
  
 DATAFILETYPE  **=**  { **'char'** | **'native'** | **'widechar'**  |  **widenative** }  
 BULK INSERT で、指定したデータ ファイルの型の値に基づいてインポート操作を実行します。  
  
|DATAFILETYPE の値|すべてのデータが示す形式|  
|------------------------|------------------------------|  
|**char** (既定値)|文字形式。<br /><br /> 詳細については、「[文字形式を使用したデータのインポートまたはエクスポート &#40;SQL Server&#41;](../../relational-databases/import-export/use-character-format-to-import-or-export-data-sql-server.md)」をご覧ください。|  
|**ネイティブ**|ネイティブ (データベース) データ型。 データの一括インポートで、ネイティブ データ ファイルを作成する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を使用して、 **bcp**ユーティリティです。<br /><br /> ネイティブ値を使用すると、char 型の値を使用するよりもパフォーマンスが向上します。<br /><br /> 詳細については、「[ネイティブ形式を使用したデータのインポートまたはエクスポート &#40;SQL Server&#41;](../../relational-databases/import-export/use-native-format-to-import-or-export-data-sql-server.md)」をご覧ください。|  
|**widechar**|Unicode 文字。<br /><br /> 詳細については、「 [Unicode 文字形式を使用したデータのインポートまたはエクスポート &#40;SQL Server&#41;](../../relational-databases/import-export/use-unicode-character-format-to-import-or-export-data-sql-server.md)」をご覧ください。|  
|**widenative**|ネイティブ (データベース) データ型では可**char**、 **varchar**、および**テキスト**列、データが Unicode として格納されています。 作成、 **widenative**データ ファイルからデータの一括インポートを[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を使用して、 **bcp**ユーティリティです。<br /><br /> **Widenative**値に代わるより高いパフォーマンス手段を提供する**widechar**です。 データ ファイルが含まれている場合[!INCLUDE[vcpransi](../../includes/vcpransi-md.md)]指定文字を拡張**widenative**です。<br /><br /> 詳細については、「 [Unicode ネイティブ形式を使用したデータのインポートまたはエクスポート &#40;SQL Server&#41;](../../relational-databases/import-export/use-unicode-native-format-to-import-or-export-data-sql-server.md)」をご覧ください。|  
  
  ERRORFILE **='***file_name***'**  
 形式エラーがあり、OLE DB 行セットに変換できない行を収集するときに使用するファイルを指定します。 該当する行は、データ ファイルからこのエラー ファイルに "そのまま" コピーされます。  
  
 このエラー ファイルは、コマンドが実行されたときに作成されます。 ファイルが既に存在する場合はエラーが発生し、 拡張子 .ERROR.txt の制御ファイルが作成されます。 このファイルにはエラー ファイルの各行の参照と、エラーの診断が含まれています。 エラーが修正されるとすぐ、データは読み込み可能になります。   
**適用対象:** [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1.
以降で[!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)]、 `error_file_path` Azure blob ストレージにすることができます。

' errorfile_data_source_name'   
**適用対象:** [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1.
名前付きの外部データ ソースは、インポート中に見つかったエラーを格納するエラー ファイルの Azure Blob ストレージの場所を指しています。 使用して、外部データ ソースを作成する必要があります、`TYPE = BLOB_STORAGE`オプションで追加された[!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)]CTP 1.1 です。 詳細については、次を参照してください。 [CREATE EXTERNAL DATA SOURCE](../../t-sql/statements/create-external-data-source-transact-sql.md)です。
 
 FIRSTROW  **=**  *first_row*  
 読み込み開始行の行番号を指定します。 既定値は、指定されたデータ ファイルの先頭行です。 FIRSTROW は 1 から始まります。  
  
> [!NOTE]  
>  FIRSTROW 属性は、列ヘッダーのスキップを目的としたものではありません。 ヘッダーのスキップは、BULK INSERT ステートメントではサポートされません。 行をスキップした場合、[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]ではフィールド ターミネータのみが調べられます。スキップした行のフィールドに含まれているデータの有効性は確認されません。  
  
 FIRE_TRIGGERS  
 一括読み込みの操作中に、インポート先のテーブルで定義されている挿入トリガーを実行します。 対象テーブルで INSERT 操作にトリガーが定義されている場合、そのトリガーは完了した各バッチに対して実行されます。  
  
 FIRE_TRIGGERS が指定されていない場合、挿入トリガーは実行されません。  

FORMATFILE_DATASOURCE  **=**  'data_source_name'   
**適用されます:** [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] 1.1 です。   
名前付きの外部データ ソースは、インポートされたデータのスキーマを定義するフォーマット ファイルの Azure Blob ストレージの場所を指しています。 使用して、外部データ ソースを作成する必要があります、`TYPE = BLOB_STORAGE`オプションで追加された[!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)]CTP 1.1 です。 詳細については、次を参照してください。 [CREATE EXTERNAL DATA SOURCE](../../t-sql/statements/create-external-data-source-transact-sql.md)です。
  
 KEEPIDENTITY  
 インポートしたデータ ファイルの ID 値 (複数可) を ID 列に使用することを指定します。 この列の id 値を検証するがインポートされない KEEPIDENTITY を指定しない場合および[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]テーブル作成時に指定されたシードと増分値に基づいて一意の値を自動的に割り当てます。 データ ファイルにテーブルまたはビュー内の id 列の値が含まれていない場合は、フォーマット ファイルを使用して、テーブルまたはビュー内の id 列が、データをインポートするときにスキップすることを指定するには[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]列の一意の値を自動的に割り当てます。 詳細については、「[DBCC CHECKIDENT &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-checkident-transact-sql.md)」をご覧ください。  
  
 詳細については、保持するかを参照してください。 特定の値を参照してください[維持の Id 値とデータの一括インポート &#40;です。SQL Server &#41;](../../relational-databases/import-export/keep-identity-values-when-bulk-importing-data-sql-server.md).  
  
 KEEPNULLS  
 一括インポート操作時、空の列が挿入される場合は NULL 値が保持されます。その列の既定値は格納されません。 詳細については、「[一括インポート中の NULL の保持または既定値の使用 &#40;SQL Server&#41;](../../relational-databases/import-export/keep-nulls-or-use-default-values-during-bulk-import-sql-server.md)」をご覧ください。  
  
 KILOBYTES_PER_BATCH  **=**  *kilobytes_per_batch*  
 バッチごとのデータのキロバイト (KB) のおおよその数を指定*kilobytes_per_batch*です。 KILOBYTES_PER_BATCH の既定値はありません。 パフォーマンスに関する考慮事項については、後の「解説」を参照してください。  
  
 LASTROW**=***last_row*  
 読み込み終了行の行番号を指定します。 既定値は 0 で、これは指定のデータ ファイルの最終行を表します。  
  
 MAXERRORS  **=**  *max_errors*  
 一括インポート操作時に許容されるデータの構文エラーの最大数を指定します。この最大数に達すると、操作は取り消されます。 一括インポート操作でインポートできない行は無視され、それぞれ 1 つのエラーとしてカウントされます。 場合*max_errors*が指定されていない、既定値は 10 です。  
  
> [!NOTE]  
>  MAX_ERRORS オプションは、制約チェックや変換には適用されません**money**と**bigint**データ型。  
  
 順序 ({*列*[ASC |DESC]} [ **、**.*n* ] )  
 データ ファイル内のデータの並べ替え方法を指定します。 インポートするデータをテーブル上のクラスター化インデックスに従って並べ替えると、一括インポートのパフォーマンスが向上します。 データ ファイルが異なる順序で並んでいる場合、つまりクラスター化インデックス キーの順序以外の順で並んでいるか、テーブルにクラスター化インデックスが存在しない場合、ORDER 句は無視されます。 指定する列の名前は、インポート先のテーブル内で有効な列の名前であることが必要です。 既定では、一括挿入操作はデータ ファイルが並べ替えられていないことを前提に実行されます。 最適な一括インポートのため、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、インポートするデータが並べ替えられているかどうかも検証されます。  
  
 *n*  
 複数の列を指定できることを示すプレースホルダーです。  
  
 ROWS_PER_BATCH  **=**  *rows_per_batch*  
 データ ファイル内のデータの行の概数を示します。  
  
 既定では、データ ファイル内のすべてのデータは単一のトランザクションとしてサーバーに送られ、バッチ内の行数はクエリ オプティマイザーには通知されません。 ROWS_PER_BATCH を値 > 0 で指定した場合、サーバーでは一括インポート操作の最適化にこの値が使用されます。 ROWS_PER_BATCH に指定する値は、実際の行数とほぼ同じにする必要があります。 パフォーマンスに関する考慮事項については、後の「解説」を参照してください。  
  
 
 TABLOCK  
 一括インポート操作中にテーブル レベルのロックを取得します。 テーブルにインデックスがなく、TABLOCK を指定した場合は、複数のクライアントで同時に 1 つのテーブルを読み込むことができます。 既定では、ロック動作はテーブル オプション **table lock on bulk load**によって決定されます。 一括インポート操作中にロックを維持すると、テーブル ロックの競合が少なくなるので、場合によってはパフォーマンスが大幅に向上します。 パフォーマンスに関する考慮事項については、後の「解説」を参照してください。  
  
 列ストア インデックスです。 複数の行セットに内部的に分かれているために、ロックの動作が異なります。  各スレッドは、同時実行データ読み込みのセッションで並列のデータの読み込みを許可する行セットで X ロックを取得して、それぞれの行セットに排他的にデータを読み込みます。 TABLOCK オプションの使用には、他の同時実行スレッドを同時にデータを読み込むようにする (従来の行セットの BU ロック) とは異なり、テーブルで、X ロックを実行するスレッドになります。  

### <a name="input-file-format-options"></a>入力ファイル形式のオプション
  
形式 **=**  'CSV'   
**適用対象:** [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1.   
準拠しているコンマ区切り値ファイルを指定します、 [RFC 4180](https://tools.ietf.org/html/rfc4180)標準です。

FIELDQUOTE  **=**  'field_quote'   
**適用対象:** [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1.   
CSV ファイルの引用符の文字として使用される文字を指定します。 指定されていない場合で定義されている、引用符の文字として引用符文字 (") を使用、 [RFC 4180](https://tools.ietf.org/html/rfc4180)標準です。
  
 FORMATFILE **='***format_file_path***'**  
 フォーマット ファイルの完全パスを指定します。 フォーマット ファイルを使用して作成された、格納された応答を含むデータ ファイルの説明、 **bcp**同じテーブルまたはビュー上のユーティリティ。 フォーマット ファイルは次の場合に使用します。  
  
-   データ ファイルに含まれる列の数が、テーブルまたはビューより多い、または少ない。  
  
-   列の順序が異なる。  
  
-   列の区切り記号が異なる。  
  
-   データ形式に他に異なる点がある。 フォーマット ファイルは、通常を使用して作成、 **bcp**ユーティリティし、必要に応じてテキスト エディターで修正します。 詳細については、「 [bcp Utility](../../tools/bcp-utility.md)」を参照してください。  

**適用対象:** [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1.   
以降で[!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)]CTP 1.1、format_file_path は Azure blob ストレージにすることができます。

 FIELDTERMINATOR **='***field_terminator***'**  
 使用されるフィールド ターミネータを指定します**char**と**widechar**データ ファイル。 既定のフィールド ターミネータは \t (タブ文字) です。 詳細については、「 [フィールド ターミネータと行ターミネータの指定 &#40;SQL Server&#41;](../../relational-databases/import-export/specify-field-and-row-terminators-sql-server.md)」を参照してください。  

 ROWTERMINATOR **='***row_terminator***'**  
 使用される行ターミネータを指定します**char**と**widechar**データ ファイル。 既定の行ターミネータは**\r\n** (改行文字)。  詳細については、「 [フィールド ターミネータと行ターミネータの指定 &#40;SQL Server&#41;](../../relational-databases/import-export/specify-field-and-row-terminators-sql-server.md)」を参照してください。  

  
## <a name="compatibility"></a>互換性  
 BULK INSERT によって、ファイルから読み込んだデータに対して厳密なデータ検証とデータ チェックが実行されるので、無効なデータを使用して既存のスクリプトを実行すると、スクリプトは失敗する可能性があります。 たとえば、BULK INSERT では次の検証が行われます。  
  
-   ネイティブ表記**float**または**実際**データ型が無効です。  
  
-   Unicode データが偶数バイト長かどうか。  
  
## <a name="data-types"></a>データ型  
  
### <a name="string-to-decimal-data-type-conversions"></a>文字列から 10 進数へのデータ型変換  
 BULK INSERT で使用される 10 進数の文字列データ型変換と同じ規則に従います、 [!INCLUDE[tsql](../../includes/tsql-md.md)] [変換](../../t-sql/functions/cast-and-convert-transact-sql.md)関数で、科学的表記法を使用して数値を表す文字列を拒否します。 したがって、BULK INSERT を実行するときに、そのような文字列が無効な値として評価され、変換エラーが報告されます。  
  
 この動作を回避するには、一括インポートの科学的表記法、フォーマット ファイルを使用**float** 10 進数の列へのデータ。 フォーマット ファイルで明示的に記述する列として**実際**または**float**データ。 これらのデータ型の詳細については、次を参照してください。 [float、real および #40 です。TRANSACT-SQL と #41 です。](../../t-sql/data-types/float-and-real-transact-sql.md).  
  
> [!NOTE]  
>  フォーマット ファイル**実際**データとして、 **SQLFLT4**データ型と**float**データとして、 **SQLFLT8**データ型。 XML 以外のフォーマット ファイルについては、次を参照してください[bcp &#40; を使用して、ファイル ストレージ型の指定。SQL Server &#41;](../../relational-databases/import-export/specify-file-storage-type-by-using-bcp-sql-server.md).  
  
#### <a name="example-of-importing-a-numeric-value-that-uses-scientific-notation"></a>科学的表記法を使用した数値をインポートする例  
 この例では、次のテーブルを使用します。  
  
```  
CREATE TABLE t_float(c1 float, c2 decimal (5,4));  
```  
  
 ユーザーの一括たいデータのインポート、`t_float`テーブル。 データ ファイル C:\t_float-c.dat には、科学的表記法が含まれています。 **float**データ; 例。  
  
```  
8.0000000000000002E-28.0000000000000002E-2  
```  
  
 しかし、テーブルの 2 番目の列 `t_float` で `c2` データ型を使用しているので、このデータを BULK INSERT によって `decimal` に直接インポートすることはできません。 そのため、フォーマット ファイルが必要です。 フォーマット ファイルは、科学的表記法をマップする必要があります**float**列の 10 進数形式にデータを`c2`です。  
  
 次のフォーマット ファイルでは、`SQLFLT8`データ型に 2 番目のデータ フィールドを 2 番目の列にマップします。  
  
 ```
 <?xml version="1.0"?> 
 <BCPFORMAT xmlns="http://schemas.microsoft.com/sqlserver/2004/bulkload/format" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"> 
 <RECORD> 
 <FIELD ID="1" xsi:type="CharTerm" TERMINATOR="\t" MAX_LENGTH="30"/> 
 <FIELD ID="2" xsi:type="CharTerm" TERMINATOR="\r\n" MAX_LENGTH="30"/>  </RECORD>  <ROW> 
 <COLUMN SOURCE="1" NAME="c1" xsi:type="SQLFLT8"/> 
 <COLUMN SOURCE="2" NAME="c2" xsi:type="SQLFLT8"/>  </ROW> </BCPFORMAT> 
 ```
  
 このフォーマット ファイル (ファイル名 `C:\t_floatformat-c-xml.xml`) を使用してテスト テーブルにテスト データをインポートするには、次の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを実行します。  
  
```  
BULK INSERT bulktest..t_float  
FROM 'C:\t_float-c.dat' WITH (FORMATFILE='C:\t_floatformat-c-xml.xml');  
GO  
```  
  
### <a name="data-types-for-bulk-exporting-or-importing-sqlxml-documents"></a>SQLXML ドキュメントの一括エクスポートまたは一括インポート用のデータ型  
 SQLXML データを一括エクスポートまたは一括インポートするには、フォーマット ファイルで次のいずれかのデータ型を使用します。  
  
|データ型|結果|  
|---------------|------------|  
|SQLCHAR または SQLVARCHAR|データは、クライアント コード ページまたは照合順序で暗黙的に指定されるコード ページで送られます。 効果は DATAFILETYPE を指定すると同じ**= 'char'**フォーマット ファイルを指定せずします。|  
|SQLNCHAR または SQLNVARCHAR|データは Unicode として送られます。 効果は DATAFILETYPE を指定すると同じ**= 'widechar'**フォーマット ファイルを指定せずします。|  
|SQLBINARY または SQLVARBIN|データは変換なしで送られます。|  
  
## <a name="general-remarks"></a>全般的な解説  
 BULK INSERT ステートメント、INSERT ... 選択\*openrowset (bulk) からステートメントでは、および**bcp**コマンドを参照してください[一括インポートし、データ ファイルのエクスポート &#40;です。SQL Server &#41;](../../relational-databases/import-export/bulk-import-and-export-of-data-sql-server.md).  
  
 データを一括インポートの準備については、次を参照してください[データを一括エクスポートまたはインポート &#40; を準備する。SQL Server &#41;](../../relational-databases/import-export/prepare-data-for-bulk-export-or-import-sql-server.md).  
  
 BULK INSERT ステートメントは、テーブルまたはビューにデータをインポートするために、ユーザー定義のトランザクション内で実行できます。 必要に応じて、一括インポート データの複数の一致を使用するために、トランザクションは BULK INSERT ステートメントで BATCHSIZE 句を指定できます。 複数のバッチのトランザクションがロールバックされた場合、トランザクションに送信したすべてのバッチ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]がロールバックされます。  
  
## <a name="interoperability"></a>相互運用性  
  
### <a name="importing-data-from-a-csv-file"></a>CSV ファイルからのデータのインポート  
以降で[!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)]CTP 1.1、一括挿入は、CSV 形式をサポートしています。  
前に[!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)]CTP 1.1 でコンマ区切り値 (CSV) ファイルはサポートされていない[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]一括インポート操作します。 ただし、場合によっては、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に対してデータを一括インポートする際、CSV ファイルをデータ ファイルとして使用できます。 CSV データ ファイルからデータをインポートするための要件については、次を参照してください[一括エクスポートまたは一括インポートのデータの準備 &#40;SQL Server&#41;](../../relational-databases/import-export/prepare-data-for-bulk-export-or-import-sql-server.md).  
  
## <a name="logging-behavior"></a>ログ記録の動作  
 一括インポートによって実行される行挿入操作がトランザクション ログに記録される条件について詳しくは、「[一括インポートで最小ログ記録を行うための前提条件](../../relational-databases/import-export/prerequisites-for-minimal-logging-in-bulk-import.md)」をご覧ください。  
  
##  <a name="Limitations"></a> 制限  
 BULK INSERT でフォーマット ファイルを使用する場合、指定できるフィールド数は 1,024 個までです。 これは、テーブルに許容される最大列数と同じです。 1,024 個を超えるフィールドが含まれるデータ ファイルで BULK INSERT を使用すると、BULK INSERT によってエラー 4822 が生成されます。 [Bcp ユーティリティ](../../tools/bcp-utility.md)されていませんこの制限がある、そのため、1,024 個を超えるフィールドを含むデータ ファイルの使用、 **bcp**コマンド。  
  
## <a name="performance-considerations"></a>パフォーマンスに関する考慮事項  
 1 つのバッチでフラッシュされるページの数が内部しきい値を超えると、バッチのコミット時にフラッシュするページを特定するためにバッファー プールのフル スキャンが行われる可能性があります。 フル スキャンが行われると、一括インポートのパフォーマンスが低下します。 この内部しきい値の問題は、大きなバッファー プールと遅い I/O サブシステムの組み合わせでも発生します。 大規模なコンピューターでバッファー オーバーフローを防ぐには、TABLOCK ヒントを使用しないようにするか (一括インポートの最適化は行われなくなります)、バッチ サイズを小さくします (一括インポートの最適化は引き続き行われます)。  
  
 コンピューターはそれぞれ異なるため、実際のデータでさまざまなバッチ サイズを試して最適な値を見つけるようにすることをお勧めします。  
  
## <a name="security"></a>セキュリティ  
  
### <a name="security-account-delegation-impersonation"></a>セキュリティ アカウントの委任 (権限借用)  
 ユーザーが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインを使用する場合は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] プロセス アカウントのセキュリティ プロファイルが使用されます。 SQL Server 認証を使用したログインは、データベース エンジン以外では認証できません。 そのため、SQL Server 認証を使用したログインによって BULK INSERT コマンドが開始されると、SQL Server プロセス アカウント (SQL Server データベース エンジン サービスで使用されるアカウント) のセキュリティ コンテキストを使用してデータへの接続が行われます。 ソース データを正しく読み取るには、SQL Server データベース エンジンで使用されるアカウントに対して、ソース データへのアクセス権を付与する必要があります。これに対して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーザーが Windows 認証を使用してログインした場合、そのユーザーは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] プロセスのセキュリティ プロファイルに関係なく、そのユーザー アカウントでアクセス可能なファイルのみを読み取ることができます。  
  
 使用して BULK INSERT ステートメントを実行するときに**sqlcmd**または**osql**、1 台のコンピューターからデータを挿入[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]別のコンピューターを指定して、 *data_file* UNC パスを使用して 3 番目のコンピューターで 4861 エラーが発生する可能性があります。  
  
 このエラーを解決するには、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証を指定し、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のセキュリティ プロファイルを使用するログインを[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]プロセス アカウント、または Windows セキュリティ アカウントの委任を有効にするを構成します。 ユーザー アカウントの信頼性を委任の対象として有効にする方法の詳細については、Windows ヘルプを参照してください。  
  
 このおよび BULK INSERT を使用するための他のセキュリティの考慮事項に関する詳細については、次を参照してください[を使用して BULK INSERT または OPENROWSET &#40; した一括データのインポート。BULK..."&"#41;&#40;です。SQL Server &#41;](../../relational-databases/import-export/import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md).  
  
### <a name="permissions"></a>Permissions  
 INSERT および ADMINISTER BULK OPERATIONS 権限が必要です。 ただし次の操作を 1 つ以上行う場合は、さらに ALTER TABLE 権限が必要になります。  
  
-   制約が存在する場合に、CHECK_CONSTRAINTS オプションを指定しない。  
  
    > [!NOTE]  
    >  制約の無効化は既定の動作です。 制約を明示的に検証するには、CHECK_CONSTRAINTS オプションを使用します。  
  
-   トリガーが存在する場合に、FIRE_TRIGGER オプションを指定しない。  
  
    > [!NOTE]  
    >  既定では、トリガーは起動しません。 トリガーを明示的に起動するには、FIRE_TRIGGERS オプションを使用します。  
  
-   KEEPIDENTITY オプションを使用して、データ ファイルから ID 値をインポートする。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-using-pipes-to-import-data-from-a-file"></a>A. ファイルからのデータのインポートにパイプを使用する  
 次の例に、注文明細情報のインポート、 `AdventureWorks2012.Sales.SalesOrderDetail` 、パイプを使用して、指定されたデータ ファイルからテーブル (`|`)、フィールド ターミネータとしてと`|\n`行ターミネータとして。  
  
```  
BULK INSERT AdventureWorks2012.Sales.SalesOrderDetail  
   FROM 'f:\orders\lineitem.tbl'  
   WITH   
      (  
         FIELDTERMINATOR =' |',  
         ROWTERMINATOR =' |\n'  
      );  
```  
  
### <a name="b-using-the-firetriggers-argument"></a>B. FIRE_TRIGGERS 引数を使用する  
 次の例では、`FIRE_TRIGGERS` 引数を指定します。  
  
```  
BULK INSERT AdventureWorks2012.Sales.SalesOrderDetail  
   FROM 'f:\orders\lineitem.tbl'  
   WITH  
     (  
        FIELDTERMINATOR =' |',  
        ROWTERMINATOR = ':\n',  
        FIRE_TRIGGERS  
      );  
```  
  
### <a name="c-using-line-feed-as-a-row-terminator"></a>C. 行ターミネータとしてライン フィードを使用する  
 次の例では、UNIX 出力などのように、ライン フィードを行ターミネータとして使用するファイルをインポートします。  
  
```  
DECLARE @bulk_cmd varchar(1000);  
SET @bulk_cmd = 'BULK INSERT AdventureWorks2012.Sales.SalesOrderDetail  
FROM ''<drive>:\<path>\<filename>''   
WITH (ROWTERMINATOR = '''+CHAR(10)+''')';  
EXEC(@bulk_cmd);  
```  
  
> [!NOTE]  
>  Microsoft Windows によるテキスト ファイルの処理方法によって**(\n**自動的に置き換え**\r\n)**です。  
  
### <a name="d-specifying-a-code-page"></a>D. コード ページの指定  
 次の例では、コード ページを指定する方法を示します。  
  
```  
BULK INSERT MyTable  
FROM 'D:\data.csv'  
WITH  
( CODEPAGE = '65001',  
    DATAFILETYPE = 'char',  
    FIELDTERMINATOR = ','  
);  
```  
### <a name="e-importing-data-from-a-csv-file"></a>E. CSV ファイルからデータをインポートします。   
次の例では、CSV ファイルを指定する方法を示します。   
```
BULK INSERT Sales.Invoices
FROM '\\share\invoices\inv-2016-07-25.csv'
WITH (FORMAT = 'CSV'); 
```

### <a name="f-importing-data-from-a-file-in-azure-blob-storage"></a>F. Azure blob ストレージ内のファイルからデータをインポートします。   
次の例は、Azure blob ストレージの場所に、外部データ ソースとして構成されている csv ファイルからデータを読み込む方法を示します。 これには、共有アクセス署名を使用してデータベース スコープ資格情報が必要です。    

```tsql
BULK INSERT Sales.Invoices
FROM 'inv-2017-01-19.csv'
WITH (DATA_SOURCE = 'MyAzureInvoices',
     FORMAT = 'CSV'); 
```

完了`BULK INSERT`資格情報と外部データ ソースの構成などの例を参照してください[例の一括データにアクセスする Azure Blob ストレージに](../../relational-databases/import-export/examples-of-bulk-access-to-data-in-azure-blob-storage.md)です。
  
### <a name="additional-examples"></a>その他の例  
 その他の`BULK INSERT`例については、次のトピックで説明します。  
  
-   [XML ドキュメントの一括インポートと一括エクスポートの例 &#40;SQL Server&#41;](../../relational-databases/import-export/examples-of-bulk-import-and-export-of-xml-documents-sql-server.md)  
  
-   [データの一括インポート時の ID 値の保持 &#40;SQL Server&#41;](../../relational-databases/import-export/keep-identity-values-when-bulk-importing-data-sql-server.md)  
  
-   [一括インポート中の NULL の保持または既定値の使用 &#40;SQL Server&#41;](../../relational-databases/import-export/keep-nulls-or-use-default-values-during-bulk-import-sql-server.md)  
  
-   [フィールド ターミネータと行ターミネータの指定 &#40;SQL Server&#41;](../../relational-databases/import-export/specify-field-and-row-terminators-sql-server.md)  
  
-   [データの一括インポートでのフォーマット ファイルの使用 &#40;SQL Server&#41;](../../relational-databases/import-export/use-a-format-file-to-bulk-import-data-sql-server.md)  
  
-   [文字形式を使用したデータのインポートまたはエクスポート &#40;SQL Server&#41;](../../relational-databases/import-export/use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [ネイティブ形式を使用したデータのインポートまたはエクスポート &#40;SQL Server&#41;](../../relational-databases/import-export/use-native-format-to-import-or-export-data-sql-server.md)  
  
-   [Unicode 文字形式を使用したデータのインポートまたはエクスポート &#40;SQL Server&#41;](../../relational-databases/import-export/use-unicode-character-format-to-import-or-export-data-sql-server.md)  
  
-   [Unicode ネイティブ形式を使用したデータのインポートまたはエクスポート &#40;SQL Server&#41;](../../relational-databases/import-export/use-unicode-native-format-to-import-or-export-data-sql-server.md)  
  
-   [フォーマット ファイルを使用したテーブル列のスキップ &#40;SQL Server&#41;](../../relational-databases/import-export/use-a-format-file-to-skip-a-table-column-sql-server.md)  
  
-   [フォーマット ファイルを使用したテーブル列とデータ ファイル フィールドのマッピング &#40;SQL Server&#41;](../../relational-databases/import-export/use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md)  
  
## <a name="see-also"></a>参照  
 [データの一括インポートと一括エクスポート &#40;SQL Server&#41;](../../relational-databases/import-export/bulk-import-and-export-of-data-sql-server.md)   
 [bcp Utility](../../tools/bcp-utility.md)   
 [インポートまたはエクスポート データ &#40; 用のフォーマット ファイルSQL Server &#41;](../../relational-databases/import-export/format-files-for-importing-or-exporting-data-sql-server.md)   
 [INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/insert-transact-sql.md)   
 [OPENROWSET &#40;Transact-SQL&#41;](../../t-sql/functions/openrowset-transact-sql.md)   
 [一括エクスポートまたはインポート &#40; のデータを準備します。SQL Server &#41;](../../relational-databases/import-export/prepare-data-for-bulk-export-or-import-sql-server.md)   
 [sp_tableoption &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-tableoption-transact-sql.md)  
  
  

