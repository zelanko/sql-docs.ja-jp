---
title: "ALTER DATABASE (Azure SQL Data Warehouse) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/03/2017
ms.prod: 
ms.prod_service: sql-data-warehouse
ms.reviewer: 
ms.service: sql-data-warehouse
ms.component: t-sql|statements
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
ms.assetid: da712a46-5f8a-4888-9d33-773e828ba845
caps.latest.revision: "20"
author: barbkess
ms.author: barbkess
manager: craigg
ms.openlocfilehash: 71737beb817cfeebed195c90d056768aef678a3e
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="alter-database-azure-sql-data-warehouse"></a>ALTER DATABASE (Azure SQL データ ウェアハウス)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

名前、最大サイズは、またはデータベースのサービス目標を変更します。  
  
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
として指定された名前のデータベースの名前を変更*new_database_name*です。  
  
MAXSIZE  
既定では 10,240 GB (10 TB) です。  

**適用されます:**パフォーマンス層の柔軟性の最適化

データベースの最大許容サイズ。 データベースは、MAXSIZE を超えることはできません。 

**適用されます:**コンピューティング パフォーマンス層用に最適化されました。

データベース内の行ストア データの最大許容サイズ。 行ストア テーブル、列ストア インデックスのデルタストアまたはクラスター化列ストア インデックスに非クラスター化インデックスに格納されたデータは、MAXSIZE を超えることはできません。  列ストア形式に圧縮されたデータは、サイズの制限はありませんし、MAXSIZE による制約を受けない。 
  
SERVICE_OBJECTIVE  
パフォーマンス レベルを指定します。 サービス目標の詳細については[!INCLUDE[ssSDW_md](../../includes/sssdw-md.md)]を参照してください[パフォーマンス層](https://azure.microsoft.com/documentation/articles/performance-tiers/)です。  
  
## <a name="permissions"></a>権限  
これらのアクセス許可が必要です。  
  
-   サーバー レベル プリンシパル ログイン (プロビジョニング処理で作成されたもの) または  
  
-   メンバー、`dbmanager`データベース ロール。  
  
所有者のメンバーである場合を除き、データベースの所有者は、データベースを変更ことはできません、`dbmanager`ロール。  
  
## <a name="general-remarks"></a>全般的な解説  
現在のデータベースが別のデータベースを変更する、したがってものにする必要があります**、master データベースに接続されている場合、ALTER を実行する必要があります**です。  
  
SQL データ ウェアハウスは、COMPATIBILITY_LEVEL 130 に設定されているし、変更できません。 詳細については、次を参照してください。 [Azure SQL データベースの互換性レベル 130 でのクエリ パフォーマンスの向上](https://azure.microsoft.com/documentation/articles/sql-database-compatibility-level-query-performance-130/)です。
  
データベースのサイズを小さくを使用して[DBCC SHRINKDATABASE](../../t-sql/database-console-commands/dbcc-shrinkdatabase-transact-sql.md)です。  
  
## <a name="limitations-and-restrictions"></a>制限事項と制約事項  
ALTER DATABASE を実行するには、データベースがオンラインにする必要があり、一時停止状態にすることはできません。  
  
ALTER DATABASE ステートメントは、既定のトランザクション管理モードには自動コミット モードで実行する必要があります。 これは、接続の設定で設定されます。  
  
ALTER DATABASE ステートメントでは、ユーザー定義のトランザクションを含めることはできません。

データベースの照合順序を変更することはできません。  
  
## <a name="examples"></a>使用例  
これらの例を実行する前にデータベースを変更するが、現在のデータベースではないことを確認します。 現在のデータベースが別のデータベースを変更する、したがってものにする必要があります**、master データベースに接続されている場合、ALTER を実行する必要があります**です。  

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
[リファレンスのトピックの一覧を SQL Data Warehouse](https://azure.microsoft.com/en-us/documentation/articles/sql-data-warehouse-overview-reference/)  
  
