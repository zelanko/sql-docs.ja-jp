---
title: "OPENROWSET (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/09/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- OPENROWSET_TSQL
- OPENROWSET
dev_langs:
- TSQL
helpviewer_keywords:
- data sources [SQL Server]
- OPENROWSET function
- remote data access [SQL Server], OPENROWSET
- ad hoc distributed queries
- OPENROWSET function, Transact-SQL
- OPENROWSET statement
- OLE DB data sources [SQL Server]
- ad hoc connection information
ms.assetid: f47eda43-33aa-454d-840a-bb15a031ca17
caps.latest.revision: 130
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 3c23ec85299af595305a5f6d5141dbbf3ffab96d
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="openrowset-transact-sql"></a>OPENROWSET (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  OLE DB データ ソースからリモート データへのアクセスに必要な、すべての接続情報をインクルードします。 これは、リンク サーバー内のテーブルにアクセスする代わりに、OLE DB を使用してリモート データに接続しアクセスする特別な方法です。 OLE DB データ ソースをより頻繁に参照する場合は、代わりにリンク サーバーを使用してください。 詳しくは、「 [リンク サーバー &#40;データベース エンジン&#41;](../../relational-databases/linked-servers/linked-servers-database-engine.md)」を参照してください。 `OPENROWSET`関数は、テーブル名の場合と同様、クエリの FROM 句で参照できます。 `OPENROWSET`関数は、の対象のテーブルとしても参照できます、 `INSERT`、 `UPDATE`、または`DELETE`ステートメントでは、OLE DB プロバイダーの機能により制限されます。 クエリは、複数の結果セットを返す可能性があります`OPENROWSET`最初の 1 つだけ返されます。  
  
 `OPENROWSET`読み取りと行セットとして返されるファイルからデータを有効にする組み込みの BULK プロバイダーによる一括操作もサポートしています。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
OPENROWSET   
( { 'provider_name' , { 'datasource' ; 'user_id' ; 'password'   
   | 'provider_string' }   
   , {   [ catalog. ] [ schema. ] object   
       | 'query'   
     }   
   | BULK 'data_file' ,   
       { FORMATFILE = 'format_file_path' [ <bulk_options> ]  
       | SINGLE_BLOB | SINGLE_CLOB | SINGLE_NCLOB }  
} )   
  
<bulk_options> ::=  
   [ , CODEPAGE = { 'ACP' | 'OEM' | 'RAW' | 'code_page' } ]   
   [ , DATASOURCE = 'data_source_name' ]
   [ , ERRORFILE = 'file_name' ]  
   [ , ERRORFILE_DATASOURCE = 'data_source_name' ]   
   [ , FIRSTROW = first_row ]   
   [ , LASTROW = last_row ]   
   [ , MAXERRORS = maximum_errors ]   
   [ , ROWS_PER_BATCH = rows_per_batch ]  
   [ , ORDER ( { column [ ASC | DESC ] } [ ,...n ] ) [ UNIQUE ] ]
  
   -- bulk_options related to input file format
   [ , FORMAT = 'CSV' ]
   [ , FIELDQUOTE = 'quote_characters']
   [ , FORMATFILE = 'format_file_path' ]   
```

  
## <a name="arguments"></a>引数  
 '*provider_name*'  
 レジストリの OLE DB プロバイダーの表示名 (または PROGID) を表す文字列を指定します。 *provider_name*既定値はありません。  
  
 '*データソース*'  
 特定の OLE DB データ ソースに対応する文字列定数を指定します。 *datasource*プロバイダーを初期化するためにプロバイダーの IDBProperties インターフェイスに渡される DBPROP_INIT_DATASOURCE プロパティです。 一般的に、この文字列にはデータベース ファイルの名前、データベース サーバーの名前、プロバイダーがデータベースを検索する際に認識する名前のいずれかを指定します。  
  
 '*user_id*'  
 指定した OLE DB プロバイダーに渡されるユーザー名を表す文字列定数を指定します。 *user_id*接続のセキュリティ コンテキストを指定し、プロバイダーを初期化するために、DBPROP_AUTH_USERID プロパティとして渡されます。 *user_id* Microsoft Windows のログイン名をすることはできません。  
  
 '*パスワード*'  
 OLE DB プロバイダーに渡されるユーザー パスワードを表す文字列定数を指定します。 *パスワード*として渡される DBPROP_AUTH_PASSWORD プロパティ プロバイダーを初期化するときにします。 *パスワード*Microsoft Windows のパスワードをすることはできません。  
  
 '*provider_string*'  
 プロバイダー固有の接続文字列を指定します。DBPROP_INIT_PROVIDERSTRING プロパティとして渡され、プロバイダーの初期化に使用されます。 *provider_string*通常、プロバイダーを初期化するために必要なすべての接続情報をカプセル化します。 によって認識されるキーワードの一覧については、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーを参照してください[初期化プロパティと承認プロパティ](../../relational-databases/native-client-ole-db-data-source-objects/initialization-and-authorization-properties.md)です。  
  
 *カタログ*  
 指定したオブジェクトが存在するカタログまたはデータベースの名前を指定します。  
  
 *スキーマ*  
 指定したオブジェクトのスキーマまたはオブジェクト所有者の名前を指定します。  
  
 *オブジェクト*  
 操作するオブジェクトを一意に識別するオブジェクト名を指定します。  
  
 '*クエリ*'  
 プロバイダーに送られ、プロバイダーによって実行される文字列定数を指定します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のローカル インスタンスでは、このクエリは処理されず、プロバイダーから返されたクエリ結果が処理されます (パススルー クエリ)。 パススルー クエリは、表形式のデータをテーブル名ではなくコマンド言語のみで公開するプロバイダーで使用すると便利です。 パススルー クエリは、クエリ プロバイダーは、OLE DB コマンド オブジェクトとその必須インターフェイスをサポートしている限り、リモート サーバーでサポートされます。 詳細については、次を参照してください[SQL Server Native Client &#40;OLE DB"&"#41;。参照](../../relational-databases/native-client-ole-db-interfaces/sql-server-native-client-ole-db-interfaces.md)です。  
  
 BULK  
 ファイルからのデータ読み取りに OPENROWSET の BULK 行セット プロバイダーを使用します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、OPENROWSET を使用すると、データを対象テーブルに読み込むことなくデータ ファイルからの読み取りができます。 このため、OPENROWSET は簡単な SELECT ステートメントで使用できます。  
  
 BULK オプションの引数を使用すると、データの読み取りを開始および終了する場所や、エラーの取り扱い、データの解釈方法について、細かく制御することができます。 データ ファイルは、型の単一行、単一列の行セットとして読み取ることを指定するたとえば、 **varbinary**、 **varchar**、または**nvarchar**です。 既定の動作については、後の引数の説明を参照してください。  
  
 BULK オプションの使用方法の詳細については、後の「解説」を参照してください。 BULK オプションに必要な権限については、後の「権限」を参照してください。  
  
> [!NOTE]  
>  OPENROWSET (BULK ...) を完全復旧モデルでデータのインポートに使用する場合、ログ記録は最適化されません。  
  
 一括インポートのデータを準備する方法については、次を参照してください[データを一括エクスポートまたはインポート &#40; を準備しますSQL Server &#41;](../../relational-databases/import-export/prepare-data-for-bulk-export-or-import-sql-server.md).  
  
 '*data_file*'  
 データを対象テーブルにコピーするデータ ファイルの完全なパスを指定します。   
 **適用対象:** [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1.   
以降で[!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)]CTP 1.1、data_file は、Azure ブログの記憶域にすることができます。 例については、次を参照してください。[例の一括データにアクセスする Azure Blob ストレージに](../../relational-databases/import-export/examples-of-bulk-access-to-data-in-azure-blob-storage.md)です。
  
 \<bulk_options >  
 BULK オプションの引数を 1 つ以上指定します。  
  
 CODEPAGE = {'ACP' |'OEM' |'生' |*code_page*'}  
 データ ファイル内のデータのコード ページを指定します。 CODEPAGE は、データが含まれている場合にのみ関連する**char**、 **varchar**、または**テキスト**127 よりまたは 32 より小さい文字値を持つ列。  
  
> [!NOTE]  
>  65001 オプションを照合順序/コード ページ仕様よりも優先する場合を除く、フォーマット ファイル内の各列の照合順序名を指定することをお勧めします。  
  
|CODEPAGE の値|Description|  
|--------------------|-----------------|  
|ACP|列に変換**char**、 **varchar**、または**テキスト**データ型を ANSI/[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows コード ページ (ISO 1252) を[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]コード ページです。|  
|OEM (既定値)|列に変換**char**、 **varchar**、または**テキスト**システム OEM コード ページからのデータ型、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]コード ページです。|  
|RAW|別の 1 つのコード ページから変換は行われません。 これは最も高速なオプションです。|  
|*code_page*|データ ファイルの文字データのエンコードに使用されているソースのコード ページを示します (例 : 850)。<br /><br /> **\*\*重要な\* \*** より前のバージョン[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]コード ページ 65001 (utf-8 エンコード) をサポートしていません。|  
  
 ERRORFILE ='*file_name*'  
 形式エラーがあり、OLE DB 行セットに変換できない行を収集するときに使用するファイルを指定します。 該当する行は、データ ファイルからこのエラー ファイルに "そのまま" コピーされます。  
  
 エラー ファイルはコマンドの実行開始時に作成されます。 存在するファイルの場合にはエラーが発生し、 拡張子 .ERROR.txt の制御ファイルが作成されます。 このファイルにはエラー ファイルの各行と、エラーの診断が含まれています。 エラーが修正されると、データは読み込み可能になります。  
**適用対象:** [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1.
以降で[!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)]、 `error_file_path` Azure ブログの記憶域にすることができます。 

' errorfile_data_source_name'   
**適用対象:** [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1.
名前付きの外部データ ソースは、インポート中に見つかったエラーを格納するエラー ファイルの Azure Blob ストレージの場所を指しています。 使用して、外部データ ソースを作成する必要があります、`TYPE = BLOB_STORAGE`オプションで追加された[!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)]CTP 1.1 です。 詳細については、次を参照してください。 [CREATE EXTERNAL DATA SOURCE](../../t-sql/statements/create-external-data-source-transact-sql.md)です。
  
 FIRSTROW =*first_row*  
 読み込み開始行の行番号を指定します。 既定値は、1 です。 指定したデータ ファイルの最初の行を示します。 行番号は行ターミネータの数をカウントして決定されます。 FIRSTROW は 1 から始まります。  
  
 LASTROW =*last_row*  
 読み込み終了行の行番号を指定します。 既定値は 0 です。 指定したデータ ファイルの最後の行を示します。  
  
 MAXERRORS =*maximum_errors*  
 フォーマット ファイルで定義されている、構文エラーまたは違反行の許容最大数を指定します。この数を超えると、OPENROWSET で例外が発生します。 OPENROWSET は、違反行を読み込まずに無視し、MAXERRORS に達するまで、違反行はエラーとしてカウントされます。  
  
 既定の*maximum_errors* 10 です。  
  
> [!NOTE]  
>  MAX_ERRORS は CHECK 制約、または変換するのには当てはまりません**money**と**bigint**データ型。  
  
 ROWS_PER_BATCH =*rows_per_batch*  
 データ ファイル内にあるデータ行の概算数を指定します。 この値は実際の行数と同じ次数にする必要があります。  
  
 OPENROWSET では、常にデータ ファイルが単一のバッチとしてインポートされますが、 ただし、指定した場合*rows_per_batch*クエリ プロセッサがの値を使用する値 > 0、 *rows_per_batch*クエリ プランでリソースを割り当てるためのヒントとして。  
  
 ROWS_PER_BATCH の既定値はありません。 ROWS_PER_BATCH = 0 は、ROWS_PER_BATCH を省略した場合と同じになります。  
  
 順序 ({*列*[ASC |DESC]} [,... *n*  ] [UNIQUE])  
 データ ファイル内のデータの並べ替え方法を指定するオプションのヒント。 既定では、一括操作はデータ ファイルが並べ替えられていないことを前提に実行されます。 指定された順序を利用してクエリ オプティマイザーでより効率的なクエリ プランを生成することができる場合、パフォーマンスが向上する可能性があります。 並べ替えの指定は、次の場合に役立ちます。  
  
-   クラスター化インデックスを持ち、クラスター化インデックス キーで行セット データが並べ替えられているテーブルに行を挿入する場合。  
  
-   行セットを別のテーブルに結合するとき、並べ替え列と結合列が一致する場合。  
  
-   並べ替え列で行セット データを集約する場合。  
  
-   クエリの FROM 句で行セットをソース テーブルとして使用するとき、並べ替え列と結合列が一致する場合。  
  
 UNIQUE は、データ ファイルに重複したエントリがないことを指定します。  
  
 データ ファイル内の実際の行が指定の順序で並べ替えられていない場合、または UNIQUE ヒントが指定された一方で重複したキーが存在する場合は、エラーが返されます。  
  
 ORDER を使用する場合は列の別名が必要です。 列の別名リストは、BULK 句によってアクセスされる派生テーブルを参照する必要があります。 ORDER 句に指定された列名は、この列の別名リストを参照します。 大きな値の型 (**varchar (max)**、 **nvarchar (max)**、 **varbinary (max)**、および**xml**) およびラージ オブジェクト (LOB) 型 (**テキスト**、 **ntext**、および**イメージ**) 列を指定することはできません。  
  
 SINGLE_BLOB  
 内容を返します*data_file*型の単一行、単一列の行セットとして**varbinary (max)**です。  
  
> [!IMPORTANT]  
>  すべての Windows エンコード変換がサポートされるのは SINGLE_BLOB オプションだけなので、SINGLE_CLOB オプションや SINGLE_NCLOB オプションではなく、SINGLE_BLOB オプションだけを使用して XML データをインポートすることをお勧めします。  
  
 SINGLE_CLOB  
 読み取って*data_file* 、ASCII として型の単一行、単一列の行セットとして内容を返します**varchar (max)**、現在のデータベースの照合順序を使用します。  
  
 SINGLE_NCLOB  
 読み取って*data_file* UNICODE として型の単一行、単一列の行セットとして内容を返します**nvarchar (max)**、現在のデータベースの照合順序を使用します。  

### <a name="input-file-format-options"></a>入力ファイル形式のオプション
  
形式 **=**  'CSV'   
**適用対象:** [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1.   
準拠しているコンマ区切り値ファイルを指定します、 [RFC 4180](https://tools.ietf.org/html/rfc4180)標準です。

 FORMATFILE ='*format_file_path*'  
 フォーマット ファイルの完全パスを指定します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2 つの種類のフォーマット ファイルをサポートしています。 XML と非 XML です。  
  
 フォーマット ファイルは、結果セットの列の型を定義する場合に必要となります。 ただし SINGLE_CLOB、SINGLE_BLOB、または SINGLE_NCLOB を指定した場合は例外で、この場合はフォーマット ファイルは必要ありません。  
  
 フォーマット ファイルについては、次を参照してください[データを一括インポート &#40; フォーマット ファイルの使用。SQL Server &#41;](../../relational-databases/import-export/use-a-format-file-to-bulk-import-data-sql-server.md).  

**適用対象:** [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1.   
以降で[!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)]CTP 1.1、format_file_path は、Azure ブログの記憶域にすることができます。 例については、次を参照してください。[例の一括データにアクセスする Azure Blob ストレージに](../../relational-databases/import-export/examples-of-bulk-access-to-data-in-azure-blob-storage.md)です。

FIELDQUOTE  **=**  'field_quote'   
**適用対象:** [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1.   
CSV ファイルの引用符の文字として使用される文字を指定します。 指定されていない場合で定義されている、引用符の文字として引用符文字 (") を使用、 [RFC 4180](https://tools.ietf.org/html/rfc4180)標準です。

  
## <a name="remarks"></a>解説  
 `OPENROWSET`リモート データにアクセスするために使用する OLE DB データ ソースから場合にのみ、 **DisallowAdhocAccess**レジストリ オプションが明示的に設定を 0 に、指定されたプロバイダーであり、Ad Hoc Distributed Queries 詳細構成オプション有効になります。 これらのオプションが設定されていない場合は、既定でアドホック接続は許可されません。  
  
 リモートの OLE DB データ ソースにアクセスするとき、信頼関係接続のログイン ID は、クライアントの接続先サーバーからクエリの対象サーバーに自動的に委任されるわけではありません。 したがって、認証の委任を構成する必要があります。  
  
 指定したデータ ソースにおいて、OLE DB プロバイダーが複数のカタログとスキーマをサポートする場合は、カタログ名とスキーマ名を指定する必要があります。 値を*カタログ*と*スキーマ*OLE DB プロバイダーではサポートしていない場合は省略できます。 プロバイダーは、スキーマ名の形式の 2 つの部分名をサポートしている場合*スキーマ***.***オブジェクト*指定する必要があります。 プロバイダーは、カタログ名の形式の 3 つの部分名をサポートしている場合*カタログ***.***スキーマ***.***オブジェクト*指定する必要があります。 パススルー クエリは、3 部構成の名前を指定する必要がありますを使用して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーです。 詳細については、次を参照してください。 [TRANSACT-SQL 構文表記規則 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md).  
  
 `OPENROWSET`変数、引数を受け入れられません。  
  
 すべての呼び出しに`OPENDATASOURCE`、 `OPENQUERY`、または`OPENROWSET`で、`FROM`句は評価とは別に、更新の対象として使用されるこれらの関数への呼び出しから同じ引数が 2 つの呼び出しに指定された場合でもです。 特に、いずれか一方の呼び出しの結果に適用されるフィルター条件または結合条件は、もう一方の結果に影響しません。  
  
## <a name="using-openrowset-with-the-bulk-option"></a>OPENROWSET を BULK オプションと共に使用する  
 次に示す [!INCLUDE[tsql](../../includes/tsql-md.md)] の機能拡張では、OPENROWSET(BULK...) 関数がサポートされます。  
  
-   FROM 句で使用される`SELECT`呼び出すことができます`OPENROWSET(BULK...)`テーブル名、完全ではなく`SELECT`機能します。  
  
     `OPENROWSET``BULK`オプションで、範囲変数または別名とも呼ばれる相関名が必要です、`FROM`句。 列には別名を指定できます。 列の別名のリストを指定しない場合は、フォーマット ファイルに列名が必要です。 次のように、列の別名を指定した場合は、フォーマット ファイルの列名よりも優先して使用されます。  
  
     `FROM OPENROWSET(BULK...) AS table_alias`  
  
     `FROM OPENROWSET(BULK...) AS table_alias(column_alias,...n)`  
>    [!IMPORTANT]  
>    エラーを追加する、`AS <table_alias>`エラーが発生します。    
>    Msg 491、レベル 16、状態 1、20 行目    
>    FROM 句の一括行セットには相関名を指定してください。    
  
-   A`SELECT...FROM OPENROWSET(BULK...)`ステートメントなしでクエリ ファイル内のデータを直接テーブルにデータをインポートします。 `SELECT…FROM OPENROWSET(BULK...)`ステートメントは、列名ともデータ型を指定するフォーマット ファイルを使用して、一括列の別名を一覧もできます。  
  
-   使用して`OPENROWSET(BULK...)`内でソース テーブルとして、`INSERT`または`MERGE`ステートメントの一括データ ファイルからのデータのインポート、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]テーブル。 詳細については、次を参照してください[を使用して BULK INSERT または OPENROWSET &#40; した一括データのインポート。BULK..."&"#41;&#40;です。SQL Server &#41;](../../relational-databases/import-export/import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md) .  
  
-   ときに、`OPENROWSET BULK`オプションを使用する`INSERT`ステートメントでは、BULK 句のテーブル ヒントをサポートしています。 テーブル ヒントなど、通常に加えて`TABLOCK`、`BULK`句は、次の特殊なテーブル ヒントを受け取ることができます: `IGNORE_CONSTRAINTS` (だけを無視、`CHECK`と`FOREIGN KEY`制約)、 `IGNORE_TRIGGERS`、 `KEEPDEFAULTS`、および`KEEPIDENTITY`です。 詳細については、「[テーブル ヒント &#40;Transact-SQL&#41;](../../t-sql/queries/hints-transact-sql-table.md)」を参照してください。  
  
 使用する方法については`INSERT...SELECT * FROM OPENROWSET(BULK...)`ステートメントを参照してください[一括インポートし、データ ファイルのエクスポート &#40;です。SQL Server &#41;](../../relational-databases/import-export/bulk-import-and-export-of-data-sql-server.md). 一括インポートによって実行される行挿入操作がトランザクション ログに記録される条件について詳しくは、「[一括インポートで最小ログ記録を行うための前提条件](../../relational-databases/import-export/prerequisites-for-minimal-logging-in-bulk-import.md)」をご覧ください。  
  
> [!NOTE]  
>  使用すると`OPENROWSET`、理解することが重要か[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]権限借用を処理します。 セキュリティに関する考慮事項については、次を参照してください[を使用して BULK INSERT または OPENROWSET &#40; した一括データのインポート。BULK..."&"#41;&#40;です。SQL Server &#41;](../../relational-databases/import-export/import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md).  
  
### <a name="bulk-importing-sqlchar-sqlnchar-or-sqlbinary-data"></a>SQLCHAR、SQLNCHAR、および SQLBINARY データの一括インポート  
 OPENROWSET(BULK...) では、指定がない場合、SQLCHAR、SQLNCHAR、および SQLBINARY データの最大の長さが 8000 バイトを超えないものと想定されます。 インポートされているデータを含む LOB データ フィールドに場合**varchar (max)**、 **nvarchar (max)**、または**varbinary (max)** 、8000 バイトを超えるオブジェクトが使用する必要があります、データ フィールドの最大長を定義する XML フォーマット ファイル。 最大の長さを指定するには、フォーマット ファイルを編集して MAX_LENGTH 属性を宣言します。  
  
> [!NOTE]  
>  自動生成されたフォーマット ファイルには、LOB フィールドの最大の長さの指定がありません。 ただし、手作業でフォーマット ファイルを編集して長さまたは最大の長さを指定できます。  
  
### <a name="bulk-exporting-or-importing-sqlxml-documents"></a>SQLXML ドキュメントの一括エクスポートまたは一括インポート  
 SQLXML データを一括エクスポートまたは一括インポートする場合、フォーマット ファイルのデータ型には次のいずれかを使用します。  
  
|データ型|結果|  
|---------------|------------|  
|SQLCHAR または SQLVARYCHAR|データは、クライアント コード ページまたは照合順序で暗黙的に指定されるコード ページで送られます。|  
|SQLNCHAR または SQLNVARCHAR|データは Unicode として送られます。|  
|SQLBINARY または SQLVARYBIN|データは変換なしで送られます。|  
  
## <a name="permissions"></a>Permissions  
 `OPENROWSET`アクセス許可は、OLE DB プロバイダーに渡されるユーザー名のアクセス許可によって決まります。 使用する、`BULK`オプションが必要です`ADMINISTER BULK OPERATIONS`権限です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-using-openrowset-with-select-and-the-sql-server-native-client-ole-db-provider"></a>A. OPENROWSET を SELECT および SQL Server Native Client OLE DB プロバイダーと共に使用する  
 次の例では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーへのアクセス、`HumanResources.Department`テーブルに、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]リモート サーバー上のデータベース`Seattle1`です。 (SQLNCLI を使用すると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] により最新バージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーにリダイレクトされます)。A`SELECT`返す行セットを定義するステートメントを使用します。 プロバイダー文字列が含まれています、`Server`と`Trusted_Connection`キーワード。 これらのキーワードは、によって認識され、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーです。  
  
```tsql  
SELECT a.*  
FROM OPENROWSET('SQLNCLI', 'Server=Seattle1;Trusted_Connection=yes;',  
     'SELECT GroupName, Name, DepartmentID  
      FROM AdventureWorks2012.HumanResources.Department  
      ORDER BY GroupName, Name') AS a;  
```  
  
### <a name="b-using-the-microsoft-ole-db-provider-for-jet"></a>B. Microsoft OLE DB Provider for Jet を使用する  
 次の例にアクセスする、`Customers`テーブルに、[!INCLUDE[msCoName](../../includes/msconame-md.md)]アクセス`Northwind`を通じてデータベース、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB Provider for Jet します。  
  
> [!NOTE]  
>  この例では、Access がインストールされていることを前提としています。 この例を実行するには、Northwind データベースをインストールする必要があります。  
  
```tsql  
SELECT CustomerID, CompanyName  
   FROM OPENROWSET('Microsoft.Jet.OLEDB.4.0',  
      'C:\Program Files\Microsoft Office\OFFICE11\SAMPLES\Northwind.mdb';  
      'admin';'',Customers);  
GO  
```  
  
### <a name="c-using-openrowset-and-another-table-in-an-inner-join"></a>C. OPENROWSET と INNER JOIN 内の別のテーブルを使用する  
 次の例のすべてのデータの選択、`Customers`のローカル インスタンスからテーブル[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]`Northwind`データベースとの間、`Orders`アクセスからテーブル`Northwind`同じコンピューターに格納されているデータベース。  
  
> [!NOTE]  
>  この例では、Access がインストールされていることを前提としています。 この例を実行するには、Northwind データベースをインストールする必要があります。  
  
```tsql  
USE Northwind  ;  
GO  
SELECT c.*, o.*  
FROM Northwind.dbo.Customers AS c   
   INNER JOIN OPENROWSET('Microsoft.Jet.OLEDB.4.0',   
   'C:\Program Files\Microsoft Office\OFFICE11\SAMPLES\Northwind.mdb';'admin';'', Orders)      
   AS o   
   ON c.CustomerID = o.CustomerID ;  
GO  
```  
  
### <a name="d-using-openrowset-to-bulk-insert-file-data-into-a-varbinarymax-column"></a>D. OPENROWSET を使用して、ファイル データを varbinary(max) 列に一括挿入する  
 次の例は、デモンストレーションのための小さなテーブルを作成し、という名前のファイルからファイル データを挿入`Text1.txt`にある、`C:`にルート ディレクトリ、`varbinary(max)`列です。  
  
```tsql  
USE AdventureWorks2012;  
GO  
CREATE TABLE myTable(FileName nvarchar(60),   
  FileType nvarchar(60), Document varbinary(max));  
GO  
  
INSERT INTO myTable(FileName, FileType, Document)   
   SELECT 'Text1.txt' AS FileName,   
      '.txt' AS FileType,   
      * FROM OPENROWSET(BULK N'C:\Text1.txt', SINGLE_BLOB) AS Document;  
GO  
```  
  
### <a name="e-using-the-openrowset-bulk-provider-with-a-format-file-to-retrieve-rows-from-a-text-file"></a>E. OPENROWSET BULK プロバイダーをフォーマット ファイルと共に使用して、テキスト ファイルから行を取得する  
 次の例は、フォーマット ファイルを使用して、タブ区切りのテキスト ファイルから行を取得`values.txt`次のデータを格納しています。  
  
```tsql  
1     Data Item 1  
2     Data Item 2  
3     Data Item 3  
```  
  
 フォーマット ファイル `values.fmt` では、`values.txt` の列が次のように表されています。  
  
```tsql  
9.0  
2  
1  SQLCHAR  0  10 "\t"        1  ID                SQL_Latin1_General_Cp437_BIN  
2  SQLCHAR  0  40 "\r\n"      2  Description        SQL_Latin1_General_Cp437_BIN  
```  
  
 データを取得するクエリは次のようになります。  
  
```tsql  
SELECT a.* FROM OPENROWSET( BULK 'c:\test\values.txt',   
   FORMATFILE = 'c:\test\values.fmt') AS a;  
```  
  
### <a name="f-specifying-a-format-file-and-code-page"></a>F. フォーマット ファイルとコード ページを指定します。  
 次の例では、同時にフォーマット ファイルとコード ページの両方のオプションを使用する方法を示します。  
  
```tsql  
INSERT INTO MyTable SELECT a.* FROM  
OPENROWSET (BULK N'D:\data.csv', FORMATFILE =   
    'D:\format_no_collation.txt', CODEPAGE = '65001') AS a;  
```  
### <a name="g-accessing-data-from-a-csv-file-with-a-format-file"></a>G. フォーマット ファイルで、CSV ファイルからデータにアクセスします。  
**適用対象:** [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1.   
```tsql
SELECT *
FROM OPENROWSET(BULK N'D:\XChange\test-csv.csv',
    FORMATFILE = N'D:\XChange\test-csv.fmt', 
    FIRSTROW=2, 
    FORMAT='CSV') AS cars;  
```

### <a name="h-accessing-data-from-a-csv-file-without-a-format-file"></a>H. フォーマット ファイルを使用せずに CSV ファイルからデータにアクセスします。

```tsql
SELECT * FROM OPENROWSET(
   BULK 'C:\Program Files\Microsoft SQL Server\MSSQL14.CTP1_1\MSSQL\DATA\inv-2017-01-19.csv',
   SINGLE_CLOB) AS DATA;
```

### <a name="i-accessing-data-from-a-file-stored-on-azure-blob-storage"></a>I. Azure Blob ストレージに格納されているファイルからデータにアクセスします。   
**適用対象:** [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1.   
次の例では、Azure ストレージ アカウントとデータベース スコープ資格情報の共有アクセス署名の作成でコンテナーを指している外部データ ソースを使用します。     

```tsql
SELECT * FROM OPENROWSET(
   BULK  'inv-2017-01-19.csv',
   DATA_SOURCE = 'MyAzureInvoices',
   SINGLE_CLOB) AS DataFile;
```   
完了`OPENROWSET`資格情報と外部データ ソースの構成などの例を参照してください[例の一括データにアクセスする Azure Blob ストレージに](../../relational-databases/import-export/examples-of-bulk-access-to-data-in-azure-blob-storage.md)です。
 
### <a name="additional-examples"></a>その他の例  
 使用して表示するその他の例の`INSERT...SELECT * FROM OPENROWSET(BULK...)`、次のトピックを参照してください。  
  
-   [XML ドキュメントの一括インポートと一括エクスポートの例 &#40;SQL Server&#41;](../../relational-databases/import-export/examples-of-bulk-import-and-export-of-xml-documents-sql-server.md)  
  
-   [データの一括インポート時の ID 値の保持 &#40;SQL Server&#41;](../../relational-databases/import-export/keep-identity-values-when-bulk-importing-data-sql-server.md)  
  
-   [一括インポート中の NULL の保持または既定値の使用 &#40;SQL Server&#41;](../../relational-databases/import-export/keep-nulls-or-use-default-values-during-bulk-import-sql-server.md)  
  
-   [データの一括インポートでのフォーマット ファイルの使用 &#40;SQL Server&#41;](../../relational-databases/import-export/use-a-format-file-to-bulk-import-data-sql-server.md)  
  
-   [文字形式を使用したデータのインポートまたはエクスポート &#40;SQL Server&#41;](../../relational-databases/import-export/use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [フォーマット ファイルを使用したテーブル列のスキップ &#40;SQL Server&#41;](../../relational-databases/import-export/use-a-format-file-to-skip-a-table-column-sql-server.md)  
  
-   [フォーマット ファイルを使用したデータ フィールドのスキップ &#40;SQL Server&#41;](../../relational-databases/import-export/use-a-format-file-to-skip-a-data-field-sql-server.md)  
  
-   [フォーマット ファイルを使用したテーブル列とデータ ファイル フィールドのマッピング &#40;SQL Server&#41;](../../relational-databases/import-export/use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md)  
  
## <a name="see-also"></a>参照  
 [DELETE &#40;Transact-SQL&#41;](../../t-sql/statements/delete-transact-sql.md)   
 [FROM &#40;Transact-SQL&#41;](../../t-sql/queries/from-transact-sql.md)   
 [データの一括インポートと一括エクスポート &#40;SQL Server&#41;](../../relational-databases/import-export/bulk-import-and-export-of-data-sql-server.md)   
 [INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/insert-transact-sql.md)   
 [OPENDATASOURCE &#40;Transact-SQL&#41;](../../t-sql/functions/opendatasource-transact-sql.md)   
 [OPENQUERY &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/openquery-transact-sql.md)   
 [行セット関数 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/rowset-functions-transact-sql.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [sp_addlinkedserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md)   
 [sp_serveroption &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-serveroption-transact-sql.md)   
 [UPDATE &#40;Transact-SQL&#41;](../../t-sql/queries/update-transact-sql.md)   
 [ここで &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/queries/where-transact-sql.md)  
  
  

