---
title: "JSON ドキュメントの SQL Server へのインポート | Microsoft Docs"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-json
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0e908ec0-7173-4cd2-8f48-2700757b53a5
caps.latest.revision: 5
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.translationtype: HT
ms.sourcegitcommit: 9045ebe77cf2f60fecad22672f3f055d8c5fdff2
ms.openlocfilehash: 95489b4e72f1321f7e1139f06040eb81a5956b15
ms.contentlocale: ja-jp
ms.lasthandoff: 07/31/2017

---
# <a name="import-json-documents-into-sql-server"></a>JSON ドキュメントの SQL Server へのインポート
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

このトピックでは、SQL Server に JSON ファイルをインポートする方法について説明します。 現在、多数の JSON ドキュメントがファイルに保存されています。 たとえば、アプリケーションは JSON ファイルに情報を記録し、センサーは JSON ファイルに保存される情報を生成します。 ファイルに保存されている JSON データ読み取り、そのデータを SQL Server に読み込んで分析できることが重要です。

## <a name="import-a-json-document-into-a-single-column"></a>JSON ドキュメントを 1 つの列にインポートする
**OPENROWSET(BULK)** は、SQL Server が読み取りアクセス権を持っている場所であれば、ローカル ドライブまたはネットワーク上の任意のファイルからデータを読み取ることができるテーブル値関数です。 ファイルの内容を含む 1 列のテーブルを返します。 OPENROWSET(BULK) 関数では、区切り記号など、さまざまなオプションを使用できます。 簡単な場合では、単にファイルの内容全体をテキスト値として読み込むことができます。 (この 1 つの大きな値は、Single Character Large Object (SINGLE_CLOB) と呼ばれます)。 

JSON ファイルを読み取り、それを 1 つの値としてユーザーに返す **OPENROWSET(BULK)** 関数の例を次に示します。

```sql
SELECT BulkColumn
 FROM OPENROWSET (BULK 'C:\JSON\Books\book.json', SINGLE_CLOB) as j
```

OPENJSON(BULK) はファイルの内容を読み取り、`BulkColumn` で返します。

次の例のように、ファイルの内容は、ローカル変数またはテーブルに読み込むことができます。

```sql
-- Load file contents into a variable
SELECT @json = BulkColumn
 FROM OPENROWSET (BULK 'C:\JSON\Books\book.json', SINGLE_CLOB) as j

-- Load file contents into a table 
SELECT BulkColumn
 INTO #temp 
 FROM OPENROWSET (BULK 'C:\JSON\Books\book.json', SINGLE_CLOB) as j
```

JSON ファイルの内容を読み込んだ後、JSON テキストをテーブルに保存できます。

## <a name="import-multiple-json-documents"></a>複数の JSON ドキュメントをインポートする
同じ方法を使用して、ファイル システムから複数の JSON ファイルを一度に 1 つずつローカル変数に読み込むことができます。 ファイルは `book<index>.json` という名前です。
  
```sql
DECLARE @i INT = 1
DECLARE @json AS NVARCHAR(MAX)

WHILE(@i < 10)
BEGIN
    SET @file = 'C:\JSON\Books\book' + cast(@i AS VARCHAR(5)) + '.json';
    SELECT @json = BulkColumn FROM OPENROWSET (BULK (@file), SINGLE_CLOB) AS j
    SELECT * FROM OPENJSON(@json) AS json
    -- Optionally, save the JSON text in a table.
    SET @i = @i + 1 ;
END
```

## <a name="import-json-documents-from-azure-file-storage"></a>Azure File Storage から JSON ドキュメントをインポートする
また、前に説明した OPENROWSET(BULK) を使って、SQL Server がアクセスできる他のファイルの場所から JSON ファイルを読み取ることができます。 たとえば、Azure File Storage は SMB プロトコルをサポートしています。 そのため、次の手順でローカルの仮想ドライブを Azure File Storage 共有にマップできます。
1.  Azure ポータルまたは Azure PowerShell を使用して、ファイル ストレージ アカウント (`mystorage` など)、ファイル共有 (`sharejson` など)、および Azure File Storage のフォルダーを作成します。
2.  いくつかの JSON ファイルをファイル ストレージ共有にアップロードします。
3.  コンピューターの Windows ファイアウォールで、ポート 445 を許可する送信ファイアウォール規則を作成します。 インターネット サービス プロバイダー (ISP) がこのポートをブロックしている可能性があるので注意してください。 次の手順で DNS エラー (エラー 53) が発生する場合は、ポート 445 を開いていないか、ISP がブロックしています。
4. Azure File Storage 共有をローカル ドライブ (`T:` など) としてマウントします。

    コマンドの構文は次のとおりです。

    ```dos
    net use [drive letter] \\[storage name].file.core.windows.net\[share name] /u:[storage account name] [storage account access key]
    ```

    ローカル ドライブ文字 `T:` を Azure File Storage 共有に割り当てる例を次に示します。

    ```dos
    net use t: \\mystorage.file.core.windows.net\sharejson /u:myaccount hb5qy6eXLqIdBj0LvGMHdrTiygkjhHDvWjUZg3Gu7bubKLg==
    ```

    ストレージ アカウント キーと、プライマリまたはセカンダリ ストレージ アカウント アクセス キーは、Azure ポータルの [設定] の [キー] セクションで確認できます。

5.  マップ済みドライブを使って Azure File Storage 共有から JSON ファイルにアクセスできるようになりました。次にその例を示します。

    ```sql
    SELECT book.* FROM
     OPENROWSET(BULK N't:\books\books.json', SINGLE_CLOB) AS json
     CROSS APPLY OPENJSON(BulkColumn)
     WITH( id nvarchar(100), name nvarchar(100), price float,
        pages_i int, author nvarchar(100)) AS book
    ```

Azure File Storage の詳細については、「[File Storage](https://azure.microsoft.com/en-us/services/storage/files/)」を参照してください。

## <a name="import-json-documents-from-azure-blob-storage"></a>Azure Blob Storage から JSON ドキュメントをインポートする

T-SQL BULK INSERT コマンドまたは OPENROWSET 関数を使用して、Azure Blob Storage のファイルを Azure SQL Database に直接読み込むことができます。

まず外部データ ソースを作成します。次に例を示します。

```sql
CREATE EXTERNAL DATA SOURCE MyAzureBlobStorage
 WITH ( TYPE = BLOB_STORAGE,
        LOCATION = 'https://myazureblobstorage.blob.core.windows.net',
        CREDENTIAL= MyAzureBlobStorageCredential);
```

次に、DATA_SOURCE オプションを指定して BULK INSERT コマンドを実行します。

```sql
BULK INSERT Product
FROM 'data/product.dat'
WITH ( DATA_SOURCE = 'MyAzureBlobStorage');
```

OPENROWSET の使用の詳細と例については、「[Loading files from Azure Blob Storage into Azure SQL Database](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2017/02/23/loading-files-from-azure-blob-storage-into-azure-sql-database/)」(Azure Blob Storage のファイルを Azure SQL Database に読み込む) をご覧ください。

## <a name="parse-json-documents-into-rows-and-columns"></a>JSON ドキュメントを行と列に解析する
JSON ファイルを 1 つの値として読み取るのではなく、解析して、ファイル内の書籍とそのプロパティを行と列で返すこともできます。 次の例では、書籍の一覧を格納している[こちらのサイト](https://github.com/tamingtext/book/blob/master/apache-solr/example/exampledocs/books.json)の JSON ファイルを使います。

### <a name="example-1"></a>例 1
最も簡単な例では、単にファイルから一覧全体を読み込むことができます。 

```sql
SELECT value
 FROM OPENROWSET (BULK 'C:\JSON\Books\books.json', SINGLE_CLOB) as j
 CROSS APPLY OPENJSON(BulkColumn)
```

### <a name="example-2"></a>例 2
OPENROWSET は 1 つのテキスト値をファイルから読み取り、BulkColumn として返し、OPENJSON 関数に渡します。 OPENJSON は BulkColumn 配列内の JSON オブジェクトの配列を反復処理し、各行で JSON 形式の 1 冊の書籍を返します。

```json
{"id":"978-0641723445″, "cat":["book","hardcover"], "name":"The Lightning Thief", … 
{"id":"978-1423103349″, "cat":["book","paperback"], "name":"The Sea of Monsters", … 
{"id":"978-1857995879″, "cat":["book","paperback"], "name":"Sophie’s World : The Greek … 
{"id":"978-1933988177″, "cat":["book","paperback"], "name":"Lucene in Action, Second … 
```

### <a name="example-3"></a>例 3
OPENJSON 関数は JSON の内容を解析し、テーブルまたは結果セットに変換することができます。 次の例は内容を読み込み、読み込まれた JSON を解析し、5 つのフィールドを列として返します。

```sql
SELECT book.*
 FROM OPENROWSET (BULK 'C:\JSON\Books\books.json', SINGLE_CLOB) as j
 CROSS APPLY OPENJSON(BulkColumn)
 WITH( id nvarchar(100), name nvarchar(100), price float,
 pages_i int, author nvarchar(100)) AS book
```

この例では、OPENROWSET(BULK) はファイルの内容を読み取り、出力用に定義されたスキーマでその内容を OPENJSON 関数に渡します。 OPENJSON は、列名を使用して、JSON オブジェクト内のプロパティを対応付けます。 たとえば、`price` プロパティは `price` 列として返され、float データ型に変換されます。 結果は次のようになります。

|Id|名前|price|pages_i|Author
|---|---|---|---|---|
978-0641723445|The Lightning Thief|12.5|384|Rick Riordan| 
978-1423103349|The Sea of Monsters|6.49|304|Rick Riordan| 
978-1857995879|Sophie’s World : The Greek Philosophers|3.07|64|Jostein Gaarder| 
978-1933988177|Lucene in Action, Second Edition|30.5|475|Michael McCandless|
||||||

このテーブルをユーザーに返したり、データを別のテーブルに読み込んだりすることができます。

## <a name="learn-more-about-the-built-in-json-support-in-sql-server"></a>SQL Server に組み込まれている JSON サポートの詳細情報  
多くの具体的なソリューション、ユース ケース、推奨事項については、Microsoft のプログラム マネージャー Jovan Popovic による SQL Server および Azure SQL Database に[組み込まれている JSON のサポートに関するブログ投稿](http://blogs.msdn.com/b/sqlserverstorageengine/archive/tags/json/)をご覧ください。
  
## <a name="see-also"></a>参照
[OPENJSON を使用して JSON データを行と列に変換する](../../relational-databases/json/convert-json-data-to-rows-and-columns-with-openjson-sql-server.md)


