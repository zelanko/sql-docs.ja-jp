---
title: "データベース (並列データ ウェアハウス) を作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: pdw
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 40cacde4-ac72-45f7-9564-d76e2b4a741a
caps.latest.revision: "13"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 622dd3433ad5cb900dbbcb23777add948ea5474b
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="create-database-parallel-data-warehouse"></a>データベース (並列データ ウェアハウス) を作成します。
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  新しいデータベースを作成、[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]アプライアンスです。 このステートメントを使用する、アプライアンスのデータベースに関連付けられているすべてのファイルを作成して、最大サイズとデータベースのテーブルとトランザクション ログの自動拡張オプションを設定します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [TRANSACT-SQL 構文表記規則 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
CREATE DATABASE database_name   
WITH (   
    [ AUTOGROW = ON | OFF , ]   
    REPLICATED_SIZE = replicated_size [ GB ] ,  
    DISTRIBUTED_SIZE = distributed_size [ GB ] ,  
    LOG_SIZE = log_size [ GB ] )  
[;]  
```  
  
## <a name="arguments"></a>引数  
 *database_name*  
 新しいデータベースの名前。 許可されているデータベース名の詳細についてを参照してください「オブジェクトの名前付け規則」と「データベース名の予約」、[!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)]です。  
  
 自動拡張 = ON |**OFF**  
 指定するかどうか、 *replicated_size*、 *distributed_size*、および*log_size*の指定を超える必要に応じて、このデータベースのパラメーターが自動的に拡大サイズ。 既定値は**OFF**です。  
  
 自動拡張が ON の場合、 *replicated_size*、 *distributed_size*、および*log_size*として拡張されます (指定した初期のサイズのブロック) ではなく各データの挿入に必要なupdate、またはその他の操作を既に割り当てられているより多くのストレージを必要とします。  
  
 自動拡張がオフの場合は、サイズが自動的に拡張されません。 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]必要な操作をしようとしたときにエラーが返されます*replicated_size*、 *distributed_size*、または*log_size*指定した値より大きくなることにします。  
  
 いずれかのすべてのサイズのオンまたはオフにすべてのサイズが自動拡張します。 たとえば、自動拡張 ON に設定することはない*log_size*、に対して設定されていませんが、 *replicated_size*です。  
  
 *replicated_size* [GB]  
 正の数値。 レプリケートされたテーブルと対応するデータに割り当てられた合計領域の整数または 10 進数ギガバイト単位でサイズを設定*各コンピューティング ノードで*です。 最小値と最大の*replicated_size*要件を参照してください「最小値と最大値」、[!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)]です。  
  
 自動拡張が ON の場合は、この制限を超えるレプリケートされたテーブルが許可されます。  
  
 挿入を既存のレプリケートされたデータは、テーブル、または、既存の更新ではなくサイズが増加するようにテーブルがレプリケートされる場合は、ユーザーが、新しいレプリケートされたテーブルを作成しようとすると、エラーが返されます自動拡張がオフの場合は、 *replicated_size*.  
  
 *distributed_size* [GB]  
 正の数値。 分散テーブル (および対応するデータ) に割り当てられた合計領域を整数または 10 進数ギガバイト単位で、サイズ*アプライアンスにわたって*です。 最小値と最大の*distributed_size*要件を参照してください「最小値と最大値」、[!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)]です。  
  
 自動拡張が ON の場合は、この制限を超える分散テーブルが許可されます。  
  
 Insert のデータを既存の分散がテーブル、またはを超えるサイズが増加するように既存の分散テーブルを更新する場合は、ユーザーが新しい分散テーブルを作成しようとすると、自動拡張がオフの場合、エラーが返されます*distributed_size*.  
  
 *log_size* [GB]  
 正の数値。 整数または 10 進数ギガバイト単位でのトランザクション ログのサイズ*アプライアンスにわたって*です。  
  
 最小値と最大の*log_size*要件を参照してください「最小値と最大値」、[!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)]です。  
  
 自動拡張が ON の場合は、この制限を超えるログ ファイルが許可されています。 使用して、 [DBCC SHRINKLOG (Azure SQL Data Warehouse)](../../t-sql/database-console-commands/dbcc-shrinklog-azure-sql-data-warehouse.md)ステートメントを元のサイズにログ ファイルのサイズを小さきます。  
  
 アクション以外の個々 のコンピューティング ノードでログのサイズが増加するためにユーザーにエラーが返されます自動拡張がオフの場合は、 *log_size*です。  
  
## <a name="permissions"></a>Permissions  
 必要があります、 **CREATE ANY DATABASE**メンバーシップまたは、master データベースの権限、 **sysadmin**固定サーバー ロール。  
  
 次の例は、データベース ユーザー Fay にデータベースを作成する権限を与えます。  
  
```  
USE master;  
GO  
GRANT CREATE ANY DATABASE TO [Fay];  
GO  
```  
  
## <a name="general-remarks"></a>全般的な解説  
 データベースが作成されます互換性は、データベース互換性レベル 120 とレベルを[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]です。 これにより、データベースがすべての使用できる、 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] PDW を使用する機能。  
  
## <a name="limitations-and-restrictions"></a>制限事項と制約事項  
 CREATE DATABASE ステートメントは、明示的なトランザクションでは許可されません。 詳細については、次を参照してください。[ステートメント](../../t-sql/statements/statements.md)です。  
  
 データベースでの最小値と最大の制約については、「最小値と最大値」を参照してください、[!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)]です。  
  
 データベースの作成時、必要がある十分な空き領域*各コンピューティング ノードで*を次のサイズの合計を割り当てます。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]テーブルを持つデータベースのサイズ*replicated_table_size*です。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]テーブルを持つデータベースのサイズ (*distributed_table_size* /コンピューティング ノードの数)。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログのサイズ (*log_size* /コンピューティング ノードの数)。  
  
## <a name="locking"></a>ロック  
 データベース オブジェクトの共有ロックを取得します。  
  
## <a name="metadata"></a>メタデータ  
 この操作に成功したら、エントリにこのデータベースが表示されますが、 [sys.databases &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)と[sys.objects &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)メタデータのビューです。  
  
## <a name="examples-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="a-basic-database-creation-examples"></a>A. 基本的なデータベースの作成例  
 次の例は、データベースを作成`mytest`レプリケートされたテーブル、分散テーブルは、アプライアンスあたり 500 GB、100 GB あたりのトランザクション ログのアプライアンスにコンピューティング ノードあたり 100 GB の記憶域の割り当てとします。 この例では自動拡張は既定で無効です。  
  
```  
CREATE DATABASE mytest  
   WITH   
   (REPLICATED_SIZE = 100 GB,  
   DISTRIBUTED_SIZE = 500 GB,  
   LOG_SIZE = 100 GB );  
```  
  
 次の例は、データベースを作成`mytest`と上と同じパラメーターを除くその自動拡張がオンになっています。 これにより、データベース、指定したサイズのパラメーターの外側に拡張できます。  
  
```  
CREATE DATABASE mytest  
   WITH   
   (AUTOGROW = ON,  
   REPLICATED_SIZE = 100 GB,  
   DISTRIBUTED_SIZE = 500 GB,  
   LOG_SIZE = 100 GB);  
```  
  
### <a name="b-creating-a-database-with-partial-gigabyte-sizes"></a>B. 部分的なギガバイト サイズでデータベースを作成します。  
 次の例は、データベースを作成`mytest`自動拡張オフ、1 つのレプリケートされたテーブルのコンピューティング ノードは 1.5 GB、分散テーブルは、アプライアンスごと 5.25 GB と 10 GB のトランザクション ログのアプライアンスごとの記憶域の割り当てを指定しています。  
  
```  
CREATE DATABASE mytest  
   WITH   
   (REPLICATED_SIZE = 1.5 GB,  
   DISTRIBUTED_SIZE = 5.25 GB,  
   LOG_SIZE = 10 GB);  
```  
  
## <a name="see-also"></a>参照  
 [ALTER DATABASE &#40;です。並列データ ウェアハウス&#41;](../../t-sql/statements/alter-database-parallel-data-warehouse.md)   
 [DROP DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/drop-database-transact-sql.md)  
  
  
