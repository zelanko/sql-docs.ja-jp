---
title: CREATE EXTERNAL TABLE (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
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
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 06fc940fad53ee37f4e97a6883a99666722a05bf
ms.sourcegitcommit: c3b190f8f87a4c80bc9126bb244896197a6dc453
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/26/2019
ms.locfileid: "56852917"
---
# <a name="create-external-table-transact-sql"></a>CREATE EXTERNAL TABLE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-all-md](../../includes/tsql-appliesto-ss2016-all-md.md)]

PolyBase または Elastic Database クエリ用の外部テーブルを作成します。 シナリオによっては、構文が大幅に異なります。 PolyBase 用に作成された外部テーブルは、Elastic Database のクエリには使用できません。  同様に、Elastic Database のクエリ用に作成された外部テーブルは、PolyBase などには使用できません。 
  
> [!NOTE]  
>  PolyBase は、SQL Server 2016 以降、Azure SQL Data Warehouse、および Parallel Data Warehouse でのみサポートされています。 Elastic Database のクエリは、Azure SQL Database v12 以降でのみサポートされています。  


- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では外部テーブルを使用して、Hadoop クラスターまたは Azure Blob Storage に格納されているデータにアクセスします。PolyBase 外部テーブルは、Hadoop クラスターまたは Azure Blob Storage に格納されているデータを参照します。 [Elastic Database クエリ](https://azure.microsoft.com/documentation/articles/sql-database-elastic-query-overview/)の外部テーブルを作成するためにも使用できます。  
  
次のために外部テーブルを使用します。  
  
-   [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを使用して、Hadoop または Azure Blob Storage データをクエリします。  
  
-   Hadoop または Azure Blob Storage からデータをインポートして、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースに格納します。  
  
-   弾力性のあるデータベース クエリで使用するための外部テーブルを作成します  
     。  
     
- Azure Data Lake Store からデータをインポートして、Azure SQL Data Warehouse に格納します。
 
「[CREATE EXTERNAL DATA SOURCE &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-data-source-transact-sql.md)」および「[DROP EXTERNAL TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/drop-external-table-transact-sql.md)」も参照してください。  
  
![記事のリンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "記事のリンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  

```sql
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

```sql
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


```sql
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
    | REJECT_TYPE = value | percentage,  
    | REJECT_VALUE = reject_value,  
    | REJECT_SAMPLE_VALUE = reject_sample_value,
    | REJECTED_ROW_LOCATION = '\REJECT_Directory'
  
}  
```  
  
## <a name="arguments"></a>引数  
*database_name* . [ schema_name ] . | schema_name. ] *table_name*  
作成するテーブルの 1 つから 3 つの部分で構成される名前。 外部テーブルの場合、SQL では、Hadoop または Azure Blob Storage 内で参照されているファイルまたはフォルダーに関する基本的な統計情報と共に、テーブルのメタデータのみが格納されます。 実際のデータは移動されず、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に格納されません。  
  
\<column_definition> [ ,...*n* ] CREATE EXTERNAL TABLE では、1 つまたは複数の列の定義を使用できます。 CREATE EXTERNAL TABLE と CREATE TABLE の両方で、列を定義するために同じ構文を使用します。 ただし、外部テーブルに対して DEFAULT CONSTRAINT を使用することはできません。 列の定義とそのデータ型の詳細については、「[CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)」と「[CREATE TABLE (Transact-SQL)](https://msdn.microsoft.com/library/d53c529a-1d5f-417f-9a77-64ccc6eddca1)」を使用してください。  
  
データ型と列の数を含む列の定義は、外部ファイルのデータと一致している必要があります。 不一致がある場合、実際のデータに対してクエリを実行するときに、ファイルの行が拒否されます。  
  
LOCATION =  '*folder_or_filepath*'  
Hadoop または Azure Blob Storage にある実際のデータのフォルダーまたはファイル パスとファイル名を指定します。 ルート フォルダーから、場所を開始します。 ルート フォルダーは、外部データ ソースで指定されたデータの場所です。  


SQL Server では、CREATE EXTERNAL TABLE ステートメントによって、まだ存在しない場合にパスとフォルダーが作成されます。 その後、INSERT INTO を使用して、ローカルの SQL Server テーブルからのデータを外部データ ソースをエクスポートすることができます。 詳細については、[PolyBase クエリ](/sql/relational-databases/polybase/polybase-queries)に関するページを参照してください。 

SQL Data Warehouse と Analytics Platform System では、[CREATE EXTERNAL TABLE AS SELECT](create-external-table-as-select-transact-sql.md) ステートメントによって、存在しない場合にパスとフォルダーが作成されます。 これらの 2 つの製品では、CREATE EXTERNAL TABLE によってパスとフォルダーは作成されません。

  
LOCATION をフォルダーとして指定した場合、外部テーブルから選択する PolyBase クエリでは、フォルダーとそのすべてのサブフォルダーからファイルが取得されます。 Hadoop と同じように PolyBase で非表示のフォルダーは返されません。 ファイル名が下線 (_) またはピリオド (.) で始まるファイルも返されません。  
  
この例では、LOCATION='/webdata/' である場合、PolyBase クエリでは mydata.txt と mydata2.txt から行が返されます。  mydata3.txt は非表示のフォルダーのサブフォルダーであるため、返されません。 また、_hidden.txt は非表示のファイルであるため返されません。  
  
![外部テーブルの再帰型データ](../../t-sql/statements/media/aps-polybase-folder-traversal.png "外部テーブルの再帰型データ")  
  
既定値を変更して、読み取りをルート フォルダーからのみに限定するには、core-site.xml 構成ファイル内で属性 \<polybase.recursive.traversal> を 'false' に設定します。 このファイルは `<SqlBinRoot>\PolyBase\Hadoop\Conf with SqlBinRoot the bin root of SQl Server` の配下に配置されます。 たとえば、`C:\\Program Files\\Microsoft SQL Server\\MSSQL13.XD14\\MSSQL\\Binn` のようにします。  
  
DATA_SOURCE = *external_data_source_name*  
外部データの場所を含む外部データ ソースの名前を指定します。 この場所は、Hadoop または Azure BLOB ストレージです。 外部データ ソースを作成するには、[CREATE EXTERNAL DATA SOURCE &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-data-source-transact-sql.md) を使用します。  
  
FILE_FORMAT = *external_file_format_name*  
外部データのファイルの種類と圧縮方法を格納する外部ファイル形式のオブジェクトの名前を指定します。 外部ファイル形式を作成するには、[CREATE EXTERNAL FILE FORMAT &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-file-format-transact-sql.md) を使用します。  
  
拒否オプション  
PolyBase が外部データ ソースから取得した*ダーティ* レコードを処理する方法を決定する、reject パラメーターを指定できます。 データ レコードの実際のデータの種類または列の数が、外部テーブルの列の定義と一致しない場合、そのデータ レコードは "ダーティ" と見なされます。  
  
reject 値を指定または変更しない場合、PolyBase では既定値が使用されます。 reject パラメーターに関するこの情報は、CREATE EXTERNAL TABLE ステートメントを使用して外部テーブルを作成するときに、追加メタデータとして格納されます。   以降の SELECT ステートメントまたは SELECT INTO SELECT ステートメントで外部テーブルからデータを選択するとき、拒否オプションを使用して、実際のクエリが失敗するまでに拒否できる行の数または割合が PolyBase によって決定されます。 拒否のしきい値を超えるまで、クエリの (部分的な) 結果が返されます。 その後、適切なエラー メッセージと共に失敗します。  
  
REJECT_TYPE = **value** | percentage  
REJECT_VALUE オプションがリテラル値として指定されているか、割合として指定されているかを明確にします。  
  
value  
REJECT_VALUE は、割合ではなくリテラル値です。 拒否された行が *reject_value* を超えると、PolyBase クエリは失敗します。  
  
たとえば、REJECT_VALUE = 5 で REJECT_TYPE = value の場合、PolyBase の SELECT クエリは、5 行を拒否した後に失敗します。  
  
percentage  
REJECT_VALUE は、リテラル値ではなく割合です。 失敗した行の *percentage* が *reject_value* を超えると、PolyBase クエリは失敗します。 失敗した行の割合は、間隔をおいて計算されます。  
  
REJECT_VALUE = *reject_value*  
クエリが失敗する前に拒否できる行を値または割合で指定します。  
  
REJECT_TYPE = value の場合、*reject_value* は 0 から 2,147, 483,647 の範囲の整数にする必要があります。  
  
REJECT_TYPE = percentage の場合、*reject_value* は 0 から 100 の範囲の浮動小数にする必要があります。  
  
REJECT_SAMPLE_VALUE = *reject_sample_value*  
REJECT_TYPE = percentage を指定する場合、この属性は必須です。 それにより、拒否された行の割合が PolyBase によって再計算されるまでに取得が試行される行の数が決定します。  
  
*reject_sample_value* パラメーターは、0 から 2,147,483,647 の範囲の整数にする必要があります。  
  
たとえば、REJECT_SAMPLE_VALUE = 1000 の場合、PolyBase によって外部データ ファイルから 1000 行のインポートが試みられた後、失敗した行の割合が再計算されます。 失敗した行のパーセンテージが *reject_value* 未満の場合、PolyBase は別の 1000 行の取得を試みます。 1000 行ずつ追加でインポートを試みた後、失敗した行の割合の再計算を続けます。  
  
> [!NOTE]  
>  PolyBase では間隔を置いて失敗した行のパーセンテージを計算するため、実際の失敗した行のパーセンテージは、*reject_value* を超える場合があります。  
  

例:  
  
この例は、REJECT の 3 つのオプションが相互にどのように作用するかを示しています。 たとえば、REJECT_TYPE = percentage で REJECT_VALUE = 30、かつ REJECT_SAMPLE_VALUE = 100 の場合、次のシナリオが発生する可能性があります。  
  
-   PolyBase で最初の 100 行の取得が試みられ、25 行が失敗し、75 行が成功しました。  
  
-   失敗した行の割合は 25% と計算されます。これは reject 値である 30% を下回っています。 その結果、PolyBase は引き続き、外部データ ソースからデータを取得します。  
  
-   PolyBase は次の 100 行の読み込みを試み、今回は 25 行が成功し、75 行が失敗しました。  
  
-   失敗した行の割合が 50% として再計算されます。 失敗した行の割合が、30% という reject 値を超えました。  
  
-   PolyBase クエリは、最初の 200 行を取得しようとした後、拒否された行 50% で失敗します。 拒否のしきい値を超えたことが PolyBase クエリによって検出される前に、一致した行が返されていることに注意してください。  
  
REJECTED_ROW_LOCATION = *<ディレクトリの場所>*
  
外部データ ソース内のディレクトリを指定します。拒否された行と該当エラー ファイルをそこに書き込みます。
指定したパスが存在しない場合、PolyBase では、そのパスが自動的に作成されます。 "_rejectedrows" という名前で子ディレクトリが作成されます。"_" 文字があることで、場所パラメーターで明示的に指定されない限り、他のデータ処理ではこのディレクトリがエスケープされます。 このディレクトリ内には、YearMonthDay -HourMinuteSecond (例:  20180330-173205) のロード サブミッション時間に基づいて作成されたフォルダーがあります。 このフォルダーで、2 種類のファイル、理由ファイルとデータ ファイルが書き込まれます。 

理由ファイルとデータ ファイルのいずれにも、CTAS ステートメントと関連付けられている queryID が含まれます。 データと理由が別々のファイル内にあるため、対応するファイルはサフィックスが一致しています。 
  
シャード化された外部テーブルのオプション  
[Elastic Database クエリ](https://azure.microsoft.com/documentation/articles/sql-database-elastic-query-overview/)の外部データ ソース (SQL Server 以外のデータ ソース) と配布方法を指定します。  
  
DATA_SOURCE  
Hadoop ファイル システム、Azure Blob Storage、または [Shard Map Manager](https://azure.microsoft.com/documentation/articles/sql-database-elastic-scale-shard-map-management/) に格納されているデータなどの外部データ ソースです。  
  
SCHEMA_NAME  
SCHEMA_NAME 句では、外部テーブルの定義をリモート データベース上のスキーマの異なるテーブルにマップする機能が提供されます。 ローカルおよびリモートの両方のデータベースに存在するスキーマ間であいまいさを排除するには、この句を使用します。  
  
OBJECT_NAME  
OBJECT_NAME 句では、外部テーブルの定義をリモート データベース上の別の名前を持つテーブルにマップする機能が提供されます。 ローカルおよびリモートの両方のデータベースに存在するオブジェクト名の間であいまいさを排除するには、この句を使用します。  
  
DISTRIBUTION  
省略可。 これは SHARD_MAP_MANAGER 型のデータベースの場合にのみ必須です。 この引数では、テーブルをシャード化されたテーブルとして扱うか、レプリケートされたテーブルとして扱うかを制御します。 **SHARDED** (*列名*) テーブルでは、異なるテーブルからのデータは重複しません。 **REPLICATED** は、テーブルですべてのシャードに同じデータを持つことを指定します。 **ROUND_ROBIN** は、データを分散するためにアプリケーション固有のメソッドが使用されていることを示します。  
  
## <a name="permissions"></a>アクセス許可  
これらのユーザー アクセス許可が必要です。  
  
-   **CREATE TABLE**  
  
-   **ALTER ANY SCHEMA**  
  
-   **ALTER ANY EXTERNAL DATA SOURCE**  
  
-   **ALTER ANY EXTERNAL FILE FORMAT**  

-   **CONTROL DATABASE**
  
外部データ ソースを作成するログインには、Hadoop または Azure Blob Storage 内にある外部データ ソースに対する読み取りおよび書き込みの権限が必要であることに注意してください。  


> [!IMPORTANT]
> 
>  ALTER ANY EXTERNAL DATA SOURCE 権限は、あらゆる外部データ ソース オブジェクトを作成し、変更する能力をプリンシパルに与えます。そのため、データベース上のすべてのデータベース スコープ資格情報にアクセスする能力も与えます。 この権限は特権として考える必要があります。したがって、システム内の信頼できるプリンシパルにのみ与える必要があります。

## <a name="error-handling"></a>エラー処理  
CREATE EXTERNAL TABLE ステートメントの実行中に、PolyBase から外部データ ソースへの接続が試みられます。 接続が失敗した場合、ステートメントは失敗し、外部テーブルは作成されません。 クエリが最終的に失敗となる前に、PolyBase によって接続が再試行されるため、コマンドが失敗するまで 1 分以上かかる可能性があります。  
  
## <a name="general-remarks"></a>全般的な解説  
SELECT FROM EXTERNAL TABLE などのアドホック クエリのシナリオの場合、PolyBase では外部データ ソースから取得された行が一時テーブルに格納されます。 クエリ完了後、PolyBase によって一時テーブルが削除されます。 SQL テーブルには、永続的なデータは格納されません。  
  
これに対し、SELECT INTO FROM EXTERNAL TABLE などのインポートのシナリオでは、外部データ ソースから取得された行が、PolyBase によって永続的なデータとして SQL テーブルに格納されます。 PolyBase が外部のデータを取得するときに、クエリの実行中に、新しいテーブルが作成されます。  
  
PolyBase では、クエリのパフォーマンスを向上させるためにクエリ計算の一部を Hadoop にプッシュできます。 このアクションは述語プッシュダウンと呼ばれます。 それを有効にするには、[CREATE EXTERNAL DATA SOURCE &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-data-source-transact-sql.md) で、Hadoop のリソース マネージャーの場所のオプションを指定します。  
  
同じまたは別の外部データ ソースを参照している多数の外部テーブルを作成できます。  
  
## <a name="limitations-and-restrictions"></a>制限事項と制約事項  
CTP2 では、SQL データを外部データ ソースに永続的に格納するなどのエクスポート機能はサポートされていません。 この機能は CTP3 で利用可能になります。  
  
外部テーブルのデータはアプライアンスの外部にあるため、PolyBase の管理下にはなく、外部プロセスによっていつでも変更または削除できます。 その結果、外部のテーブルに対するクエリの結果は確定的であることが保証されません。 同じクエリを外部のテーブルに対して実行するたびに、異なる結果が返される可能性があります。 同様に、外部データが移動または削除された場合、クエリが失敗する可能性があります。  
  
それぞれが異なる外部データ ソースを参照する複数の外部テーブルを作成できます。 異なる複数の Hadoop データ ソースに対して同時にクエリを実行する場合は、各 Hadoop ソースに同じ 'Hadoop 接続' サーバー構成の設定が使用されている必要があります。 たとえば、ことはできません同時にクエリを実行する Cloudera Hadoop クラスターと Hortonworks の Hadoop クラスターに対してこれらさまざまな構成設定を使用するためです。 構成設定とサポートされる組み合わせについては、「[PolyBase 接続構成 &#40;Transact-SQL&#41;](../../database-engine/configure-windows/polybase-connectivity-configuration-transact-sql.md)」を参照してください。  
  
外部テーブルに対しては、これらのデータ定義言語 (DDL) ステートメントのみを使用できます。  
  
-   CREATE TABLE および DROP TABLE  
  
-   CREATE STATISTICS および DROP STATISTICS  
注:Azure SQL Database では、外部テーブルに対する CREATE STATISTICS と DROP STATISTICS はサポートされていません。 
  
-   CREATE VIEW および DROP VIEW  
  
サポートされていない構成要素と操作:  
  
-   外部テーブルの列に対する DEFAULT 制約  
  
-   データ操作言語 (DML) の削除、挿入、更新の操作  
  
クエリの制限事項:  
  
PolyBase では、32 個の同時 PolyBase クエリを実行しているときに、フォルダーあたり最大 33,000 ファイルを使用できます。 この最大数には、各 HDFS フォルダー内のファイルとサブフォルダーの両方が含まれます。 コンカレンシーの度合いが 32 未満である場合、ユーザーは 33,000 より多いファイルが含まれている HDFS のフォルダーに対して PolyBase クエリを実行できます。 外部ファイルのパスを短く維持し、使用するファイルの数を HDFS フォルダーあたり 30,000 以下にすることをお勧めします。 参照しているファイルの数が多すぎる場合は、Java 仮想マシン (JVM) のメモリ不足例外が発生する可能性があります。  

テーブルの幅の制限:

SQL Server 2016 の PolyBase には、テーブル定義による有効な 1 つの行の最大幅に基づいた、行の幅 32 KB という制限があります。 列スキーマの合計が 32 KB を超えている場合、PolyBase によるデータのクエリは実行できません。 

SQL Data Warehouse では、この制限が 1 MB に引き上げられています。


## <a name="locking"></a>ロック  
SCHEMARESOLUTION オブジェクトに対する共有ロック。  
  
## <a name="security"></a>Security  
外部テーブルのデータ ファイルは Hadoop または Azure Blob Storage に格納されます。 これらのデータ ファイルはご自身のプロセスによって作成され、管理されます。 外部データのセキュリティを管理することは、ユーザー自身の責任になります。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-create-an-external-table-with-data-in-text-delimited-format"></a>A. テキスト区切り形式のデータを含む外部テーブルを作成します。  
この例では、テキスト区切りのファイルで書式設定されたデータを含む外部テーブルを作成するために必要なすべての手順を示します。 これは、外部データ ソース *mydatasource*c と外部ファイルの形式 *myfileformat* を定義します。 その後、これらのデータベース レベル オブジェクトは、CREATE EXTERNAL TABLE ステートメントで参照されます。 詳細については、「[CREATE EXTERNAL DATA SOURCE &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-data-source-transact-sql.md)」および「[CREATE EXTERNAL FILE FORMAT &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-file-format-transact-sql.md)」を参照してください。  
  
```sql
  
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
  
### <a name="b-create-an-external-table-with-data-in-rcfile-format"></a>B. RCFile 形式のデータを含む外部テーブルを作成します。  
この例では、RCFile として書式設定されたデータを含む外部テーブルを作成するために必要なすべての手順を示します。 これは、外部データ ソース *mydatasource_rc* と外部ファイルの形式 *myfileformat_rc* を定義します。 その後、これらのデータベース レベル オブジェクトは、CREATE EXTERNAL TABLE ステートメントで参照されます。 詳細については、「[CREATE EXTERNAL DATA SOURCE &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-data-source-transact-sql.md)」および「[CREATE EXTERNAL FILE FORMAT &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-file-format-transact-sql.md)」を参照してください。  
  
```sql
  
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
  
### <a name="c-create-an-external-table-with-data-in-orc-format"></a>C. ORC 形式のデータを含む外部テーブルを作成します。  
この例では、ORC ファイルとして書式設定されたデータを含む外部テーブルを作成するために必要なすべての手順を示します。 それにより、外部データ ソース mydatasource_orc と外部ファイル myfileformat_orc を定義します。 その後、これらのデータベース レベル オブジェクトは、CREATE EXTERNAL TABLE ステートメントで参照されます。 詳細については、「[CREATE EXTERNAL DATA SOURCE &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-data-source-transact-sql.md)」および「[CREATE EXTERNAL FILE FORMAT &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-file-format-transact-sql.md)」を参照してください。  
  
```sql
  
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
  
### <a name="d-querying-hadoop-data"></a>D. Hadoop データのクエリ  
クリックストリームは、Hadoop クラスター上の区切りテキスト ファイルである employee.tbl に接続する外部テーブルです。 次のクエリは、標準のテーブルに対するクエリとまったく同じように見えます。 ただし、このクエリでは Hadoop からデータを取得し、restuls を計算します。  
  
```sql
SELECT TOP 10 (url) FROM ClickStream WHERE user_ip = 'xxx.xxx.xxx.xxx'  
;  
```  
  
### <a name="e-join-hadoop-data-with-sql-data"></a>E. SQL データと Hadoop データの結合  
このクエリは、2 つの SQL テーブルに対する標準の JOIN とまったく同じように見えます。 違いは、PolyBase によって Hadoop からクリックストリーム データが取得され、その後 UrlDescription テーブルに結合されることです。 一方のテーブルは外部テーブルで、もう一方は標準の SQL テーブルです。  
  
```sql
SELECT url.description  
FROM ClickStream cs  
JOIN UrlDescription url ON cs.url = url.name  
WHERE cs.url = 'msdn.microsoft.com'  
;  
```  
  
### <a name="f-import-data-from-hadoop-into-a-sql-table"></a>F. Hadoop から SQL テーブルへのデータのインポート  
この例では、標準の SQL テーブル *user*と外部テーブル *ClickStream* との結合の結果を永続的に格納する新しい SQL テーブル ms_user を作成します。  
  
```sql
SELECT DISTINCT user.FirstName, user.LastName  
INTO ms_user  
FROM user INNER JOIN (  
    SELECT * FROM ClickStream WHERE cs.url = 'www.microsoft.com'  
    ) AS ms_user  
ON user.user_ip = ms.user_ip  
;  
  
```  
  
### <a name="g-create-an-external-table-for-a-sharded-data-source"></a>G. シャード化されたデータ ソース用の外部テーブルの作成  
この例では、SCHEMA_NAME 句と OBJECT_NAME 句を使用してリモートの DMV を外部テーブルに再マッピングします。  
  
```sql
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
 
  
```sql

-- These values come from your Azure Active Directory Application used to authenticate to ADLS
CREATE DATABASE SCOPED CREDENTIAL ADLUser 
WITH IDENTITY = '<clientID>@\<OAuth2.0TokenEndPoint>',
SECRET = '<KEY>' ;


CREATE EXTERNAL DATA SOURCE AzureDataLakeStore
WITH (TYPE = HADOOP,
      LOCATION = 'adl://pbasetr.azuredatalakestore.net'
)



CREATE EXTERNAL FILE FORMAT TextFileFormat 
WITH
(
    FORMAT_TYPE = DELIMITEDTEXT 
    , FORMAT_OPTIONS ( FIELDTERMINATOR = '|' 
                     , STRINGDELIMITER = '' 
                     , DATEFORMAT = 'yyyy-MM-dd HH:mm:ss.fff' 
                     , USETYPE_DEFAULT = FALSE 
                     ) 
)


CREATE EXTERNAL TABLE [dbo].[DimProductexternal] 
( [ProductKey] [int] NOT NULL, 
  [ProductLabel] nvarchar NULL, 
  [ProductName] nvarchar NULL ) 
WITH
(
    LOCATION='/DimProduct/' , 
    DATA_SOURCE = AzureDataLakeStore , 
    FILE_FORMAT = TextFileFormat , 
    REJECT_TYPE = VALUE ,
    REJECT_VALUE = 0
) ;


CREATE TABLE [dbo].[DimProduct] 
WITH (DISTRIBUTION = HASH([ProductKey] ) ) 
AS SELECT * FROM 
[dbo].[DimProduct_external] ; 
     
```  
  
### <a name="i-join-external-tables"></a>I. 外部テーブルを結合する  
  
```sql
SELECT url.description  
FROM ClickStream cs  
JOIN UrlDescription url ON cs.url = url.name  
WHERE cs.url = 'msdn.microsoft.com'  
;  
```  
  
### <a name="j-join-hdfs-data-with-pdw-data"></a>J. HDFS データと PDW データを結合する  
  
```sql
SELECT cs.user_ip FROM ClickStream cs  
JOIN User u ON cs.user_ip = u.user_ip  
WHERE cs.url = 'www.microsoft.com'  
;  
  
```  
  
### <a name="k-import-row-data-from-hdfs-into-a-distributed-pdw-table"></a>K. HDFS から分散 PDW テーブルに行のデータをインポートする  
  
```sql
CREATE TABLE ClickStream_PDW  
WITH ( DISTRIBUTION = HASH (url) )  
AS SELECT url, event_date, user_ip FROM ClickStream  
;  
```  
  
### <a name="l-import-row-data-from-hdfs-into-a-replicated-pdw-table"></a>L. HDFS からレプリケートされた PDW テーブルに行のデータをインポートする  
  
```sql
CREATE TABLE ClickStream_PDW  
WITH ( DISTRIBUTION = REPLICATE )  
AS SELECT url, event_date, user_ip   
FROM ClickStream  
;  
```  
  
## <a name="see-also"></a>参照  
[共通のメタデータのクエリ例 (SQL Server PDW)](https://msdn.microsoft.com/733fc99b-b9f6-4a29-b085-a1bd4f09f2ed)   
[CREATE EXTERNAL DATA SOURCE &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-data-source-transact-sql.md)   
[CREATE EXTERNAL FILE FORMAT &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-file-format-transact-sql.md)   
[CREATE EXTERNAL TABLE AS SELECT &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-table-as-select-transact-sql.md)   
[CREATE TABLE AS SELECT &#40;Azure SQL Data Warehouse&#41;](../../t-sql/statements/create-table-as-select-azure-sql-data-warehouse.md)  
  
  



