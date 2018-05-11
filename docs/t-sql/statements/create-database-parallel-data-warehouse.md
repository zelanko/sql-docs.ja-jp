---
title: CREATE DATABASE (並列データ ウェアハウス) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: pdw
ms.component: t-sql|statements
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 40cacde4-ac72-45f7-9564-d76e2b4a741a
caps.latest.revision: 13
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: a7cef1f977e59e8145a57c806d7edaeb262b1275
ms.sourcegitcommit: d2573a8dec2d4102ce8882ee232cdba080d39628
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
---
# <a name="create-database-parallel-data-warehouse"></a>CREATE DATABASE (並列データ ウェアハウス)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] アプライアンスで新しいデータベースを作成します。 このステートメントを使用し、アプライアンス データベースに関連付けられているすべてのファイルを作成し、データベース テーブルとトランザクション ログの最大サイズと自動増加オプションを設定します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則 &#40;Transact-SQL&#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
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
 新しいデータベースの名前。 許容されるデータベース名の詳細については、[!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)]の "オブジェクトの名前付け規則" と "予約済みデータベース名" を参照してください。  
  
 AUTOGROW = ON | **OFF**  
 このデータベースの *replicated_size*、*distributed_size*、*log_size* パラメーターを必要に応じ、指定サイズを超えて自動増加するのかどうかを指定します。 既定値は **OFF** です。  
  
 AUTOGROW が ON の場合、*replicated_size*、*distributed_size*、*log_size* は、割り当て以上の記憶域を必要とするデータの挿入、更新、その他のアクションごとに、必要に応じて増加します (最初に指定したサイズのブロックではなく)。  
  
 AUTOGROW が OFF の場合、サイズは自動増加しません。 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] は、*replicated_size*、*distributed_size*、*log_size* がその指定値を超えて増加することが要求されるアクションを試行するとエラーを返します。  
  
 AUTOGROW はすべてのサイズに対して ON にするか、すべてのサイズに対して OFF にします。 たとえば、*log_size* に対して AUTOGROW を ON に設定し、*replicated_size* に対しては ON に設定しないということはできません。  
  
 *replicated_size* [ GB ]  
 正の数。 *計算ノードごとに*、複製テーブルと対応データに割り当てる合計領域のサイズを設定します (整数または 10 進数の GB)。 *replicated_size* の最小要件と最大要件については、[!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)] の "最小値と最大値" を参照してください。  
  
 AUTOGROW が ON の場合、複製テーブルはこの上限を超えて増加できます。  
  
 AUTOGROW が OFF の場合、ユーザーが新しい複製テーブルを作成しようとしたり、既存の複製テーブルにデータを挿入しようとしたり、サイズが *replicated_size* を超えるのに既存の複製テーブルを更新しようとするとエラーが返されます。  
  
 *distributed_size* [ GB ]  
 正の数。 *アプライアンス全体で*分散テーブル (と対応データ) に割り当てる合計領域のサイズ (整数または 10 進数の GB)。 *distributed_size* の最小要件と最大要件については、[!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)] の "最小値と最大値" を参照してください。  
  
 AUTOGROW が ON の場合、分散テーブルはこの上限を超えて増加できます。  
  
 AUTOGROW が OFF の場合、ユーザーが新しい分散テーブルを作成しようとしたり、既存の分散テーブルにデータを挿入しようとしたり、サイズが *distributed_size* を超えるのに既存の分散テーブルを更新しようとするとエラーが返されます。  
  
 *log_size* [ GB ]  
 正の数。 *アプライアンス全体*のトランザクション ログのサイズ (整数または 10 進数の GB)。  
  
 *log_size* の最小要件と最大要件については、[!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)] の "最小値と最大値" を参照してください。  
  
 AUTOGROW が ON の場合、ログ ファイルはこの上限を超えて増加できます。 ログ ファイルのサイズを元のサイズまで減らすには、[DBCC SHRINKLOG (Azure SQL Data Warehouse)](../../t-sql/database-console-commands/dbcc-shrinklog-azure-sql-data-warehouse.md) ステートメントを使用します。  
  
 AUTOGROW が OFF の場合、個々の計算ノードで、ログ サイズが *log_size* を超えて増加するようなアクションが行われると、ユーザーにエラーが返されます。  
  
## <a name="permissions"></a>アクセス許可  
 master データベースの **CREATE ANY DATABASE** 許可または **sysadmin** 固定サーバー ロールのメンバーシップが必要です。  
  
 次の例は、データベース ユーザー Fay にデータベースを作成する権限を与えます。  
  
```  
USE master;  
GO  
GRANT CREATE ANY DATABASE TO [Fay];  
GO  
```  
  
## <a name="general-remarks"></a>全般的な解説  
 データベースはデータベース互換性レベル 120 で作成されます。これは [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] の互換性レベルです。 この互換性によって、PDW で使用されるすべての [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 機能をデータベースで使用できます。  
  
## <a name="limitations-and-restrictions"></a>制限事項と制約事項  
 CREATE DATABASE ステートメントは、明示的なトランザクションでは使用できません。 詳細については、「[ステートメント](../../t-sql/statements/statements.md)」を参照してください。  
  
 データベースの制約の最小値と最大値については、[!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)] の "最小値と最大値" を参照してください。  
  
 データベースを作成するときは、次のサイズの組み合わせ合計を割り当てるために、*計算ノードごとに*十分な空き領域が必要になります。  
  
-   テーブルのサイズが *replicated_table_size* の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベース。  
  
-   テーブルのサイズが (*distributed_table_size* / 計算ノードの数) の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベース。  
  
-   ログのサイズが (*log_size* / 計算ノードの数) の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。  
  
## <a name="locking"></a>ロック  
 DATABASE オブジェクトを共有ロックします。  
  
## <a name="metadata"></a>メタデータ  
 この操作に成功すると、このデータベースのエントリがメタデータ ビューの [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) と [sys.objects &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md) に表示されます。  
  
## <a name="examples-includesspdwincludessspdw-mdmd"></a>例: [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="a-basic-database-creation-examples"></a>A. 基本的データベース作成の例  
 次の例では、データベース `mytest` を作成します。複製テーブルの記憶域割り当ては計算ノードごとに 100 GB、分散テーブルの記憶域割り当てはアプライアンスごとに 500 GB、トランザクション ログの記憶域割り当てはアプライアンスごとに 100 GB です。 この例では、AUTOGROW は既定の OFF です。  
  
```  
CREATE DATABASE mytest  
   WITH   
   (REPLICATED_SIZE = 100 GB,  
   DISTRIBUTED_SIZE = 500 GB,  
   LOG_SIZE = 100 GB );  
```  
  
 次の例では上の例と同じパラメーターでデータベース `mytest` を作成しますが、AUTOGROW を ON にします。 指定サイズ パラメーターを超えてデータベースは増加できます。  
  
```  
CREATE DATABASE mytest  
   WITH   
   (AUTOGROW = ON,  
   REPLICATED_SIZE = 100 GB,  
   DISTRIBUTED_SIZE = 500 GB,  
   LOG_SIZE = 100 GB);  
```  
  
### <a name="b-creating-a-database-with-partial-gigabyte-sizes"></a>B. 小数点以下を含む GB サイズでデータベースを作成する  
 次の例では、データベース `mytest` を作成します。AUTOGROW は OFF です。複製テーブルの記憶域割り当ては計算ノードごとに 1.5 GB、分散テーブルの記憶域割り当てはアプライアンスごとに 5.25 GB、トランザクション ログの記憶域割り当てはアプライアンスごとに 10 GB です。  
  
```  
CREATE DATABASE mytest  
   WITH   
   (REPLICATED_SIZE = 1.5 GB,  
   DISTRIBUTED_SIZE = 5.25 GB,  
   LOG_SIZE = 10 GB);  
```  
  
## <a name="see-also"></a>参照  
 [ALTER DATABASE &#40;並列データ ウェアハウス&#41;](../../t-sql/statements/alter-database-parallel-data-warehouse.md)   
 [DROP DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/drop-database-transact-sql.md)  
  
  
