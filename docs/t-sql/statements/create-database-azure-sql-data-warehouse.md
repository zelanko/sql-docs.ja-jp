---
title: CREATE DATABASE (Azure SQL Data Warehouse) | Microsoft Docs
ms.custom: ''
ms.date: 02/14/20178
ms.prod: ''
ms.prod_service: sql-data-warehouse
ms.reviewer: ''
ms.service: sql-data-warehouse
ms.component: t-sql|statements
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: = azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: 621d348cface10d459693fc64b261fc2fa2ddf04
ms.sourcegitcommit: d2573a8dec2d4102ce8882ee232cdba080d39628
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
---
# <a name="create-database-azure-sql-data-warehouse"></a>データベース (Azure SQL データ ウェアハウス) を作成します。
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

新しいデータベースを作成します。  
  
## <a name="syntax"></a>構文  
  
```  
CREATE DATABASE database_name [ COLLATE collation_name ]  
(  
    [ MAXSIZE = { 
          250 | 500 | 750 | 1024 | 5120 | 10240 | 20480 | 30720 
        | 40960 | 51200 | 61440 | 71680 | 81920 | 92160 | 102400 
        | 153600 | 204800 | 245760 
      } GB ,
    ]  
    EDITION = 'datawarehouse',  
    SERVICE_OBJECTIVE = { 
         'DW100' | 'DW200' | 'DW300' | 'DW400' | 'DW500' | 'DW600' 
        | 'DW1000' | 'DW1200' | 'DW1500' | 'DW2000' | 'DW3000' | 'DW6000' 
        | 'DW1000c' | 'DW1500c' | 'DW2000c' | 'DW2500c' | 'DW3000c' | 'DW5000c' 
        | 'DW6000c' | 'DW7500c' | 'DW10000c' | 'DW15000c' | 'DW30000c'
    }  
)  
[;]  
```  
  
## <a name="arguments"></a>引数  
*database_name*  
新しいデータベースの名前。 この名前は、[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] データベースと [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] データベースの両方をホストでき、ID の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の規則に従う、SQL Server に固有のものである必要があります。 詳細については、「[データベース識別子](http://go.microsoft.com/fwlink/p/?LinkId=180386)」を参照してください。  
  
*collation_name*  
データベースの既定の照合順序を指定します。 照合順序名には、Windows 照合順序名または SQL 照合順序名を指定できます。 指定しない場合、既定の照合順序である SQL_Latin1_General_CP1_CI_AS がデータベースに割り当てられます。  
  
Windows と SQL の照合順序名の詳細については、[COLLATE (Transact-SQL)](http://msdn.microsoft.com/library/ms184391.aspx) に関するページを参照してください。  
  
*EDITION*  
データベースのサービス層を指定します。 [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] では、'datawarehouse' を使用します。  
  
*MAXSIZE*  
既定値は 245,760 GB (240 TB) です。  

**適用対象:** エラスティック用に最適化パフォーマンス レベル

データベースの最大許容サイズ。 データベースは MAXSIZE を超えることはできません。 

**適用対象:** 計算用に最適化パフォーマンス レベル

データベースの行ストア データの最大許容サイズ。 行ストア テーブル、列ストア インデックスのデルタストア、またはクラスター化列ストア インデックスの非クラスター化インデックスに格納されているデータは MAXSIZE を超えることはできません。  列ストア形式に圧縮されたデータにはサイズ制限はなく、MAXSIZE に制約されません。
  
SERVICE_OBJECTIVE  
パフォーマンス レベルを指定します。 [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] のサービス目標の詳細については、[パフォーマンス レベル](https://azure.microsoft.com/documentation/articles/performance-tiers/)に関するページを参照してください。  
  
## <a name="general-remarks"></a>全般的な解説  
データベースのプロパティを参照するには、[DATABASEPROPERTYEX &#40;Transact-SQL&#41;](../../t-sql/functions/databasepropertyex-transact-sql.md) を使用します。  
  
後で最大サイズ、またはサービス目標の値を変更するには、[ALTER DATABASE &#40;Azure SQL Data Warehouse&#41;](../../t-sql/statements/alter-database-azure-sql-data-warehouse.md) を使用します。   

SQL Data Warehouse は COMPATIBILITY_LEVEL 130 に設定されており、変更することはできません。 詳細については、「[ALTER DATABASE (TRANSACT-SQL) の互換性レベル](https://azure.microsoft.com/documentation/articles/sql-database-compatibility-level-query-performance-130/)」を参照してください。
  
## <a name="permissions"></a>アクセス許可  
必要なアクセスを許可します。  
  
-   サーバー レベル プリンシパル ログイン、プロビジョニングのプロセスによって作成されたか、  
  
-   `dbmanager` データベース ロールのメンバー。  
  
## <a name="error-handling"></a>エラー処理  
データベースのサイズが MAXSIZE に達するとエラー コード 40544 が表示されます。 このような場合は、挿入、データを更新して (テーブル、ストアド プロシージャ、ビュー、関数など) の新しいオブジェクトを作成またはことはできません。 まだ読み取りとデータを削除、テーブルの切り捨て、テーブルやインデックスを削除してインデックスを再構築できます。 これを解決するには、MAXSIZE を現在のデータベースのサイズより大きい値にするか、一部のデータを削除してストレージ領域を解放します。 新しいデータを挿入できるようになるまでに、最大で 15 分の遅延が生じる可能性があります。  
  
## <a name="limitations-and-restrictions"></a>制限事項と制約事項  
新しいデータベースを作成するには、master データベースに接続している必要があります。  
  
`CREATE DATABASE` ステートメントが [!INCLUDE[tsql](../../includes/tsql-md.md)] バッチ内の唯一のステートメントである必要があります。

データベースを作成した後、データベースの照合順序を変更することはできません。   
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd"></a>例: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]  
  
### <a name="a-simple-example"></a>A. 簡単な例  
データ ウェアハウスのデータベースを作成するための簡単な例です。 これにより、10240 GB、既定の照合順序は SQL_Latin1_General_CP1_CI_AS、最小のコンピューティング能力が DW100 の、最小の最大サイズのデータベースが作成されます。  
  
```  
CREATE DATABASE TestDW  
(EDITION = 'datawarehouse', SERVICE_OBJECTIVE='DW100');  
```  
  
### <a name="b-create-a-data-warehouse-database-with-all-the-options"></a>B. すべてのオプションを使用して、データ ウェアハウス データベースを作成します。  
作成の例は、すべてのオプションを使用して 10 テラバイトのデータ ウェアハウスです。  
  
```  
CREATE DATABASE TestDW COLLATE Latin1_General_100_CI_AS_KS_WS  
(MAXSIZE = 10240 GB, EDITION = 'datawarehouse', SERVICE_OBJECTIVE = 'DW1000');  
```  
  
## <a name="see-also"></a>参照  
[ALTER DATABASE &#40;Azure SQL Data Warehouse&#40;](../../t-sql/statements/alter-database-azure-sql-data-warehouse.md)
[CREATE TABLE &#40;Azure SQL Data Warehouse&#41;](../../t-sql/statements/create-table-azure-sql-data-warehouse.md) 
[DROP DATABASE &#40;Transact-SQL&#40;](../../t-sql/statements/drop-database-transact-sql.md) 
  

