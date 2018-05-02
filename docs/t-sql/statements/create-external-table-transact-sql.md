---
title: CREATE EXTERNAL TABLE (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 11/27/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: t-sql|statements
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- CREATE_EXTERNAL_TABLE
- CREATE EXTERNAL TABLE
- PolyBase, T-SQL
dev_langs:
- TSQL
helpviewer_keywords:
- External
- External, table create
- PolyBase, external table
ms.assetid: 6a6fd8fe-73f5-4639-9908-2279031abdec
caps.latest.revision: 30
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: On Demand
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 352bdf39861d8874f1e7b535c2ef954e65d48339
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="create-external-table-transact-sql"></a>外部テーブル (TRANSACT-SQL) を作成します。
[!INCLUDE[tsql-appliesto-ss2016-all-md](../../includes/tsql-appliesto-ss2016-all-md.md)]

  PolyBase または Elastic Database クエリ用の外部テーブルを作成します。 シナリオによっては、構文が大幅に異なります。 PolyBase 用に作成された外部テーブルは、Elastic Database のクエリには使用できません。  同様に、Elastic Database のクエリ用に作成された外部テーブルは、PolyBase などには使用できません。 
  
> [!NOTE]  
>  PolyBase は、SQL Server 2016 以降、Azure SQL Data Warehouse、および Parallel Data Warehouse でのみサポートされています。 Elastic Database のクエリは、Azure SQL Database v12 以降でのみサポートされています。  


- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は外部テーブルを使用して、Hadoop クラスターまたは Azure Blob Storage に格納されているデータにアクセスします。PolyBase 外部テーブルは、Hadoop クラスターまたは Azure Blob Storage に格納されているデータを参照します。 [Elastic Database クエリ](https://azure.microsoft.com/documentation/articles/sql-database-elastic-query-overview/)の外部テーブルを作成するためにも使用できます。  
  
 外部テーブルを使用します。  
  
-   [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを使用して、Hadoop または Azure Blob Storage データをクエリします。  
  
-   Hadoop または Azure Blob Storage からデータをインポートして、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースに格納します。  
  
-   弾力性のあるデータベースで使用するため、外部テーブルを作成します。  
     クエリ。  
     
- Azure Data Lake Store からデータをインポートして、Azure SQL Data Warehouse に格納します。
  
 「[CREATE EXTERNAL DATA SOURCE &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-data-source-transact-sql.md)」および「[DROP EXTERNAL TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/drop-external-table-transact-sql.md)」も参照してください。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  

```  
-- Syntax for SQL Server 
  
-- Create a new external table  
CREATE EXTERNAL TABLE [ database_name . [ schema_name ] . | schema_name. ] table_name   
    ( <column_definition> [ ,...n ] )  
    WITH (   
        LOCATION = 'folder_or_filepath',  
        DATA_SOURCE = external_data_source_name,  
        FILE_FORMAT = external_file_format_name  
        [ , <reject_options> [ ,...n ] ]  
    )  
[;]  
  
<reject_options> ::=  
{  
    | REJECT_TYPE = value | percentage  
    | REJECT_VALUE = reject_value  
    | REJECT_SAMPLE_VALUE = reject_sample_value  
  
}  
  
-- Create a table for use with Elastic Database query  
CREATE EXTERNAL TABLE [ database_name . [ schema_name ] . | schema_name. ] table_name   
    ( <column_definition> [ ,...n ] )  
    WITH ( <sharded_external_table_options> )  
[;]  
  
<sharded_external_table_options> ::=  
        DATA_SOURCE = external_data_source_name,   
        SCHEMA_NAME = N'nonescaped_schema_name',  
        OBJECT_NAME = N'nonescaped_object_name',  
        [DISTRIBUTION  = SHARDED(sharding_column_name) | REPLICATED | ROUND_ROBIN]]  
    )  
[;]  
```  

```  
-- Syntax for Azure SQL Database
  
-- Create a table for use with Elastic Database query  
CREATE EXTERNAL TABLE [ database_name . [ schema_name ] . | schema_name. ] table_name   
    ( <column_definition> [ ,...n ] )  
    WITH ( <sharded_external_table_options> )  
[;]  
  
<sharded_external_table_options> ::=  
        DATA_SOURCE = external_data_source_name,   
        SCHEMA_NAME = N'nonescaped_schema_name',  
        OBJECT_NAME = N'nonescaped_object_name',  
        [DISTRIBUTION  = SHARDED(sharding_column_name) | REPLICATED | ROUND_ROBIN]]  
    )  
[;]  
```  


```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
-- Create a new external table in SQL Server PDW  
CREATE EXTERNAL TABLE [ database_name . [ schema_name ] . | schema_name. ] table_name   
    ( <column_definition> [ ,...n ] )  
    WITH (   
        LOCATION = 'hdfs_folder_or_filepath',  
        DATA_SOURCE = external_data_source_name,  
        FILE_FORMAT = external_file_format_name  
        [ , <reject_options> [ ,...n ] ]  
    )  
[;]  
  
<reject_options> ::=  
{  
    | REJECT_TYPE = value | percentage  
    | REJECT_VALUE = reject_value  
    | REJECT_SAMPLE_VALUE = reject_sample_value  
  
}  
```  
  
## <a name="arguments"></a>引数  
 *database_name* . [schema_name] です。 |schema_name です。 ] *table_name*  
 1 つを 3 つの一部の名前を作成するテーブル。 外部テーブルのテーブルのメタデータのみのファイルまたはフォルダーの Hadoop または Azure blob ストレージ内で参照に関する基本的な統計情報と値は SQL に格納されます。 実際のデータは移動されず、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に格納されません。  
  
 \<column_definition> [ ,...*n* ] CREATE EXTERNAL TABLE では、1 つまたは複数の列の定義を使用できます。 CREATE EXTERNAL TABLE と CREATE TABLE の両方の列を定義する同じ構文を使用します。 例外が次のようには、外部テーブルで、既定の制約を使用することはできません。 列の定義とそのデータ型の詳細については、「[CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)」と「[CREATE TABLE (Transact-SQL)](http://msdn.microsoft.com/library/d53c529a-1d5f-417f-9a77-64ccc6eddca1)」を使用してください。  
  
 列の定義には、外部ファイル内のデータを一致データ型と列の数を含む必要があります。 不一致がある場合、実際のデータを照会するときに、ファイルの行が拒否されます。  
  
 外部データ ソース内のファイルを参照する外部のテーブルでは、列と型の定義は、外部ファイルの正確なスキーマにマップする必要があります。 Hadoop/ハイブに格納されているデータを参照するデータの種類を定義する場合は、SQL、および Hive のデータ型の間では、次のマッピングを使用し、そこから選択するときに、SQL のデータ型に型をキャストします。 型には、特にそれ以外の場合に記されていない、ハイブのすべてのバージョンが含まれます。

> [!NOTE]  
>  SQL Server では、いずれの変換でも Hive の _infinity_のデータ値をサポートしていません。 PolyBase はデータ型変換エラーで失敗します。


|SQL データ型|.NET データ型|データ型を hive します。|Hadoop と Java のデータ型|コメント|  
|-------------------|--------------------|--------------------|----------------------------|--------------|  
|TINYINT|Byte|TINYINT|ByteWritable|符号なし数値の場合のみです。|  
|SMALLINT|Int16|SMALLINT|ShortWritable||  
|ssNoversion|Int32|ssNoversion|IntWritable||  
|BIGINT|Int64|BIGINT|LongWritable||  
|bit|ブール値|boolean|BooleanWritable||  
|FLOAT|Double|double|DoubleWritable||  
|REAL|単一|FLOAT|FloatWritable||  
|money|Decimal|double|DoubleWritable||  
|SMALLMONEY|Decimal|double|DoubleWritable||  
|NCHAR|String<br /><br /> Char[]|string|text||  
|NVARCHAR|String<br /><br /> Char[]|string|Text||  
|char|String<br /><br /> Char[]|string|Text||  
|varchar|String<br /><br /> Char[]|string|Text||  
|binary|Byte[]|binary|BytesWritable|Hive 0.8 およびそれ以降に適用されます。|  
|varbinary|Byte[]|binary|BytesWritable|Hive 0.8 およびそれ以降に適用されます。|  
|日付|DateTime|TIMESTAMP|TimestampWritable||  
|smalldatetime|DateTime|TIMESTAMP|TimestampWritable||  
|datetime2|DateTime|TIMESTAMP|TimestampWritable||  
|DATETIME|DateTime|TIMESTAMP|TimestampWritable||  
|time|TimeSpan|TIMESTAMP|TimestampWritable||  
|Decimal|Decimal|Decimal|BigDecimalWritable|Hive0.11 以降が適用されます。|  
  
 LOCATION =  '*folder_or_filepath*'  
 Hadoop または Azure blob ストレージでは、フォルダーまたはファイル パスと、実際のデータのファイル名を指定します。 ルート フォルダーから、場所を開始します。ルート フォルダーは、外部データ ソースで指定されたデータの場所です。  


SQL Server では、CREATE EXTERNAL TABLE ステートメントによって、まだ存在しない場合にパスとフォルダーが作成されます。 その後、INSERT INTO を使用して、ローカルの SQL Server テーブルからのデータを外部データ ソースをエクスポートすることができます。 詳細については、「[PolyBase クエリ](/sql/relational-databases/polybase/polybase-queries)」を参照してください。 

SQL Data Warehouse と Analytics Platform System では、[CREATE EXTERNAL TABLE AS SELECT](create-external-table-as-select-transact-sql.md) ステートメントによって、存在しない場合にパスとフォルダーが作成されます。 これらの 2 つの製品では、CREATE EXTERNAL TABLE によってパスとフォルダーは作成されません。

  
 フォルダーであることをする場所を指定する場合、外部テーブルから選択する PolyBase クエリはフォルダーとそのすべてのサブフォルダーからファイルを取得します。 Hadoop と同じように PolyBase で非表示のフォルダーは返されません。 それも返さないことをファイル名は、下線 (_) またはピリオド (.) で始まるファイルです。  
  
 この例で場合場所 ='webdata/'、PolyBase クエリ mydata.txt および mydata2.txt から行が返されます。  非表示のフォルダーのサブフォルダーであるために、mydata3.txt を返すことはできません。 隠しファイルであるために、_hidden.txt を返すことはできません。  
  
 ![外部テーブルの再帰型データ](../../t-sql/statements/media/aps-polybase-folder-traversal.png "外部テーブルの再帰型データ")  
  
 既定値を変更して、読み取りをルート フォルダーからのみに限定するには、core-site.xml 構成ファイル内で属性 \<polybase.recursive.traversal> を 'false' に設定します。 このファイルは `<SqlBinRoot>\Polybase\Hadoop\Conf with SqlBinRoot the bin root of SQl Server` の配下に配置されます。 たとえば、 `C:\\Program Files\\Microsoft SQL Server\\MSSQL13.XD14\\MSSQL\\Binn`のようにします。  
  
 DATA_SOURCE = *external_data_source_name*  
 外部のデータの場所を含む外部データ ソースの名前を指定します。 この場所は、Hadoop または Azure blob ストレージです。 外部データ ソースを作成するには、[CREATE EXTERNAL DATA SOURCE &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-data-source-transact-sql.md) を使用します。  
  
 FILE_FORMAT = *external_file_format_name*  
 外部データに対するファイルの種類と比較のメソッドを格納する外部のファイル形式のオブジェクトの名前を指定します。 外部ファイル形式を作成するには、[CREATE EXTERNAL FILE FORMAT &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-file-format-transact-sql.md) を使用します。  
  
 オプションを拒否します。  
 PolyBase が外部データ ソースから取得した*ダーティ* レコードを処理する方法を決定する、reject パラメーターを指定できます。 データ レコードは、'ダーティ' 場合と見なされますが実際のデータ型または列の数も、外部テーブルの列の定義が一致しません。  
  
 指定または拒否する値を変更しない、ときに、PolyBase は、既定値を使用します。 CREATE EXTERNAL TABLE ステートメントを使用して、外部テーブルを作成するときに、拒否するパラメーターについては、この情報は追加のメタデータとして格納されます。   ときに、将来の SELECT ステートメントまたは選択 INTO SELECT ステートメントは、外部テーブルからデータを選択して、PolyBase オプションを使用して、拒否数や、実際のクエリが失敗する前に拒否されることもの行の割合を判断します。 のインスタンスにアクセスするたびに SQL Server ログインを指定する必要はありません。 クエリは結果を返します (部分) まで、拒否のしきい値を超過するとします。また、適切なエラー メッセージと、失敗します。  
  
 REJECT_TYPE = **value** | percentage  
 REJECT_VALUE オプションは、リテラル値またはパーセントとして指定されているかどうか明確にします。  
  
 value  
 REJECT_VALUE は、リテラル値、パーセンテージではありません。 拒否された行が *reject_value* を超えると、PolyBase クエリは失敗します。  
  
 たとえば場合、REJECT_VALUE = 5 と REJECT_TYPE = 値、PolyBase の 5 行が拒否された後、SELECT クエリは失敗します。  
  
 割合  
 REJECT_VALUE では、リテラル値ではなく、パーセンテージです。 失敗した行の *percentage* が *reject_value* を超えると、PolyBase クエリは失敗します。 障害が発生した行の割合は、間隔で計算されます。  
  
 REJECT_VALUE = *reject_value*  
 または、クエリが失敗する前に拒否されることもの行のパーセンテージの値を指定します。  
  
 REJECT_TYPE = value の場合、*reject_value* は 0 から 2,147, 483,647 の範囲の整数にする必要があります。  
  
 REJECT_TYPE = percentage の場合、*reject_value* は 0 から 100 の範囲の浮動小数にする必要があります。  
  
 REJECT_SAMPLE_VALUE = *reject_sample_value*  
 REJECT_TYPE を指定する場合は、この属性は必須 = 割合。 前に、PolyBase が拒否された行の割合を再計算を取得しようとする行の数を決定します。  
  
 *reject_sample_value* パラメーターは、0 から 2,147,483,647 の範囲の整数にする必要があります。  
  
 たとえば場合、REJECT_SAMPLE_VALUE = 1000、PolyBase では、1000年行を外部のデータ ファイルからインポートしようとしましたが、後に障害が発生した行の比率が計算されます。 失敗した行のパーセンテージが *reject_value* 未満の場合、PolyBase は別の 1000 行の取得を試みます。 各追加の 1000年行をインポートする試みた後に障害が発生した行の割合を再計算を続行します。  
  
> [!NOTE]  
>  PolyBase では間隔を置いて失敗した行のパーセンテージを計算するため、実際の失敗した行のパーセンテージは、*reject_value* を超える場合があります。  
  
 例:  
  
 この例では、拒否の 3 つのオプションが相互にやり取りする方法を示します。 たとえば場合、REJECT_TYPE 割合、REJECT_VALUE を = = 30、および REJECT_SAMPLE_VALUE、次のシナリオが発生する可能性が 100 を =。  
  
-   PolyBase が、最初の 100 行を取得しようとしています。25 75、および失敗および成功します。  
  
-   障害が発生した行の割合は、これは、30% の拒否の値よりも小さい 25%、として計算されます。 そのため、PolyBase は引き続き、外部データ ソースからデータを取得します。  
  
-   PolyBase が、次の 100 個の行では; をロードしようとしています。この時刻の 25 が成功して、75 が失敗します。  
  
-   失敗した行の割合が 50% として再計算されます。 障害が発生した行の割合が 30% の拒否の値を超えました。  
  
-   PolyBase クエリは、最初の 200 の行を取得しようとした後、拒否、50% の行で失敗します。 PolyBase クエリでは、拒否のしきい値を超えましたが検出する前に一致する行が返されたことに注意してください。  
  
 外部テーブルを分割のオプション  
 [Elastic Database クエリ](https://azure.microsoft.com/documentation/articles/sql-database-elastic-query-overview/)の外部データ ソース (SQL Server 以外のデータ ソース) と配布方法を指定します。  
  
 DATA_SOURCE  
 Hadoop ファイル システム、Azure Blob Storage、または [Shard Map Manager](https://azure.microsoft.com/documentation/articles/sql-database-elastic-scale-shard-map-management/) に格納されているデータなどの外部データ ソースです。  
  
 SCHEMA_NAME  
 SCHEMA_NAME 句では、外部テーブルの定義をリモート データベースに対する別のスキーマ内のテーブルにマップする機能を提供します。 ローカルおよびリモートの両方のデータベースに存在するスキーマ間で明確に区別するには、これを使用します。  
  
 OBJECT_NAME  
 OBJECT_NAME 句では、外部テーブルの定義をリモート データベースに対する別の名前を持つテーブルにマップする機能を提供します。 ローカルおよびリモートの両方のデータベースに存在するオブジェクト名の間で明確に区別するには、これを使用します。  
  
 DISTRIBUTION  
 省略可。 これは型 SHARD_MAP_MANAGER のデータベースでのみ必須です。 これは、テーブルが、シャードされたテーブルまたはレプリケートされたテーブルとして扱うかどうかを制御します。 **SHARDED** (*列名*) テーブルでは、異なるテーブルからのデータは重複しません。 **REPLICATED** は、テーブルですべてのシャードに同じデータを持つことを指定します。 **ROUND_ROBIN** は、データを分散するためにアプリケーション固有のメソッドが使用されていることを示します。  
  
## <a name="permissions"></a>アクセス許可  
 これらのユーザー アクセス許可が必要です。  
  
-   **CREATE TABLE**  
  
-   **ALTER ANY SCHEMA**  
  
-   **ALTER ANY EXTERNAL DATA SOURCE**  
  
-   **ALTER ANY EXTERNAL FILE FORMAT**  

-   **CONTROL DATABASE**
  
 外部データ ソースを作成したログインに注意してください Hadoop または Azure blob ストレージにある、外部データ ソースを読み書きするアクセス許可が必要です。  


 > [!IMPORTANT]  

>  ALTER ANY EXTERNAL DATA SOURCE 権限は、あらゆる外部データ ソース オブジェクトを作成し、変更する能力をプリンシパルに与えます。そのため、データベース上のすべてのデータベース スコープ資格情報にアクセスする能力も与えます。 この権限は特権として考える必要があります。したがって、システム内の信頼できるプリンシパルにのみ与える必要があります。

## <a name="error-handling"></a>エラー処理  
 CREATE EXTERNAL TABLE ステートメントを実行するには、中に、PolyBase は外部データ ソースに接続しようとします。 接続に失敗した場合は、ステートメントは失敗し、外部テーブルは作成されません。 コマンドの PolyBase 最終的に、クエリが失敗する前に、接続を再試行するために失敗を 1 分以上がかかることができます。  
  
## <a name="general-remarks"></a>全般的な解説  
 つまりから外部テーブルの選択、アドホック クエリのシナリオでは、PolyBase は、一時テーブルに外部データ ソースから取得された行を格納します。 クエリが完了したら、PolyBase は削除し、一時テーブルを削除します。 SQL テーブルには、永続的なデータは格納されません。  
  
 これに対し、シナリオでは、インポート、つまりにから外部テーブルの選択、PolyBase では、SQL テーブル内の永続的なデータとして、外部データ ソースから取得された行に格納します。 Polybase が外部のデータを取得するときに、クエリの実行中に、新しいテーブルが作成されます。  
  
 PolyBase は、クエリのパフォーマンスを向上させるために Hadoop をクエリの計算の一部をプッシュできます。 これには、述語のプッシュ ダウンは呼び出されます。 これを有効にするには、[CREATE EXTERNAL DATA SOURCE &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-data-source-transact-sql.md) で、Hadoop のリソース マネージャーの場所のオプションを指定します。  
  
 同じまたは別の外部データ ソースを参照している多数の外部テーブルを作成できます。  
  
## <a name="limitations-and-restrictions"></a>制限事項と制約事項  
 CTP2 では、エクスポート機能はサポートされていません、つまり完全に SQL データを外部データ ソースに格納します。 この機能は、CTP3 で使用されます。  
  
 アプライアンス オフ、外部テーブルのデータが存在するため、PolyBase の管理されていないと変更またはの外部プロセスによっていつでも削除です。 このため、外部のテーブルに対して uery 結果は決定的である保証はありません。 同じクエリでは、外部のテーブルに対して実行するたびに異なる結果を返すことができます。 同様に、外部のデータが削除されるか、再配置する場合に、クエリが失敗することができます。  
  
 さまざまな外部データ ソースを参照して各いる複数の外部テーブルを作成することができます。 ただし、さまざまな Hadoop のデータ ソースに対してクエリを同時に実行すると、各 Hadoop ソース必要があります同じ 'hadoop 接続' サーバーの構成設定を使用します。 たとえば、ことはできません同時にクエリを実行する Cloudera Hadoop クラスターと Hortonworks の Hadoop クラスターに対してこれらさまざまな構成設定を使用するためです。 構成設定とサポートされる組み合わせについては、「[PolyBase 接続構成 &#40;Transact-SQL&#41;](../../database-engine/configure-windows/polybase-connectivity-configuration-transact-sql.md)」を参照してください。  
  
 テーブルの外部では、これらのデータ定義言語 (DDL) ステートメントのみが使用できます。  
  
-   CREATE TABLE、および DROP TABLE  
  
-   統計の作成と DROP STATISTICS  
注: Azure SQL Database では、外部テーブルの CREATE と DROP STATISTICS はサポートされていません。 
  
-   ビューの作成、および DROP VIEW  
  
 構成要素と操作がサポートされていません。  
  
-   外部テーブルの列に対して既定の制約  
  
-   Delete、insert、および update のデータ操作言語 (DML) 操作  
  
 クエリの制限事項:  
  
 PolyBase は 32 の同時実行 PolyBase クエリを実行している場合、最大で 1 つのフォルダーの 33 k ファイルを使用できます。 この最大数には、各 HDFS フォルダー内のファイルとサブフォルダーの両方が含まれます。 同時実行の程度が 32 未満である場合は、ユーザーは、複数の 33 k ファイルが含まれている HDFS のフォルダーに対して PolyBase クエリを実行できます。 短い外部ファイルのパスを維持して、1 つの HDFS フォルダー 30 個を超える k ファイルを使用することをお勧めします。 ファイルが多すぎますが参照されるときに、Java 仮想マシン (JVM) のメモリ不足の例外が発生する可能性があります。  

テーブルの幅の制限: SQL Server 2016 の PolyBase には、テーブル定義により、有効な 1 つの行の最大サイズに基づく 32 KB の行の幅の制限があります。 列のスキーマの合計が 32 KB を超えると、PolyBase はデータをクエリできなくなります。 

SQL Data Warehouse では、この制限が 1 MB に増えます。


## <a name="locking"></a>ロック  
 SCHEMARESOLUTION オブジェクトのロックを共有します。  
  
## <a name="security"></a>Security  
 外部テーブルのデータ ファイルは、Hadoop または Azure blob ストレージに格納されます。 これらのデータ ファイルが作成され、独自のプロセスによって管理されます。 ユーザーの責任において、外部のデータのセキュリティを管理することをお勧めします。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-create-an-external-table-with-data-in-text-delimited-format"></a>A. データをテキストで区切られた形式で外部テーブルを作成します。  
 この例では、テキスト区切りのファイルで書式設定されたデータのある外部テーブルを作成するために必要なすべての手順を示します。 これは、外部データ ソース *mydatasource*c と外部ファイルの形式 *myfileformat* を定義します。 これらのデータベース レベルのオブジェクトは、CREATE EXTERNAL TABLE ステートメントで参照します。 詳細については、「[CREATE EXTERNAL DATA SOURCE &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-data-source-transact-sql.md)」および「[CREATE EXTERNAL FILE FORMAT &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-file-format-transact-sql.md)」を参照してください。  
  
```  
  
CREATE EXTERNAL DATA SOURCE mydatasource  
WITH (  
    TYPE = HADOOP,  
    LOCATION = 'hdfs://xxx.xxx.xxx.xxx:8020'  
)  
  
CREATE EXTERNAL FILE FORMAT myfileformat  
WITH (  
    FORMAT_TYPE = DELIMITEDTEXT,   
    FORMAT_OPTIONS (FIELD_TERMINATOR ='|')  
);  
  
CREATE EXTERNAL TABLE ClickStream (   
    url varchar(50),  
    event_date date,  
    user_IP varchar(50)  
)  
WITH (  
        LOCATION='/webdata/employee.tbl',  
        DATA_SOURCE = mydatasource,  
        FILE_FORMAT = myfileformat  
    )  
;  
  
```  
  
### <a name="b-create-an-external-table-with-data-in-rcfile-format"></a>B. RCFile 形式でのデータには、外部テーブルを作成します。  
 この例では、外部テーブルを持つ RCFiles として書式設定されたデータの作成に必要なすべての手順を示します。 これは、外部データ ソース *mydatasource_rc* と外部ファイルの形式 *myfileformat_rc* を定義します。 これらのデータベース レベルのオブジェクトは、CREATE EXTERNAL TABLE ステートメントで参照します。 詳細については、「[CREATE EXTERNAL DATA SOURCE &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-data-source-transact-sql.md)」および「[CREATE EXTERNAL FILE FORMAT &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-file-format-transact-sql.md)」を参照してください。  
  
```  
  
CREATE EXTERNAL DATA SOURCE mydatasource_rc  
WITH (  
    TYPE = HADOOP,  
    LOCATION = 'hdfs://xxx.xxx.xxx.xxx:8020'  
)  
  
CREATE EXTERNAL FILE FORMAT myfileformat_rc  
WITH (  
    FORMAT_TYPE = RCFILE,  
    SERDE_METHOD = 'org.apache.hadoop.hive.serde2.columnar.LazyBinaryColumnarSerDe'  
)  
;  
  
CREATE EXTERNAL TABLE ClickStream_rc (   
    url varchar(50),  
    event_date date,  
    user_ip varchar(50)  
)  
WITH (  
        LOCATION='/webdata/employee_rc.tbl',  
        DATA_SOURCE = mydatasource_rc,  
        FILE_FORMAT = myfileformat_rc  
    )  
;  
  
```  
  
### <a name="c-create-an-external-table-with-data-in-orc-format"></a>C. ORC 形式でのデータには、外部テーブルを作成します。  
 この例を ORC ファイルとして書式設定されたデータを持つ外部テーブルを作成するのに必要なすべての手順を示します。 これは、外部データのソース mydatasource_orc と外部ファイルの形式 myfileformat_orc を定義します。 これらのデータベース レベルのオブジェクトは、CREATE EXTERNAL TABLE ステートメントで参照します。 詳細については、「[CREATE EXTERNAL DATA SOURCE &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-data-source-transact-sql.md)」および「[CREATE EXTERNAL FILE FORMAT &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-file-format-transact-sql.md)」を参照してください。  
  
```  
  
CREATE EXTERNAL DATA SOURCE mydatasource_orc  
WITH (  
    TYPE = HADOOP,  
    LOCATION = 'hdfs://xxx.xxx.xxx.xxx:8020'  
)  
  
CREATE EXTERNAL FILE FORMAT myfileformat_orc  
WITH (  
    FORMAT = ORC,  
    COMPRESSION = 'org.apache.hadoop.io.compress.SnappyCodec'  
)  
;  
  
CREATE EXTERNAL TABLE ClickStream_orc (   
    url varchar(50),  
    event_date date,  
    user_ip varchar(50)  
)  
WITH (  
        LOCATION='/webdata/',  
        DATA_SOURCE = mydatasource_orc,  
        FILE_FORMAT = myfileformat_orc  
    )  
;  
  
```  
  
### <a name="d-querying-hadoop-data"></a>D. Hadoop のデータを照会します。  
 クリック ストリームは、Hadoop クラスター上の employee.tbl 区切りテキスト ファイルに接続する外部テーブルです。 次のクエリでは、標準のテーブルに対するクエリと同じように検索します。 ただし、このクエリでは、Hadoop からデータを取得し、、restuls を計算します。  
  
```  
SELECT TOP 10 (url) FROM ClickStream WHERE user_ip = 'xxx.xxx.xxx.xxx'  
;  
```  
  
### <a name="e-join-hadoop-data-with-sql-data"></a>E. SQL データと Hadoop のデータを結合します。  
 このクエリは、2 つの SQL テーブルに、標準の結合と同じように検索します。 違いは、PolyBase が Hadoop からクリック ストリーム データを取得し、UrlDescription テーブルに結合することです。 1 つのテーブルには、外部テーブルで、もう一方は標準の SQL テーブルです。  
  
```  
SELECT url.description  
FROM ClickStream cs  
JOIN UrlDescription url ON cs.url = url.name  
WHERE cs.url = 'msdn.microsoft.com'  
;  
```  
  
### <a name="f-import-data-from-hadoop-into-a-sql-table"></a>F. Hadoop から SQL テーブルにデータをインポートします。  
 この例では、標準の SQL テーブル *user*と外部テーブル *ClickStream* との結合の結果を永続的に格納する新しい SQL テーブル ms_user を作成します。  
  
```  
SELECT DISTINCT user.FirstName, user.LastName  
INTO ms_user  
FROM user INNER JOIN (  
    SELECT * FROM ClickStream WHERE cs.url = 'www.microsoft.com'  
    ) AS ms_user  
ON user.user_ip = ms.user_ip  
;  
  
```  
  
### <a name="g-create-an-external-table-for-a-sharded-data-source"></a>G. 分割データ ソースの外部のテーブルを作成します。  
 この例では、リモートの DMV SCHEMA_NAME、OBJECT_NAME 句を使用して外部テーブルに再マップします。  
  
```  
CREATE EXTERNAL TABLE [dbo].[all_dm_exec_requests]([session_id] smallint NOT NULL,  
  [request_id] int NOT NULL,  
  [start_time] datetime NOT NULL,   
  [status] nvarchar(30) NOT NULL,  
  [command] nvarchar(32) NOT NULL,  
  [sql_handle] varbinary(64),  
  [statement_start_offset] int,  
  [statement_end_offset] int,  
  [cpu_time] int NOT NULL)  
WITH  
(  
  DATA_SOURCE = MyExtSrc,  
  SCHEMA_NAME = 'sys',  
  OBJECT_NAME = 'dm_exec_requests',  
  DISTRIBUTION=ROUND_ROBIN  
);   
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] および [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="h-importing-data-from-adls-into-azure-includessdwincludesssdw-mdmd"></a>H. ADLS から Azure [!INCLUDE[ssDW](../../includes/ssdw-md.md)] にデータをインポートする  
 
  
```  

-- These values come from your Azure Active Directory Application used to authenticate to ADLS
CREATE DATABASE SCOPED CREDENTIAL ADLUser 
WITH IDENTITY = '<clientID>@\<OAuth2.0TokenEndPoint>',
SECRET = '<KEY>' ;


CREATE EXTERNAL DATA SOURCE AzureDataLakeStore
WITH (TYPE = HADOOP,
      LOCATION = 'adl://pbasetr.azuredatalakestore.net'
)



CREATE EXTERNAL FILE FORMAT TextFileFormat 
WITH ( FORMATTYPE = DELIMITEDTEXT 
     , FORMATOPTIONS ( FIELDTERMINATOR = '|' 
                     , STRINGDELIMITER = '' 
                     , DATEFORMAT = 'yyyy-MM-dd HH:mm:ss.fff' 
                     , USETYPE_DEFAULT = FALSE 
                     ) 
    )


CREATE EXTERNAL TABLE [dbo].[DimProductexternal] 
( [ProductKey] [int] NOT NULL, 
  [ProductLabel] nvarchar NULL, 
  [ProductName] nvarchar NULL ) 
WITH ( LOCATION='/DimProduct/' , 
       DATA_SOURCE = AzureDataLakeStore , 
       FILE_FORMAT = TextFileFormat , 
       REJECT_TYPE = VALUE ,
       REJECT_VALUE = 0 ) ;


CREATE TABLE [dbo].[DimProduct] 
WITH (DISTRIBUTION = HASH([ProductKey] ) ) 
AS SELECT * FROM 
[dbo].[DimProduct_external] ; 
     
```  
  
### <a name="i-join-external-tables"></a>I. 外部テーブルを結合する  
  
```  
SELECT url.description  
FROM ClickStream cs  
JOIN UrlDescription url ON cs.url = url.name  
WHERE cs.url = 'msdn.microsoft.com'  
;  
```  
  
### <a name="j-join-hdfs-data-with-pdw-data"></a>J. HDFS データと PDW データを結合する  
  
```  
SELECT cs.user_ip FROM ClickStream cs  
JOIN User u ON cs.user_ip = u.user_ip  
WHERE cs.url = 'www.microsoft.com'  
;  
  
```  
  
### <a name="k-import-row-data-from-hdfs-into-a-distributed-pdw-table"></a>K. HDFS から分散 PDW テーブルに行のデータをインポートする  
  
```  
CREATE TABLE ClickStream_PDW  
WITH ( DISTRIBUTION = HASH (url) )  
AS SELECT url, event_date, user_ip FROM ClickStream  
;  
```  
  
### <a name="l-import-row-data-from-hdfs-into-a-replicated-pdw-table"></a>L. HDFS からレプリケートされた PDW テーブルに行のデータをインポートする  
  
```  
CREATE TABLE ClickStream_PDW  
WITH ( DISTRIBUTION = REPLICATE )  
AS SELECT url, event_date, user_ip   
FROM ClickStream  
;  
```  
  
## <a name="see-also"></a>参照  
 [共通のメタデータのクエリ例 (SQL Server PDW)](http://msdn.microsoft.com/en-us/733fc99b-b9f6-4a29-b085-a1bd4f09f2ed)   
 [CREATE EXTERNAL DATA SOURCE &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-data-source-transact-sql.md)   
 [CREATE EXTERNAL FILE FORMAT &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-file-format-transact-sql.md)   
 [CREATE EXTERNAL TABLE AS SELECT &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-table-as-select-transact-sql.md)   
 [CREATE TABLE AS SELECT &#40;Azure SQL Data Warehouse&#41;](../../t-sql/statements/create-table-as-select-azure-sql-data-warehouse.md)  
  
  



