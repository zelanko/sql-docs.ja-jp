---
title: "テーブル (Azure SQL データ ウェアハウス) を作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/14/2017
ms.prod: 
ms.reviewer: 
ms.service: sql-data-warehouse
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: ea21c73c-40e8-4c54-83d4-46ca36b2cf73
caps.latest.revision: 59
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 11df71495b55ca72074c6ab928caaf6474bb2576
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="create-table-azure-sql-data-warehouse"></a>テーブル (Azure SQL データ ウェアハウス) を作成します。
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw_md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  新しいテーブルを作成[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]または[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]です。  
 
テーブルとその使用方法を理解するのを参照してください。 [SQL データ ウェアハウス内のテーブル](https://azure.microsoft.com/documentation/articles/sql-data-warehouse-tables-overview/)です。

注: この記事で SQL データ ウェアハウスに関するディスカッション適用 SQL Data Warehouse と並列データ ウェアハウスの両方に明記されない限り、します。 
 
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  

<a name="Syntax"></a>   
## <a name="syntax"></a>構文  
  
```  
-- Create a new table. 
CREATE TABLE [ database_name . [ schema_name ] . | schema_name. ] table_name   
    ( 
      { column_name <data_type>  [ <column_options> ] } [ ,...n ]   
    )  
    [ WITH [ <table_option> [ ,...n ] ) ]  
[;]  
   
<column_options> ::=
    [ COLLATE Windows_collation_name ]  
    [ NULL | NOT NULL ] -- default is NULL  
    [ [ CONSTRAINT constraint_name ] DEFAULT constant_expression  ]
  
<table_option> ::= 
    {   
        CLUSTERED COLUMNSTORE INDEX --default for SQL Data Warehouse 
      | HEAP --default for Parallel Data Warehouse   
      | CLUSTERED INDEX ( { index_column_name [ ASC | DESC ] } [ ,...n ] ) -- default is ASC 
    }  
    { 
        DISTRIBUTION = HASH ( distribution_column_name ) 
      | DISTRIBUTION = ROUND_ROBIN -- default for SQL Data Warehouse
      | DISTRIBUTION = REPLICATE -- default for Parallel Data Warehouse
    }   
    | PARTITION ( partition_column_name RANGE [ LEFT | RIGHT ] -- default is LEFT  
        FOR VALUES ( [ boundary_value [,...n] ] ) )  
  
<data type> ::=   
      datetimeoffset [ ( n ) ]  
    | datetime2 [ ( n ) ]  
    | datetime  
    | smalldatetime  
    | date  
    | time [ ( n ) ]  
    | float [ ( n ) ]  
    | real [ ( n ) ]  
    | decimal [ ( precision [ , scale ] ) ]   
    | numeric [ ( precision [ , scale ] ) ]   
    | money  
    | smallmoney  
    | bigint  
    | int   
    | smallint  
    | tinyint  
    | bit  
    | nvarchar [ ( n | max ) ]  -- max applies only to SQL Data Warehouse 
    | nchar [ ( n ) ]  
    | varchar [ ( n | max )  ] -- max applies only to SQL Data Warehouse  
    | char [ ( n ) ]  
    | varbinary [ ( n | max ) ] -- max applies only to SQL Data Warehouse  
    | binary [ ( n ) ]  
    | uniqueidentifier  
```  

<a name="Arguments"></a>   
## <a name="arguments"></a>引数  
 *database_name*  
 新しいテーブルを格納するデータベースの名前です。 既定値は現在のデータベースです。  
  
 *schema_name*  
 テーブルのスキーマです。 指定する*スキーマ*は省略可能です。 空白の場合は、既定のスキーマが使用されます。  
  
 *table_name*  
 新しいテーブルの名前です。 ローカル一時テーブルを作成するには、# でテーブル名を前に付けます。  説明と一時テーブルの詳細については、次を参照してください。 [Azure SQL データ ウェアハウス内の一時テーブル](https://azure.microsoft.com/documentation/articles/sql-data-warehouse-tables-temporary/)です。 
 
 *column_name*  
 テーブルの列の名前です。
   
### <a name="ColumnOptions"></a>列のオプション

 `COLLATE`*Windows_collation_name*  
 式の照合順序を指定します。 照合順序でサポートされている Windows 照合順序のいずれかを指定する必要があります[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 サポートされている Windows 照合順序の一覧については[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を参照してください[Windows 照合順序名 (TRANSACT-SQL)](http://msdn.microsoft.com/library/ms188046\(v=sql11\)/)です。  
  
 `NULL` | `NOT NULL`  
 指定するかどうか`NULL`列で値を許容します。 既定値は `NULL` です。  
  
 [ `CONSTRAINT` *constraint_name* ] `DEFAULT` *constant_expression*  
 列の既定値を指定します。  
  
 | 引数 | 説明 |
 | -------- | ----------- |
 | *constraint_name* | (省略可能) 制約の名前です。 制約名は、データベース内で一意です。 名前は、他のデータベース内で再利用できます。 |
 | *constant_expression* | 列の既定値。 式は、リテラル値である必要があります、または定数。 たとえば、これらの定数式が許可されている: `'CA'`、`4`です。 これらは許可されていません: `2+3`、`CURRENT_TIMESTAMP`です。 |
  

### <a name="TableOptions"></a>テーブル構造のオプション
テーブルの種類を選択する方法の詳細については、次を参照してください。 [Azure SQL データ ウェアハウス内のテーブルのインデックス作成](https://docs.microsoft.com/azure/sql-data-warehouse/sql-data-warehouse-tables-index/)です。
  
 `CLUSTERED COLUMNSTORE INDEX`  
クラスター化列ストア インデックスとしてテーブルを格納します。 クラスター化列ストア インデックスは、すべてのテーブルのデータに適用されます。 これは、既定の[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]します。   
 
 `HEAP`   
  テーブルをヒープとして格納します。 これは、既定の[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]します。  
  
 `CLUSTERED INDEX`( *index_column_name* [,...*n* ] )  
 1 つまたは複数のキー列を含むクラスター化インデックスとしてテーブルを格納します。 これは、行によって、データを格納します。 使用して*index_column_name*をインデックスに 1 つまたは複数のキー列の名前を指定します。  詳細については、全般的な解説内の行ストア テーブルを参照してください。
 
 `LOCATION = USER_DB`   
 このオプションは推奨されません。 不要になったが構文的に受け入れてし、不要になった動作に影響します。   
  
### <a name="TableDistributionOptions"></a>テーブルの配布オプション
最適な配布方法を選択して、分散テーブルを使用する方法を理解するを参照してください[Azure SQL データ ウェアハウス内のテーブルを配布する](https://azure.microsoft.com/documentation/articles/sql-data-warehouse-tables-distribute/)です。

`DISTRIBUTION = HASH`( *distribution_column_name* )   
1 つの配布に各行を割り当てに格納された値をハッシュして*distribution_column_name*です。 つまり、同じディストリビューションに同じ値を常にハッシュ アルゴリズムは決定的です。  ディストリビューション列は、NULL が同じ配布に割り当てられるあるすべての行から NOT NULL として定義する必要があります。

`DISTRIBUTION = ROUND_ROBIN`   
行に、ラウンド ロビン方式でのすべてのディストリビューションに均等に分散します。 これは、既定の[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]します。

`DISTRIBUTION = REPLICATE`    
各コンピューティング ノードで、テーブルの 1 つのコピーを格納します。 [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]各コンピューティング ノードでディストリビューション データベースのテーブルが格納されます。 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]でテーブルが格納されている、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]コンピューティング ノードにまたがるファイル グループ。 これは、既定の[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]します。
  
### <a name="TablePartitionOptions"></a>テーブル パーティションのオプション
テーブルのパーティションを使用する方法の詳細については、次を参照してください。 [SQL データ ウェアハウス内のテーブルをパーティション分割](https://azure.microsoft.com/documentation/articles/sql-data-warehouse-tables-partition/)です。

 `PARTITION`( *partition_column_name* `RANGE` [ `LEFT`  |  `RIGHT` ] `FOR VALUES` ([ *boundary_value* [,...*n*] ] ))   
1 つまたは複数のテーブルのパーティションを作成します。 これらは、テーブルがヒープ、クラスター化インデックスまたはクラスター化列ストア インデックスとして格納されているかどうかに関係なく行のサブセットに対して操作を実行することは横方向のテーブルのスライスです。 配布 列とは異なりテーブルのパーティションは、各行が格納されている配布を特定できません。 代わりに、テーブルのパーティションは、行をグループ化し、各配布内に格納する方法を決定します。  
 
| 引数 | 説明 |
| -------- | ----------- |
|*partition_column_name*| 列を指定する[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]行をパーティション分割に使用されます。 このコラムでは、任意のデータ型を指定できます。 [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]パーティション列の値で昇順に並べ替えられます。 低-高に順序付けがから`LEFT`に`RIGHT`の目的、`RANGE`仕様です。 |  
| `RANGE LEFT` | (低い値) の左側にある、パーティションに属する境界値を指定します。 既定値は LEFT です。 |
| `RANGE RIGHT` | 右 (値を大きく) 上のパーティションに属する境界値を指定します。 | 
| `FOR VALUES`( *boundary_value* [,...*n*] ) | パーティションの境界値を指定します。 *boundary_value*定数式です。 NULL は指定できません。 必要がありますかと一致かのデータ型に暗黙的に変換できる*partition_column_name*です。 サイズと値の小数点以下桁数でのデータ型が一致しないようにには、暗黙の変換中に切り捨てられることはできません*partition_column_name*<br></br><br></br>指定した場合、`PARTITION`句、境界値を指定しないで[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]1 つのパーティション分割されたテーブルが作成されます。 該当する場合、後で 2 つのパーティションにテーブルを分割します。<br></br><br></br>結果のテーブルに 2 つのパーティションに 1 つの境界値を指定する場合境界値よりも大きい値のいずれかの境界値と下限の値のいずれかです。 非パーティション テーブルにパーティションを移動する場合、非パーティション テーブル、データを受け取るがそのメタデータでパーティション境界はありませんに注意してください。| 
 
 参照してください[パーティション テーブルを作成](#PartitionedTable)例」のセクションでします。

### <a name="DataTypes"></a>データ型
[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]最も一般的に使用されるデータ型をサポートしています。 以下は、詳細情報とストレージのバイトと共にサポートされるデータ型の一覧を示します。 データ型とその使用方法を理解するには、次を参照してください。 [ SQL データ ウェアハウス内のテーブルのデータ型](https://azure.microsoft.com/documentation/articles/sql-data-warehouse-tables-data-types)です。

データ型変換のテーブルの場合の暗黙的な変換セクションを参照してください。 [CAST および CONVERT (TRANSACT-SQL)](http://msdn.microsoft.com/library/ms187928/)です。

`datetimeoffset` [ ( *n* ) ]  
 既定値 *n* は 7 です。  
  
 `datetime2` [ ( *n* ) ]  
同じ`datetime`, 秒の小数部の数を指定する点が異なります。 既定値 *n* は`7`します。  
  
|*n*値|有効桁数|Scale|  
|--:|--:|-:|  
|`0`|19|0|  
|`1`|21|1|  
|`2`|22|2|  
|`3`|23|3|  
|`4`|24|4|  
|`5`|25|5|  
|`6`|26|6|  
|`7`|27|7|  
  
 `datetime`  
 構成のグレゴリオ暦カレンダーに従って 19 ～ 23 の文字の 1 日の日付と時刻を格納します。 日付には、年、月、および日を含めることができます。 時間には、時間、分、秒数が含まれています。オプションでは、秒の小数部の 3 桁の数字を表示できます。 記憶領域のサイズは 8 バイトです。  
  
 `smalldatetime`  
 日付と時刻を格納します。 記憶域のサイズは、4 バイトです。  
  
 `date`  
 最大 10 文字を使用して年、月、および構成のグレゴリオ暦カレンダーにおける日付を格納します。 記憶域のサイズは、3 バイトです。 日付は、整数として保存されます。  
  
 `time` [ ( *n* ) ]  
 既定値 *n* は`7`します。  
  
 `float` [ ( *n* ) ]  
 浮動小数点数値データで使用するおおよその数のデータを入力します。 浮動小数点データは概数、つまりデータ型の範囲内のすべての値を正確に表すことができます。 *n*仮数を格納するために使用するビット数を指定します、`float`科学的表記法でします。 したがって、  *n* 有効桁数およびストレージのサイズに影響します。 場合 *n* の間の値をする必要があります指定`1`と`53`です。 既定値の *n* は`53`します。  
  
| *n*値 | 有効桁数 | ストレージのサイズ |  
| --------: | --------: | -----------: |  
| 1-24   | 7 桁の数字  | 4 バイト      |  
| 25-53  | 15 桁 | 8 バイト      |  
  
 [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]扱います *n* として 2 つの値のいずれか。 場合`1` <=   *n*   <=  `24`、  *n* として扱われる`24`です。 場合`25`  <=   *n*   <=  `53`、  *n* として扱われる`53`です。  
  
 [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] `float`データ型は、のすべての値、ISO 標準に準拠している *n* から`1`を通じて`53`です。 倍精度のシノニムは`float(53)`します。  
  
 `real` [ ( *n* ) ]  
 実際の定義は、浮動小数点数と同じです。 ISO シノニムは、`real`は`float(24)`します。  
  
 `decimal`[(*精度*[ *、小数点以下桁数*])] |`numeric` [(*精度*[ *、小数点以下桁数*])]  
 固定有効桁数と小数点以下桁数の数値を保存します。  
  
 *有効桁数 (precision)*  
 小数点の右側および左側にある保存できる最大文字 (数字) 数の合計です。 有効桁数が値を指定する必要があります`1`の最大有効桁数を`38`です。 既定の有効桁数は`18`します。  
  
 *scale*  
 小数点の右側にある保存できる最大文字 (数字) 数です。 *スケール*値を指定する必要があります`0`を通じて*精度*です。 のみを指定できます*スケール*場合*精度*を指定します。 既定のスケールは`0`。 したがって、 `0`  <= *スケール* <= *精度*です。 ストレージの最大サイズは有効桁数によって異なります。  
  
| 有効桁数 | ストレージのバイト サイズ  |  
| ---------: |-------------: |  
|  1-9       |             5 |  
| 10-19      |             9 |  
| 20-28      |            13 |  
| 29-38      |            17 |  
  
 `money` | `smallmoney`  
 通貨値を表すデータ型。  
  
| データ型 | ストレージのバイト サイズ |  
| --------- | ------------: |  
| `money`|8|  
| `smallmoney` |4|  
  
 `bigint` | `int` | `smallint` | `tinyint`  
 整数データを使用する実数データ型です。 次の表に、記憶域が表示されます。  
  
| データ型 | ストレージのバイト サイズ |  
| --------- | ------------: |  
| `bigint`|8|  
| `int` |4|  
| `smallint` |2|  
| `tinyint` |1|  
  
 `bit`  
 整数データ型の値が実行できる`1`、 `0`、または ' NULL です。 [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]ビット列の記憶域を最適化します。 テーブル内で 8 個以下のビット列がある場合は、列が 1 バイトとして格納されます。 9 ～ 16 ビット列の場合、列は 2 バイトとしては保存されなど。  
  
 `nvarchar`[(  *n*   |  `max` )]-`max`にのみ適用されます[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]です。  
 可変長の UNICODD 文字データです。 *n*1 ~ 4000 の値を指定できます。 `max` は最大格納サイズが 2^31-1 バイト (2 GB) であることを示します。 記憶域のサイズ (バイト単位) は、入力した + 2 バイトの 2 倍の数です。 入力データの長さは 0 文字でもかまいません。  
  
 `nchar` [ ( *n* ) ]  
 固定長の Unicode 文字データの長さと *n* 文字です。 *n*値を指定する必要があります`1`を通じて`4000`です。 ストレージのサイズは 2 回 *n* バイトです。  
  
 `varchar`[(  *n*    |  `max` )]-`max`にのみ適用されます[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]です。   
 可変長の Unicode 以外の文字データの長さと *n* バイトです。 *n*値を指定する必要があります`1`に`8000`です。 `max`ストレージの最大サイズが 2 であることを示します。 ^ 31-1 バイト (2 GB)。ストレージ サイズは、入力したデータの実際の長さ + 2 バイトです。  
  
 `char` [ ( *n* ) ]  
 固定長 Unicode 以外の文字データの長さと *n* バイトです。 *n*値を指定する必要があります`1`に`8000`です。 ストレージのサイズは *n* バイトです。 既定の *n* は`1`します。  
  
 `varbinary`[(  *n*    |  `max` )]-`max`にのみ適用されます[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]です。  
 可変長 binary データ。 *n*値を指定できます`1`に`8000`です。 `max` は最大格納サイズが 2^31-1 バイト (2 GB) であることを示します。 記憶領域のサイズは、入力されたデータの実際の長さに 2 バイトを加えたものとなります。 既定値 *n* は 7 です。  
  
 `binary` [ ( *n* ) ]  
 固定長バイナリ データの長さと *n* バイトです。 *n*値を指定できます`1`に`8000`です。 ストレージのサイズは *n* バイトです。 既定値 *n* は`7`します。  
  
 `uniqueidentifier`  
 16 バイトの GUID です。  
   
<a name="Permissions"></a>  
## <a name="permissions"></a>Permissions  
 テーブルを作成するには、権限が必要です、`db_ddladmin`固定データベース ロール、または。
 - `CREATE TABLE`データベースに対する権限
 - `ALTER SCHEMA`テーブルを含むスキーマの権限。 

パーティション分割されたテーブルを作成するには、権限が必要です、`db_ddladmin`固定データベース ロール、または

- `ALTER ANY DATASPACE`アクセス許可
  
 ローカル一時テーブルを作成するログインを受け取る`CONTROL`、 `INSERT`、 `SELECT`、および`UPDATE`テーブルに対する権限。  
 
<a name="GeneralRemarks"></a>  
## <a name="general-remarks"></a>全般的な解説  
 
最小と最大値では、次を参照してください。 [SQL データ ウェアハウスの処理能力の限界](https://azure.microsoft.com/documentation/articles/sql-data-warehouse-service-capacity-limits/)です。 
 
### <a name="determining-the-number-of-table-partitions"></a>テーブルのパーティションの数を決定します。
各ユーザー定義テーブルは、配布と呼ばれる別の場所に格納されている複数の小さなテーブルに分割されます。 [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]60 の配布を使用します。 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]ディストリビューションの数は、コンピューティング ノードの数によって異なります。
 
各配布には、すべてのテーブルのパーティションが含まれています。 たとえば、60 の配布と 4 つのテーブルのパーティションがある場合は、320 のパーティションがあります。 テーブルがクラスター化列ストア インデックスの場合、列ストア インデックスは 320 columnstore インデックスを作成する必要があるパーティション 1 つがあります。

列ストア インデックスの利点を活用するために十分な行が少ないテーブル パーティションようを使用して各列ストア インデックスをお勧めします。 さらにガイダンスについては、次を参照してください[SQL データ ウェアハウス内のテーブルをパーティション分割](https://azure.microsoft.com/documentation/articles/sql-data-warehouse-tables-partition/)と[SQL データ ウェアハウス内のテーブルのインデックス。](https://azure.microsoft.com/en-us/documentation/articles/sql-data-warehouse-tables-index/)  

  
 ### <a name="rowstore-table-heap-or-clustered-index"></a>行ストア テーブル (ヒープまたはクラスター化インデックス)  
 行ストア テーブルは、行単位での順序で格納されているテーブルです。 ヒープまたはクラスター化インデックスをお勧めします。 [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]ページの圧縮とすべての行ストア テーブルを作成します。ユーザー構成可能ではありません。   
 
 ### <a name="columnstore-table-columnstore-index"></a>列ストア テーブル (列ストア インデックス)
列ストア テーブルは、列、列の順序で格納されているテーブルです。 列ストア インデックスは、列ストア テーブルに格納されているデータを管理するテクノロジです。  クラスター化列ストア インデックスには影響しません。 データの配布方法これは、各配布内でのデータの格納方法に影響します。

列ストア テーブルに行ストア テーブルを変更するに既存のすべてのインデックス、テーブルを削除し、クラスター化列ストア インデックスを作成します。 例については、次を参照してください。 [CREATE COLUMNSTORE INDEX & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-columnstore-index-transact-sql.md).

詳細については、次の記事を参照してください。
- [列ストア インデックスのバージョン管理機能の概要](https://msdn.microsoft.com/library/dn934994/)
- [SQL データ ウェアハウス内のテーブルのインデックス](https://azure.microsoft.com/en-us/documentation/articles/sql-data-warehouse-tables-index/)
- [列ストア インデックス ガイド](~/relational-databases/indexes/columnstore-indexes-overview.md) 
 
<a name="LimitationsRestrictions"></a>  
## <a name="limitations-and-restrictions"></a>制限事項と制約事項  
 ディストリビューション列の既定の制約を定義することはできません。  
  
 ### <a name="partitions"></a>パーティション
 パーティションを使用する場合、パーティション列は、Unicode 専用の照合順序はできません。 たとえば、次のステートメントは失敗します。  
  
 `CREATE TABLE t1 ( c1 varchar(20) COLLATE Divehi_90_CI_AS_KS_WS) WITH (PARTITION (c1 RANGE FOR VALUES (N'')))`  
 
 場合*boundary_value*でのデータ型に暗黙的に変換する必要がありますをリテラル値は、 *partition_column_name*、矛盾が発生します。 通じてリテラルの値を表示、[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]システム ビュー、変換後の値が使用の[!INCLUDE[tsql](../../includes/tsql-md.md)]操作します。 
 
  
 ### <a name="temporary-tables"></a>一時テーブル
 グローバルの一時テーブルで始まる ## はサポートされていません。  
  
 ローカル一時テーブルは、次の制限事項と制約があります。  
  
-   現在のセッションにのみ表示されます。 [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]削除に自動的にセッションの最後にします。 それら explicitlt を削除するには、DROP TABLE ステートメントを使用します。   
-   名前変更できません。 
-   これらは、パーティションまたはビューにはできません。  
-   そのアクセス許可を変更することはできません。 `GRANT`、 `DENY`、および`REVOKE`ステートメントは、ローカル一時テーブルでは使用できません。   
-   データベース コンソール コマンドは、一時テーブルがブロックされます。   
-   バッチ内で 1 つ以上のローカル一時テーブルを使用した場合、一意の名前でそれぞれ必要があります。 複数のセッションが同じバッチを実行していて、同じローカル一時テーブルを作成する場合[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]内部で各ローカル一時テーブルの一意の名前を維持するためにローカル一時テーブル名に数値サフィックスを追加します。  
    
<a name="LockingBehavior"></a>   
## <a name="locking-behavior"></a>ロック動作  
 テーブルに排他ロックを取得します。 データベース、スキーマ、および SCHEMARESOLUTION オブジェクト上には、共有ロックを取得します。  
 

<a name="ExamplesColumn"></a>   
## <a name="examples-for-columns"></a>列の例

### <a name="ColumnCollation"></a> A. 列の照合順序を指定します。 
 次の例では、テーブルで`MyTable`は 2 つの異なる列の照合順序で作成します。 既定では、列、 `mycolumn1`、Latin1_General_100_CI_AS_KS_WS 既定の照合順序がします。 列、 `mycolumn2` Frisian_100_CS_AS 照合順序。  
  
```  
CREATE TABLE MyTable   
  (  
    mycolumnnn1 nvarchar,  
    mycolumn2 nvarchar COLLATE Frisian_100_CS_AS )  
WITH ( CLUSTERED COLUMNSTORE INDEX )  
;  
  
```  
  
### <a name="DefaultConstraint"></a> B. 列に既定の制約を指定します。  
 次の例では、列の既定値を指定する構文を示します。 コーラの列が constraint_colA と、既定値は 0 という名前の既定の制約です。  
  
```  
  
CREATE TABLE MyTable   
  (  
    colA int CONSTRAINT constraint_colA DEFAULT 0,  
    colB nvarchar COLLATE Frisian_100_CS_AS   
  )  
WITH ( CLUSTERED COLUMNSTORE INDEX )  
;  
```  

<a name="ExamplesTemporaryTables"></a> 
## <a name="examples-for-temporary-tables"></a>一時テーブルの例

### <a name="TemporaryTable"></a> C. ローカル一時テーブルを作成します。  
 次に、#myTable をという名前のローカル一時テーブルを作成します。 テーブルは、3 部構成の名前を指定します。 一時テーブル名を # で開始します。   
  
```  
CREATE TABLE AdventureWorks.dbo.#myTable   
  (  
   id int NOT NULL,  
   lastName varchar(20),  
   zipCode varchar(6)  
  )  
WITH  
  (   
    DISTRIBUTION = HASH (id),  
    CLUSTERED COLUMNSTORE INDEX   
  )  
;  
```

<a name="ExTableStructure"></a>  
## <a name="examples-for-table-structure"></a>テーブルの構造の例

### <a name="ClusteredColumnstoreIndex"></a> D. クラスター化列ストア インデックスを持つテーブルを作成します。  
 次の例では、クラスター化列ストア インデックスを持つ分散型のテーブルを作成します。 各配布は、列ストアとして格納されます。  
  
 クラスター化列ストア インデックスには影響しませんデータを配布する方法です。データは、行を常に分散されます。 クラスター化列ストア インデックスでは、各配布内でのデータの格納方法に影響します。  
  
```  
  
CREATE TABLE MyTable   
  (  
    colA int CONSTRAINT constraint_colA DEFAULT 0,  
    colB nvarchar COLLATE Frisian_100_CS_AS   
  )  
WITH   
  (   
    DISTRIBUTION = HASH ( colB ),  
    CLUSTERED COLUMNSTORE INDEX   
  )  
;  
```  
 
<a name="ExTableDistribution"></a> 
## <a name="examples-for-table-distribution"></a>テーブルの配布の例

### <a name="RoundRobin"></a> E. ROUND_ROBIN テーブルを作成します。  
 次の例は、3 つの列と、パーティションを使わない ROUND_ROBIN テーブルを作成します。 データはすべての配布に分散します。 クラスター化列ストア インデックス、ヒープまたは行ストア クラスター化インデックスよりも優れたパフォーマンスとデータ圧縮機能を提供する、テーブルが作成されます。  
  
```  
CREATE TABLE myTable   
  (  
    id int NOT NULL,  
    lastName varchar(20),  
    zipCode varchar(6)  
  )  
WITH ( CLUSTERED COLUMNSTORE INDEX );  
```  
  
### <a name="HashDistributed"></a> F. ハッシュ分散のテーブルを作成します。  
 次の例では、前の例と同じテーブルを作成します。 ただし、このテーブルの行が分散されます (上、`id`列) の代わりにランダムには、分散 ROUND_ROBIN テーブルのようにします。 クラスター化列ストア インデックス、ヒープまたは行ストア クラスター化インデックスよりも優れたパフォーマンスとデータ圧縮機能を提供する、テーブルが作成されます。  
  
```  
CREATE TABLE myTable   
  (  
    id int NOT NULL,  
    lastName varchar(20),  
    zipCode varchar(6)  
  )  
WITH  
  (   
    DISTRIBUTION = HASH (id),   
    CLUSTERED COLUMNSTORE INDEX  
  );  
```  
  
### <a name="Replicated"></a>G. レプリケートされたテーブルを作成します。  
 次の例では、前の例のようなレプリケートされたテーブルを作成します。 レプリケートされたテーブルは、各計算ノードに完全にコピーされます。 各コンピューティング ノードでこのコピーでは、クエリのデータ移動が小さくなります。 この例には、クラスター化インデックス、ヒープより優れたデータ圧縮を提供し、適切なクラスター化列ストア インデックスの圧縮を実現するために十分な行を含めることはできませんが作成されます。  
  
```  
CREATE TABLE myTable   
  (  
    id int NOT NULL,  
    lastName varchar(20),  
    zipCode varchar(6)  
  )  
WITH  
  (   
    DISTRIBUTION = REPLICATE,   
    CLUSTERED INDEX (lastName)  
  );  
```  

<a name="ExTablePartitions"></a> 
## <a name="examples-for-table-partitions"></a>テーブル パーティションの例

###  <a name="PartitionedTable"></a>H. パーティション テーブルを作成します。  
 例 A を追加すると、RANGE LEFT パーティションで示すように、次の例は、同じテーブルを作成、`id`列です。 その結果は 5 つのパーティションに 4 つのパーティションの境界値を指定します。  
  
```  
CREATE TABLE myTable   
  (  
    id int NOT NULL,  
    lastName varchar(20),  
    zipCode int)  
WITH   
  (   
  
    PARTITION ( id RANGE LEFT FOR VALUES (10, 20, 30, 40 )),  
    CLUSTERED COLUMNSTORE INDEX      
  )  
;  
```  
  
 この例では、データが次のパーティションに並べ替えられます。  
  
-   パーティション 1: col < = 10   
-   パーティション 2時 10分 < col < = 20   
-   パーティション 3時 20分 < col < = 30   
-   パーティション 4時 30分 < col < = 40   
-   パーティション 5時 40分 < col  
  
 この同じテーブルがパーティション分割されている場合は、次のパーティションに RANGE LEFT (既定値) の場合、データの代わりに、RANGE RIGHT が並べ替えられます。  
  
-   パーティション 1: col < 10  
-   パーティション 2時 10分 < = col < 20   
-   パーティション 3時 20分 < = col < 30    
-   パーティション 4時 30分 < = col < 40   
-   パーティション 5時 40分 < = col  
  
### <a name="OnePartition"></a>私。 1 つのパーティションを持つパーティション テーブルを作成します。  
 次の例では、1 つのパーティションをパーティション テーブルを作成します。 指定しません任意の境界値では、1 つのパーティションになります。  
  
```  
CREATE TABLE myTable (  
    id int NOT NULL,  
    lastName varchar(20),  
    zipCode int)  
WITH   
    (   
      PARTITION ( id RANGE LEFT FOR VALUES ( )),  
      CLUSTERED COLUMNSTORE INDEX  
    )  
;  
```  
  
### <a name="DatePartition"></a>J. 日付でパーティション分割テーブルを作成します。  
 次の例は、という名前の新しいテーブルを作成`myTable`にパーティション分割、`date`列です。 境界値の範囲の右側と日付を使用するは、各パーティション内の月のデータを格納します。  
  
```  
CREATE TABLE myTable (  
    l_orderkey      bigint,       
    l_partkey       bigint,                                             
    l_suppkey       bigint,                                           
    l_linenumber    bigint,        
    l_quantity      decimal(15,2),  
    l_extendedprice decimal(15,2),  
    l_discount      decimal(15,2),  
    l_tax           decimal(15,2),  
    l_returnflag    char(1),  
    l_linestatus    char(1),  
    l_shipdate      date,  
    l_commitdate    date,  
    l_receiptdate   date,  
    l_shipinstruct  char(25),  
    l_shipmode      char(10),  
    l_comment       varchar(44))  
WITH   
  (   
    DISTRIBUTION = HASH (l_orderkey),  
    CLUSTERED COLUMNSTORE INDEX,  
    PARTITION ( l_shipdate  RANGE RIGHT FOR VALUES   
      (  
        '1992-01-01','1992-02-01','1992-03-01','1992-04-01','1992-05-01',
        '1992-06-01','1992-07-01','1992-08-01','1992-09-01','1992-10-01',
        '1992-11-01','1992-12-01','1993-01-01','1993-02-01','1993-03-01',
        '1993-04-01','1993-05-01','1993-06-01','1993-07-01','1993-08-01',
        '1993-09-01','1993-10-01','1993-11-01','1993-12-01','1994-01-01',
        '1994-02-01','1994-03-01','1994-04-01','1994-05-01','1994-06-01',
        '1994-07-01','1994-08-01','1994-09-01','1994-10-01','1994-11-01',
        '1994-12-01'  
      ))
  );  
```  
  
<a name="SeeAlso"></a>    
## <a name="see-also"></a>参照 
 
 [テーブルとして選択 &#40; を作成します。Azure SQL Data Warehouse &#41;](../../t-sql/statements/create-table-as-select-azure-sql-data-warehouse.md)   
 [DROP TABLE & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-table-transact-sql.md)   
 [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)  
  
  

