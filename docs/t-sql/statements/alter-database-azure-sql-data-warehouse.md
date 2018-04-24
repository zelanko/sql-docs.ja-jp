---
title: ALTER DATABASE (Azure SQL Data Warehouse) | Microsoft Docs
ms.custom: ''
ms.date: 02/15/2018
ms.prod: ''
ms.prod_service: sql-data-warehouse
ms.reviewer: ''
ms.service: sql-data-warehouse
ms.component: t-sql|statements
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: da712a46-5f8a-4888-9d33-773e828ba845
caps.latest.revision: 20
author: barbkess
ms.author: barbkess
manager: craigg
monikerRange: = azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: 893d777d40446be2feeb5583312877222be6707d
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="alter-database-azure-sql-data-warehouse"></a>ALTER DATABASE (Azure SQL データ ウェアハウス)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

データベースの名前、最大サイズ、またはサービス目標を変更します。  
  
![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
ALTER DATABASE database_name  

  MODIFY NAME = new_database_name  
| MODIFY ( <edition_option> [, ... n] )  
  
<edition_option> ::=   
      MAXSIZE = { 
            250 | 500 | 750 | 1024 | 5120 | 10240 | 20480 
          | 30720 | 40960 | 51200 | 61440 | 71680 | 81920 
          | 92160 | 102400 | 153600 | 204800 | 245760 
      } GB  
      | SERVICE_OBJECTIVE = { 
            'DW100' | 'DW200' | 'DW300' | 'DW400' | 'DW500' 
          | 'DW600' | 'DW1000' | 'DW1200' | 'DW1500' | 'DW2000' 
          | 'DW3000' | 'DW6000' | 'DW1000c' | 'DW1500c' | 'DW2000c' 
          | 'DW2500c' | 'DW3000c' | 'DW5000c' | 'DW6000c' | 'DW7500c' 
          | 'DW10000c' | 'DW15000c' | 'DW30000c'
      }  
```  
  
## <a name="arguments"></a>引数  
*database_name*  
変更するデータベースの名前を指定します。  

MODIFY NAME = *new_database_name*  
データベースの名前を、*new_database_name* で指定した名前に変更します。  
  
MAXSIZE  
既定値は 245,760 GB (240 TB) です。  

**適用対象:** エラスティック用に最適化パフォーマンス レベル

データベースの最大許容サイズ。 データベースは MAXSIZE を超えることはできません。 

**適用対象:** 計算用に最適化パフォーマンス レベル

データベースの行ストア データの最大許容サイズ。 行ストア テーブル、列ストア インデックスのデルタストア、またはクラスター化列ストア インデックスの非クラスター化インデックスに格納されているデータは MAXSIZE を超えることはできません。  列ストア形式に圧縮されたデータにはサイズ制限はなく、MAXSIZE に制約されません。 
  
SERVICE_OBJECTIVE  
パフォーマンス レベルを指定します。 [!INCLUDE[ssSDW_md](../../includes/sssdw-md.md)] のサービス目標の詳細については、[パフォーマンス レベル](https://azure.microsoft.com/documentation/articles/performance-tiers/)に関するページを参照してください。  
  
## <a name="permissions"></a>アクセス許可  
これらのアクセス許可が必要です。  
  
-   サーバー レベル プリンシパル ログイン (プロビジョニング処理で作成されたもの) または  
  
-   `dbmanager` データベース ロールのメンバー。  
  
所有者が `dbmanager` ロールのメンバーである場合を除き、データベースの所有者はデータベースを変更することはできません。  
  
## <a name="general-remarks"></a>全般的な解説  
現在のデータベースは、変更対象とは異なるデータベースである必要があります。したがって、**ALTER は master データベースに接続されている間に実行する必要があります**。  
  
SQL Data Warehouse は COMPATIBILITY_LEVEL 130 に設定されており、変更することはできません。 詳細については、「[ALTER DATABASE (TRANSACT-SQL) の互換性レベル](https://azure.microsoft.com/documentation/articles/sql-database-compatibility-level-query-performance-130/)」を参照してください。
  
データベースのサイズを縮小するには、[DBCC SHRINKDATABASE](../../t-sql/database-console-commands/dbcc-shrinkdatabase-transact-sql.md) を使用します。  
  
## <a name="limitations-and-restrictions"></a>制限事項と制約事項  
ALTER DATABASE を実行するには、データベースをオンラインにする必要があり、一時停止状態にすることはできません。  
  
ALTER DATABASE ステートメントは、既定のトランザクション管理モードには自動コミット モードで実行する必要があります。 これは、接続の設定で設定されます。  
  
ALTER DATABASE ステートメントでは、ユーザー定義のトランザクションを含めることはできません。

データベースの照合順序を変更することはできません。  
  
## <a name="examples"></a>使用例  
これらの例を実行する前に、変更対象のデータベースが現在のデータベースでないことを確認します。 現在のデータベースは、変更対象とは異なるデータベースである必要があります。したがって、**ALTER は master データベースに接続されている間に実行する必要があります**。  

### <a name="a-change-the-name-of-the-database"></a>A. データベースの名前を変更します。  

```  
ALTER DATABASE AdventureWorks2012  
MODIFY NAME = Northwind;  
```  
  
### <a name="b-change-max-size-for-the-database"></a>B. データベースの最大サイズを変更します。  
  
```  
ALTER DATABASE dw1 MODIFY ( MAXSIZE=10240 GB );  
```  
  
### <a name="c-change-the-performance-level"></a>C. パフォーマンス レベルを変更します。  
  
```  
ALTER DATABASE dw1 MODIFY ( SERVICE_OBJECTIVE= 'DW1200' );  
```  
  
### <a name="d-change-the-max-size-and-the-performance-level"></a>D. 最大サイズとパフォーマンス レベルを変更します。  
  
```  
ALTER DATABASE dw1 MODIFY ( MAXSIZE=10240 GB, SERVICE_OBJECTIVE= 'DW1200' );  
```  
  
## <a name="see-also"></a>参照  
[CREATE DATABASE (Azure SQL Data Warehouse)](../../t-sql/statements/create-database-azure-sql-data-warehouse.md)
[SQL Data Warehouse の参照トピック](https://azure.microsoft.com/en-us/documentation/articles/sql-data-warehouse-overview-reference/)  
  
