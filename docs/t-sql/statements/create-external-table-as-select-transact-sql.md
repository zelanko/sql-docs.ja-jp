---
title: "外部テーブルとして選択 (TRANSACT-SQL) を作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/10/2017
ms.prod: 
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: 
ms.service: sql-data-warehouse
ms.component: t-sql|statements
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CREATE EXTERNAL TABLE AS SELECT
- CREATE_EXTERNAL_TABLE_AS_SELECT
- CREATE EXTERNAL TABLE AS SELECT_TSQL
helpviewer_keywords:
- External, table
- PolyBase, external table
- External, table create as select
- PolyBase, create table as select
ms.assetid: 32dfe254-6df7-4437-bfd6-ca7d37557b0a
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: f2ca379cf30fe2e7d359a294a18804f0b5e6faeb
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="create-external-table-as-select-transact-sql"></a>外部テーブルとして選択 (TRANSACT-SQL) を作成します。
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  外部テーブルを作成し、エクスポートすると、並列での結果、 [!INCLUDE[tsql](../../includes/tsql-md.md)] Hadoop または Azure Storage の Blob に SELECT ステートメント。  
  
 作成する外部テーブルとして選択 (CETAS) ステートメントを使用します。  
  
-   データベース テーブルを Hadoop または Azure blob ストレージにエクスポートします。  
  
-   Hadoop または Azure blob ストレージからデータをインポートし、データベースに保存します。  
  
-   Hadoop または Azure blob ストレージからデータをクエリ、データベースのリレーショナル テーブルと結合し、結果を Hadoop または Azure blob ストレージに書き戻すします。  
  
-   Hadoop または Azure blob ストレージからデータをクエリ、データベースの高速処理の機能を使用して変換ジョブや Hadoop または Azure blob ストレージに書き込みます。  
  
 詳細については、「 [PolyBase 入門](../../relational-databases/polybase/get-started-with-polybase.md)」を参照してください。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [TRANSACT-SQL 構文表記規則 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
CREATE EXTERNAL TABLE [ [database_name  . [ schema_name ] . ] | schema_name . ] table_name   
    WITH (   
        LOCATION = 'hdfs_folder',  
        DATA_SOURCE = external_data_source_name,  
        FILE_FORMAT = external_file_format_name  
        [ , <reject_options> [ ,...n ] ]  
    )  
    AS <select_statement>  
[;]  
  
<reject_options> ::=  
{  
    | REJECT_TYPE = value | percentage  
    | REJECT_VALUE = reject_value  
    | REJECT_SAMPLE_VALUE = reject_sample_value  
}  
  
<select_statement> ::=  
    [ WITH <common_table_expression> [ ,...n ] ]  
    SELECT <select_criteria>  
```  
  
## <a name="arguments"></a>引数  
 [ [ *database_name* . [ *schema_name* ] . ] | *schema_name* . ] *table_name*  
 1 つを 3 つの部分の名前でデータベースを作成するテーブル。 外部テーブルのリレーショナル データベースのテーブルのメタデータのみが格納されます。  
  
 LOCATION =  '*hdfs_folder*'  
 外部データ ソースに関する SELECT ステートメントの結果の書き込み先を指定します。 場所は、フォルダー名であり、Hadoop クラスターまたは Azure Storage の Blob のルート フォルダーに対応するパスを含めることができます必要に応じて。  PolyBase が既に存在しない場合、パスとフォルダーが作成されます。  
  
 外部ファイルに書き込まれます*hdfs_folder*と名前付き*QueryID_date_time_ID.format*ここで、 *ID*増分識別子と*形式*エクスポートされたデータ形式です。 たとえば、QID776_20160130_182739_0.orc です。  
  
 DATA_SOURCE = *external_data_source_name*  
 外部のデータが格納されているまたはを格納する場所を含む外部データ ソース オブジェクトの名前を指定します。 場所は、Hadoop クラスターまたは Azure Storage の Blob のいずれか。 外部データ ソースを作成するには、使用[外部データ ソースの作成 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-external-data-source-transact-sql.md)  
  
 FILE_FORMAT = *external_file_format_name*  
 外部データ ファイルの形式を含む外部ファイル形式オブジェクトの名前を指定します。 外部ファイル形式を作成するには使用[CREATE EXTERNAL FILE FORMAT &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-external-file-format-transact-sql.md)  
  
 オプションを拒否します。  
 拒否するオプションは、この CREATE EXTERNAL TABLE AS SELECT ステートメントの実行時に適用されません。 代わりに、それらは、ここで指定したデータベースが、外部テーブルからデータをインポートする場合、後で使用できるようにします。 後で、CREATE TABLE AS SELECT ステートメントを外部テーブルからデータを選択すると、データベース オプションを使用して、拒否数またはインポートを停止する前にインポートに失敗した行の割合を決定します。  
  
 REJECT_VALUE = *reject_value*  
 またはデータベースのインポートを停止する前にインポートに失敗した行のパーセンテージの値を指定します。  
  
 REJECT_TYPE =**値**| 割合  
 REJECT_VALUE オプションは、リテラル値またはパーセントとして指定されているかどうか明確にします。  
  
 value  
 REJECT_VALUE は、リテラル値、パーセンテージではありません。  失敗した行の数を超えた場合に、外部データ ファイルから行をインポートするデータベースは停止*reject_value*です。  
  
 たとえば場合、REJECT_VALUE = 5 と REJECT_TYPE = 値、5 行がインポートに失敗した後に行をインポートするデータベースは停止します。  
  
 割合  
 REJECT_VALUE では、リテラル値ではなく、パーセンテージです。 データベースの外部からの行のインポートが停止データ ファイルの場合、*割合*失敗した行を超えています*reject_value*です。 障害が発生した行の割合は、間隔で計算されます。  
  
 REJECT_SAMPLE_VALUE = *reject_sample_value*  
 場合に必須 REJECT_TYPE = 割合、これが、データベースが障害が発生した行の割合を再計算する前にインポートしようとする行の数を指定します。  
  
 たとえば場合、REJECT_SAMPLE_VALUE = 1000、データベース外部のデータ ファイルから 1000 年行をインポートしようとしました後に失敗した行の比率が計算されます。 失敗した行の比率がある場合より小さい*reject_value*、データベースはもう 1 つの 1000 行をロードしようとしています。 データベースは、各追加の 1000 行をインポートする試みた後に障害が発生した行の割合を再計算を続行します。  
  
> [!NOTE]  
>  失敗した行の実際の割合を超える場合、データベースは、間隔で障害が発生した行の比率を計算、ため*reject_value*です。  
  
 例:  
  
 この例では、拒否の 3 つのオプションが相互にやり取りする方法を示します。 たとえば場合、REJECT_TYPE 割合、REJECT_VALUE を = = 30、および REJECT_SAMPLE_VALUE、次のシナリオが発生する可能性が 100 を =。  
  
-   データベースが、最初の 100 行を読み込むしようとしています。25 75、および失敗および成功します。  
  
-   障害が発生した行の割合は、これは、30% の拒否の値よりも小さい 25%、として計算されます。 そのため、負荷を停止する必要はありません。  
  
-   データベースが、次の 100 行を読み込みしようとしています。この時刻の 25 が成功して、75 が失敗します。  
  
-   失敗した行の割合が 50% として再計算されます。 障害が発生した行の割合が 30% の拒否の値を超えました。  
  
-   読み込みに失敗失敗 50% の行を含む 200 の行をロードしようとした後は、指定された 30% 制限よりも大きいです。  
  
 WITH *common_table_expression*  
 共通テーブル式 (CTE) と呼ばれる一時的な名前付き結果セットを指定します。 詳細については、次を参照してください。[で common_table_expression と #40 です。TRANSACT-SQL と #41 です](../../t-sql/queries/with-common-table-expression-transact-sql.md)。  
  
 選択\<select_criteria > によって、SELECT ステートメントの結果を新しいテーブルを作成します。 *select_criteria*新しいテーブルにコピーするデータを決定する SELECT ステートメントの本文です。 SELECT ステートメントの概要については、次を参照してください[SELECT &#40;。TRANSACT-SQL と #41 です。](../../t-sql/queries/select-transact-sql.md).  
  
## <a name="permissions"></a>権限  
 このコマンドを実行する、**データベース ユーザー**すべてこれらの権限またはメンバーシップ必要があります。  
  
-   **ALTER SCHEMA**のメンバーシップまたは新しいテーブルを格納するローカルのスキーマに対する権限、 **db_ddladmin**固定データベース ロール。  
  
-   **CREATE TABLE**権限またはメンバーシップ、 **db_ddladmin**固定データベース ロール。  
  
-   **選択**で参照されているすべてのオブジェクトに対する権限、 *select_criteria*です。  
  
 ログインには、すべてのこれらのアクセス許可が必要です。  
  
-   **ADMINISTER BULK OPERATIONS**権限  
  
-   **ALTER ANY EXTERNAL DATA SOURCE**権限  
  
-   **任意の外部ファイル形式の ALTER**権限  
  
-   ログインで読み取りおよび書き込みを外部のフォルダーに、Hadoop クラスターまたは Azure Storage の Blob への書き込み権限が必要です。  
 
 > [!IMPORTANT]  
 >  任意の外部データ ソースの ALTER 権限は、任意のプリンシパルを作成し、任意の外部データ ソース オブジェクトを変更する権限を付与し、そのため、データベース上のすべてのデータベース スコープ資格情報にアクセスする権限付与もします。 このアクセス許可する必要がありますと見なされる高度な権限し、そのため、システムで信頼されたプリンシパルにのみ付与する必要があります。
  
## <a name="error-handling"></a>エラー処理  
 データをテキストで区切られたファイルにエクスポートする CREATE EXTERNAL TABLE AS SELECT、ときに、エクスポートに失敗した行の却下ファイルがありません。  
  
 外部テーブルを作成するときに、データベースは外部の Hadoop クラスターまたは Azure Storage の Blob への接続を試みます。 接続に失敗した場合、コマンドは失敗し、外部テーブルは作成されません。 コマンドの接続に失敗データベース再試行後に、少なくとも 3 倍を 1 分以上かかることができます。  
  
 CREATE EXTERNAL TABLE AS SELECT が取り消されたか、失敗する場合、データベースが新しいファイルと、外部データ ソースに既に作成されたフォルダーを削除する 1 回限りの試行になります。  
  
 データベースには、データのエクスポート中に、外部データ ソースで発生する Java エラーが報告されます。  
  
##  <a name="GeneralRemarks"></a>全般的な解説  
 実行することができます、CETAS ステートメントが完了したら、[!INCLUDE[tsql](../../includes/tsql-md.md)]外部テーブルに対するクエリ。 これらの操作はデータをインポート、データベース クエリの実行中、CREATE TABLE AS SELECT ステートメントを使用してインポートする場合を除き。  
  
 外部テーブルの名前と定義は、データベースのメタデータに格納されます。 データは、外部データ ソースに格納されます。  
  
 外部ファイルの名前は *QueryID_date_time_ID.format*です ( *ID* は増分識別子、 *format* はエクスポートされるデータ形式)。 たとえば、QID776_20160130_182739_0.orc です。  
  
 CETAS ステートメントを常には、ソース テーブルがパーティション分割されている場合でも、非パーティション テーブルを作成します。  
  
 説明を databaseuses ではクエリ プランの外部テーブルに対するこれらのクエリ プランの操作を作成します。  
  
-   外部のシャッフル移動  
  
-   外部のブロードキャストを移動します。  
  
-   外部のパーティションの移動  
  
 **適用対象:**[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]アプライアンス管理者を外部テーブルを作成するための前提条件、としては、hadoop の接続を構成する必要があります。 詳細については、マニュアルを参照して外部データ (Analytics Platform System) への接続を構成する APS からダウンロードできます[ここ](http://www.microsoft.com/download/details.aspx?id=48241)です。  
  
## <a name="limitations-and-restrictions"></a>制限事項と制約事項  
 以降、データベース、バックアップの外部で外部テーブルのデータが存在して、復元操作は、データベースに格納されたデータにのみ作用します。 つまり、メタデータのみのバックアップおよび復元されます。  
  
 データベースでは、外部テーブルを含むデータベースのバックアップを復元するときに、外部データ ソースへの接続は確認されません。 元のソースがアクセスできない場合は、外部テーブルのメタデータの復元も成功しますが、外部テーブルに対する SELECT 操作が失敗します。  
  
 データベースでは、外部データ用のデータベース間でデータの一貫性は保証されません。 、、顧客は、お客様が外部のデータとデータベース間の一貫性を維持します。  
  
 データ操作言語 (DML) 操作は、テーブルの外部ではサポートされません。 たとえば、使用することはできません、 [!INCLUDE[tsql](../../includes/tsql-md.md)] update、insert、または delete[!INCLUDE[tsql](../../includes/tsql-md.md)]外部のデータを変更するステートメント。  
  
 CREATE TABLE、DROP TABLE、CREATE STATISTICS、DROP STATISTICS、CREATE VIEW、および DROP VIEW は、テーブルの外部で許可される唯一のデータ定義言語 (DDL) 操作です。  
  
 PolyBase は 32 の同時実行 PolyBase クエリを実行している場合、最大で 1 つのフォルダーの 33 k ファイルを使用できます。 この最大数には、各 HDFS フォルダー内のファイルとサブフォルダーの両方が含まれます。 同時実行の程度が 32 未満である場合は、ユーザーは、複数の 33 k ファイルが含まれている HDFS のフォルダーに対して PolyBase クエリを実行できます。 [!INCLUDE[msCoName](../../includes/msconame-md.md)]Hadoop と PolyBase のことをお勧めユーザーは、短いファイル パスを維持し、1 つの HDFS フォルダー 30 個を超える k ファイルを使用します。 ファイルが多すぎますが参照されている場合は、JVM のメモリ不足の例外が発生します。  
  
 [SET ROWCOUNT と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/set-rowcount-transact-sql.md)この CREATE EXTERNAL TABLE AS SELECT に影響を与えません。 同様の動作を実現するために使用[TOP &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/queries/top-transact-sql.md).  
  
 CREATE EXTERNAL TABLE AS SELECT、RCFile から選択をしたときに、RCFile で列の値を含めないでくださいパイプ ' |' 文字です。  
  
## <a name="locking"></a>ロック  
 SCHEMARESOLUTION オブジェクト上には、共有ロックを取得します。  
  
##  <a name="Examples"></a> 使用例  
  
### <a name="a-create-a-hadoop-table-using-create-external-table-as-select-cetas"></a>A. 作成する外部テーブルとして選択 (CETAS) を使用して Hadoop テーブルを作成します。  
 次の例は、という名前の新しい外部テーブルを作成`hdfsCustomer`、列の定義と、ソース テーブルからデータを使用して`dimCustomer`です。  
  
 テーブルの定義は、データベースに格納され、SELECT ステートメントの結果にエクスポートする、'/pdwdata/customer.tbl' Hadoop の外部データ ソース上のファイル*customer_ds*です。 ファイルが外部ファイル形式に従って書式設定された*customer_ff*です。  
  
 ファイル名は、データベースによって生成され、それを生成するクエリを含んだファイルの配置が容易なクエリ ID が含まれています。  
  
 パス`hdfs://xxx.xxx.xxx.xxx:5000/files/`前に、顧客ディレクトリに存在する必要があります。 ただし、顧客ディレクトリが存在しない場合、データベースは、ディレクトリを作成します。  
  
> [!NOTE]  
>  この例は、5000 を指定します。 ポートが指定されていない場合、データベースは、既定のポートとして 8020 を使用します。  
  
 場所とファイル名になります結果として得られる Hadoop`hdfs:// xxx.xxx.xxx.xxx:5000/files/Customer/ QueryID_YearMonthDay_HourMinutesSeconds_FileIndex.txt.`です。  
  
```  
  
      -- Example is based on AdventureWorks   
CREATE EXTERNAL TABLE hdfsCustomer  
WITH (  
        LOCATION='/pdwdata/customer.tbl',  
        DATA_SOURCE = customer_ds,  
        FILE_FORMAT = customer_ff  
) AS SELECT * FROM dimCustomer;  
```  
  
### <a name="b-use-a-query-hint-with-create-external-table-as-select-cetas"></a>B. CREATE EXTERNAL TABLE AS を持つクエリ ヒントを使用する (CETAS) を選択します。  
 このクエリは、CETAS ステートメントと共にクエリの結合ヒントを使用するための基本構文を示しています。 データベースでは、ハッシュ結合の方法を使用して、クエリ プランを生成するクエリが送信されるとします。 結合ヒントや、OPTION 句を使用する方法の詳細については、次を参照してください。 [OPTION 句と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/queries/option-clause-transact-sql.md).  
  
> [!NOTE]  
>  この例は、5000 を指定します。 ポートが指定されていない場合、データベースは、既定のポートとして 8020 を使用します。  
  
```  
  
      -- Example is based on AdventureWorks  
CREATE EXTERNAL TABLE dbo.FactInternetSalesNew  
WITH   
    (   
        LOCATION = '/files/Customer',  
        DATA_SOURCE = customer_ds,  
        FILE_FORMAT = customer_ff  
    )  
AS SELECT T1.* FROM dbo.FactInternetSales T1 JOIN dbo.DimCustomer T2  
ON ( T1.CustomerKey = T2.CustomerKey )  
OPTION ( HASH JOIN );  
```  
  
## <a name="see-also"></a>参照  
 [CREATE EXTERNAL DATA SOURCE &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-data-source-transact-sql.md)   
 [CREATE EXTERNAL FILE FORMAT &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-file-format-transact-sql.md)   
 [CREATE EXTERNAL TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-table-transact-sql.md)   
 [TABLE &#40; を作成します。Azure SQL Data Warehouse、並列データ ウェアハウス &#41;](~/t-sql/statements/create-table-azure-sql-data-warehouse.md)   
 [テーブルとして選択 &#40; を作成します。Azure SQL Data Warehouse &#41;](../../t-sql/statements/create-table-as-select-azure-sql-data-warehouse.md)   
 [DROP TABLE &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-table-transact-sql.md)   
 [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)  
  
  


