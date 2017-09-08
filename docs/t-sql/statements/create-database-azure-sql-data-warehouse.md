---
title: "データベース (Azure SQL データ ウェアハウス) を作成 |Microsoft ドキュメント"
ms.custom:
- MSDN content
- MSDN - SQL DB
ms.date: 03/14/2017
ms.prod: 
ms.reviewer: 
ms.service: sql-warehouse
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 42819b93-b757-4b2c-8179-d4be3c512c19
caps.latest.revision: 20
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: a178756610f0d0e463c21a2a62a287ada6c863a1
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="create-database-azure-sql-data-warehouse"></a>データベース (Azure SQL データ ウェアハウス) を作成します。
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx_md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

新しいデータベースを作成します。  
  
## <a name="syntax"></a>構文  
  
```  
-- Syntax for Azure SQL Data Warehouse  
  
CREATE DATABASE database_name [ COLLATE collation_name ]  
(  
    [ MAXSIZE = { 250 | 500 | 750 | 1024 | 5120 | 10240 | 20480 | 30720 | 40960 | 51200 | 61440 | 71680 | 81920 | 92160 | 102400 | 153600 | 204800 | 245760 } GB ,]  
    EDITION = 'datawarehouse',  
    SERVICE_OBJECTIVE = { 'DW100' | 'DW200' | 'DW300' | 'DW400' | 'DW500' | 'DW600' | 'DW1000' | 'DW1200' | 'DW1500' | 'DW2000' | 'DW3000' | 'DW6000' }  
)  
[;]  
```  
  
## <a name="arguments"></a>引数  
*database_name*  
新しいデータベースの名前。 この名前は、両方をホストできる SQL server 上で一意である必要があります[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]データベースおよび[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]データベースに準拠している、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]識別子の規則。 詳細については、次を参照してください。[識別子](http://go.microsoft.com/fwlink/p/?LinkId=180386)です。  
  
*collation_name*  
データベースの既定の照合順序を指定します。 照合順序名には、Windows 照合順序名または SQL 照合順序名を指定できます。 指定しない場合、データベースには、既定の照合順序は SQL_Latin1_General_CP1_CI_AS が割り当てられます。  
  
Windows と SQL 照合順序名の詳細については、次を参照してください。 [COLLATE (TRANSACT-SQL)](http://msdn.microsoft.com/library/ms184391.aspx)です。  
  
*エディション*  
データベースのサービス層を指定します。 [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] 'データ ウェアハウス' を使用します。  
  
*MAXSIZE*  
データベースの最大サイズまでを拡張することがあります。 この値を設定すると、設定サイズを超えてデータベース サイズの増加ができなくなります。 既定値*MAXSIZE* 10240 gb (10 TB) を指定しない場合。  その他の考えられる値の範囲は 250 GB から最大 240 TB です。  
  
SERVICE_OBJECTIVE  
パフォーマンス レベルを指定します。 サービス目標の詳細については[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]を参照してください[SQL データ ウェアハウスのスケールのパフォーマンス](https://azure.microsoft.com/documentation/articles/sql-data-warehouse-performance-scale/)です。  
  
## <a name="general-remarks"></a>全般的な解説  
使用して[DATABASEPROPERTYEX & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/databasepropertyex-transact-sql.md)データベース プロパティを表示します。  
  
使用して[ALTER DATABASE &#40;Azure SQL Data Warehouse &#41;](../../t-sql/statements/alter-database-azure-sql-data-warehouse.md)目標の値を後でサービスを最大サイズを変更します。   

SQL データ ウェアハウスは、COMPATIBILITY_LEVEL 130 に設定されているし、変更できません。 詳細については、次を参照してください。 [Azure SQL データベースの互換性レベル 130 でのクエリ パフォーマンスの向上](https://azure.microsoft.com/documentation/articles/sql-database-compatibility-level-query-performance-130/)です。
  
## <a name="permissions"></a>Permissions  
必要なアクセスを許可します。  
  
-   サーバー レベル プリンシパル ログイン、プロビジョニングのプロセスによって作成されたか、  
  
-   メンバー、`dbmanager`データベース ロール。  
  
## <a name="error-handling"></a>エラー処理  
データベースのサイズが MAXSIZE に達するとエラー コード 40544 が表示されます。 このような場合は、挿入、データを更新して (テーブル、ストアド プロシージャ、ビュー、関数など) の新しいオブジェクトを作成またはことはできません。 まだ読み取りとデータを削除、テーブルの切り捨て、テーブルやインデックスを削除してインデックスを再構築できます。 これを解決するには、MAXSIZE を現在のデータベースのサイズより大きい値にするか、一部のデータを削除してストレージ領域を解放します。 新しいデータを挿入できるようになるまでに、最大で 15 分の遅延が生じる可能性があります。  
  
## <a name="limitations-and-restrictions"></a>制限事項と制約事項  
新しいデータベースを作成するには、master データベースに接続している必要があります。  
  
`CREATE DATABASE`ステートメントは唯一のステートメントである必要があります、[!INCLUDE[tsql](../../includes/tsql-md.md)]バッチ。

データベースを作成した後、データベースの照合順序を変更することはできません。   
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd"></a>例:[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]  
  
### <a name="a-simple-example"></a>A. 簡単な例  
データ ウェアハウスのデータベースを作成するための簡単な例です。 これは、10240 GB、既定の照合順序は SQL_Latin1_General_CP1_CI_AS、および DW100 をある最小のコンピューティング能力をある最小の最大サイズをデータベースを作成します。  
  
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
[ALTER DATABASE & #40 です。Azure SQL Data Warehouse & #40 です。](../../t-sql/statements/alter-database-azure-sql-data-warehouse.md) 
[テーブルを作成する & #40 です。Azure SQL Data Warehouse &#41;](../../t-sql/statements/create-table-azure-sql-data-warehouse.md)  
 [DATABASE &#40; を削除Transact SQL & #40 です。](../../t-sql/statements/drop-database-transact-sql.md) 
  


