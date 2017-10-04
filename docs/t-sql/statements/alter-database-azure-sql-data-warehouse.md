---
title: "ALTER DATABASE (Azure SQL Data Warehouse) |Microsoft ドキュメント"
ms.custom:
- MSDN content
- MSDN - SQL DB
ms.date: 03/03/2017
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
ms.assetid: da712a46-5f8a-4888-9d33-773e828ba845
caps.latest.revision: 20
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b5e328da952c853409437f7c3a4993f17022de22
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="alter-database-azure-sql-data-warehouse"></a>ALTER DATABASE (Azure SQL データ ウェアハウス)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx_md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

名前、最大サイズは、またはデータベースのサービス目標を変更します。  
  
![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
ALTER DATABASE database_name  

  MODIFY NAME = new_database_name  
| MODIFY ( <edition_option> [, ... n] )  
  
<edition_option> ::=   
      MAXSIZE = { 250 | 500 | 750 | 1024 | 5120 | 10240 | 20480 | 30720 | 40960 | 51200 | 61440 | 71680 | 81920 | 92160 | 102400 | 153600 | 204800 | 245760 } GB  
    | SERVICE_OBJECTIVE = { 'DW100' | 'DW200' | 'DW300' | 'DW400' | 'DW500' | 'DW600' | 'DW1000' | 'DW1200' | 'DW1500' | 'DW2000' | 'DW3000' | 'DW6000'}  
```  
  
## <a name="arguments"></a>引数  
*database_name*  
変更するデータベースの名前を指定します。  

MODIFY NAME = *new_database_name*  
として指定された名前のデータベースの名前を変更*new_database_name*です。  
  
MAXSIZE  
データベースの最大サイズまでを拡張することがあります。 この値を設定すると、設定サイズを超えてデータベース サイズの増加ができなくなります。 既定値*MAXSIZE* 10240 gb (10 TB) を指定しない場合。 その他の考えられる値の範囲は 250 GB から最大 240 TB です。  
  
SERVICE_OBJECTIVE  
パフォーマンス レベルを指定します。 サービス目標の詳細については[!INCLUDE[ssSDW_md](../../includes/sssdw-md.md)]を参照してください[SQL データ ウェアハウスのスケールのパフォーマンス](https://azure.microsoft.com/documentation/articles/sql-data-warehouse-manage-compute-overview/)です。  
  
## <a name="permissions"></a>Permissions  
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
  
