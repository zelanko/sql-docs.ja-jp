---
title: DBCC SHRINKDATABASE (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- DBCC_SHRINKDATABASE_TSQL
- DBCC SHRINKDATABASE
- SHRINKDATABASE_TSQL
- SHRINKDATABASE
dev_langs:
- TSQL
helpviewer_keywords:
- data shrinking [SQL Server]
- shrinking files
- shrinking databases
- DBCC SHRINKDATABASE statement
- decreasing database size
- file shrinking [SQL Server]
- database shrinking [SQL Server]
- logs [SQL Server], shrinking
- reducing database size
ms.assetid: fc976afd-1edb-4341-bf41-c4a42a69772b
caps.latest.revision: 62
author: uc-msft
ms.author: umajay
manager: craigg
ms.openlocfilehash: b6fe7fcf315849e6779b66087e8a87d2953d96d0
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="dbcc-shrinkdatabase-transact-sql"></a>DBCC SHRINKDATABASE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

指定したデータベース内のデータ ファイルとログ ファイルのサイズを圧縮します。
  
![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>構文  
  
```sql
DBCC SHRINKDATABASE   
( database_name | database_id | 0   
     [ , target_percent ]   
     [ , { NOTRUNCATE | TRUNCATEONLY } ]   
)  
[ WITH NO_INFOMSGS ]  
```  
  
## <a name="arguments"></a>引数  
 *database_name* | *database_id* | 0  
 圧縮するデータベースの名前または ID を指定します。 0 を指定すると、現在のデータベースが選択されます。  
  
 *target_percent*  
 データベースを圧縮した後、データベース ファイル内に残す空き領域のパーセンテージを指定します。  
  
 NOTRUNCATE  
 ファイル末尾の割り当て済みページをファイル先頭の未割り当てページに移動することにより、データ ファイルのデータを圧縮します。 *target_percent* は省略可能です。 このオプションは Azure SQL Data Warehouse ではサポートされません。 
  
 ファイル末尾の空き領域はオペレーティング システムに返されず、ファイルの物理サイズは変わりません。 したがって、NOTRUNCATE を指定した場合は、データベースが圧縮されていないように見えます。  
  
 NOTRUNCATE はデータ ファイルにのみ適用され、 ログ ファイルは影響を受けません。  
  
 TRUNCATEONLY  
 ファイル末尾のすべての空き領域をオペレーティング システムに渡します。ただし、ファイル内でのページの移動は行われません。 データ ファイルは、最後に割り当てられたエクステントを限度として圧縮されます。 *target_percent* は、TRUNCATEONLY と共に指定した場合、無視されます。 このオプションは Azure SQL Data Warehouse ではサポートされません。
  
 TRUNCATEONLY はログ ファイルに影響します。 データ ファイルのみを切り捨てるには、DBCC SHRINKFILE を使用します。  
  
 WITH NO_INFOMSGS  
 重大度レベル 0 から 10 のすべての情報メッセージを表示しないようにします。  
  
## <a name="result-sets"></a>結果セット  
次の表では、結果セットの列について説明します。
  
|列名|Description|  
|-----------------|-----------------|  
|**DbId**|[!INCLUDE[ssDE](../../includes/ssde-md.md)]で圧縮が試行されたファイルのデータベース識別番号。|  
|**FileId**|[!INCLUDE[ssDE](../../includes/ssde-md.md)]で圧縮が試行されたファイルのファイル識別番号。|  
|**CurrentSize**|ファイルが現在占有する 8 KB ページの数。|  
|**MinimumSize**|ファイルが占有できる 8 KB ページの最小数。 この値は、ファイルの最小サイズまたは最初に作成されたサイズと一致します。|  
|**UsedPages**|ファイルが現在使用している 8 KB ページの数。|  
|**EstimatedPages**|[!INCLUDE[ssDE](../../includes/ssde-md.md)]で推定されるファイル圧縮後の 8 KB ページの数。|  
  
>[!NOTE]
> [!INCLUDE[ssDE](../../includes/ssde-md.md)]では圧縮されないファイルの行は表示されません。  
  
## <a name="remarks"></a>Remarks  
特定のデータベースに関するすべてのデータとログ ファイルを圧縮するには、DBCC SHRINKDATABASE コマンドを実行します。 特定のデータベースで一度に 1 つのデータまたはログ ファイルを圧縮するには、[DBCC SHRINKFILE](../../t-sql/database-console-commands/dbcc-shrinkfile-transact-sql.md) コマンドを実行します。
  
データベースの空き (未割り当て) 領域の現在の量を表示するには、[sp_spaceused](../../relational-databases/system-stored-procedures/sp-spaceused-transact-sql.md) を実行します。
  
DBCC SHRINKDATABASE 操作は、プロセスのどの時点でも中断でき、中断時に完了していた作業は保持されます。
  
データベースは、そのデータベースの最小サイズより小さくすることはできません。 最小サイズは、データベースの最初の作成時に指定したサイズ、または DBCC SHRINKFILE や ALTER DATABASE のファイル サイズ変更操作によって最後に明示的に設定されたサイズのどちらかになります。 たとえば、最初の作成時にサイズを 10 MB に指定したデータベースが 100 MB まで拡張した場合は、データベース内のすべてのデータを削除したとしても、縮小できる限界は 10 MB までです。
  
NOTRUNCATE オプションも TRUNCATEONLY オプションも指定しないで DBCC SHRINKDATABASE を実行した場合は、NOTRUNCATE を指定して DBCC SHRINKDATABASE 操作を実行した後に、TRUNCATEONLY を指定して DBCC SHRINKDATABASE 操作を実行した場合と同じ結果になります。
  
圧縮されるデータベースは、シングル ユーザー モードになっていなくてもかまいません。データベースを圧縮している最中でも、他のユーザーがそのデータベースで作業することができます。 システム データベースの場合も同様です。
  
データベースのバックアップ中、データベースを圧縮することはできません。 逆に、データベースの圧縮操作の進行中、データベースをバックアップすることはできません。

>[!NOTE]
> 現在、Azure SQL Data Warehouse では TDE が有効になっている DBCC SHRINKDATABASE はサポートされません。
  
## <a name="how-dbcc-shrinkdatabase-works"></a>DBCC SHRINKDATABASE の動作  
DBCC SHRINKDATABASE では、データ ファイルはファイルごとに圧縮されますが、ログ ファイルはすべてが 1 つの連続的なログ プールに存在するものとして圧縮されます。 ファイルは常に末尾から圧縮されます。
  
たとえば、**mydb** という名前のデータベースに、1 つのデータ ファイルと 2 つのログ ファイルがあり、 各データ ファイルとログ ファイルのサイズは 10 MB で、データ ファイルに 6 MB のデータが含まれているとします。
  
この場合、それぞれのファイルについて、[!INCLUDE[ssDE](../../includes/ssde-md.md)]では目標サイズが計算されます。 これはファイルの圧縮後のサイズです。 DBCC SHRINKDATABASE を *target_percent* と共に指定すると、[!INCLUDE[ssDE](../../includes/ssde-md.md)]では、圧縮後にファイル内の空き領域が *target_percent* になるように目標サイズが計算されます。 たとえば、**mydb** を圧縮する場合に *target_percent* を 25 に指定すると、[!INCLUDE[ssDE](../../includes/ssde-md.md)]ではデータ ファイルの目標サイズが 8 MB (6 MB のデータに 2 MB の空き領域を加えたもの) と計算されます。 したがって、[!INCLUDE[ssDE](../../includes/ssde-md.md)]ではデータ ファイルの末尾 2 MB にあるすべてのデータがデータ ファイルの先頭 8 MB にある空き領域に移動されてから、ファイルが圧縮されます。
  
次に、**mydb** のデータ ファイルに 7 MB のデータが含まれているとします。 *target_percent* を 30 に指定した場合、このデータ ファイルは空き領域のパーセンテージが 30 になるように圧縮されます。 ただし、*target_percent* を 40 に指定した場合、データ ファイルは圧縮されません。[!INCLUDE[ssDE](../../includes/ssde-md.md)]では、圧縮後のファイル サイズが現在のデータ占有領域よりも小さくなる場合、ファイルは圧縮されません。 別の考え方をすれば、目的の空き領域 40% にデータ ファイル最大容量の 70% (10 MB 中の 7 MB) を加算すると、100% を超えます。 30 を超える値を *target_size* に指定すると、目的の空き領域のパーセンテージと、データ ファイルの現在の占有パーセンテージを加算した値が 100% を超えるので (この場合は 10% 超過)、データ ファイルは圧縮されません。
  
ログ ファイルの場合、[!INCLUDE[ssDE](../../includes/ssde-md.md)]では *target_percent* を使用してログ全体の目標サイズが計算されるため、*target_percent* は圧縮処理後のログ内の空き領域サイズになります。 計算の後、ログ全体の目標サイズは各ログ ファイルの目標サイズに変換されます。
  
DBCC SHRINKDATABASE では、各物理ログ ファイルの目標サイズへの圧縮がすぐに試行されます。 ログ ファイルの目標サイズを超える仮想ログ内に論理ログの部分がない場合は、ログ ファイルは目標サイズまで正常に切り捨てられ、DBCC SHRINKDATABASE はメッセージなしで終了します。 ただし、論理ログの一部が、目標サイズを超える仮想ログ内に存在する場合は、[!INCLUDE[ssDE](../../includes/ssde-md.md)]により、できるだけ多くの領域が解放され、情報メッセージが発行されます。 このメッセージには、ファイルの末尾で仮想ログから論理ログを移動するために行う必要のある操作が説明されています。 この操作を実行した後、DBCC SHRINKDATABASE を使って、残りの領域を解放できます。
  
ログ ファイルは仮想ログ ファイルの境界を越えて圧縮できないため、ログ ファイルを仮想ログ ファイルのサイズより小さく圧縮することはできません。これはログ ファイルが使用されていない場合でも同じです。 [!INCLUDE[ssDE](../../includes/ssde-md.md)]では、ログ ファイルの作成時または拡張時に仮想ログ ファイルのサイズが動的に選択されます。
  
## <a name="best-practices"></a>ベスト プラクティス  
データベースを圧縮する場合は次のことを考慮してください。
-   圧縮操作は、テーブルの切り捨てやテーブルの削除操作など、大きな未使用領域を生成する操作の後に実行すると最も効果的です。  
-   ほとんどのデータベースでは、毎日の定期的操作で使用するための空き領域が必要です。 データベースを何度圧縮しても、データベースのサイズが大きくなってしまう場合は、通常の操作にそれだけの領域が必要であることを示しています。 このような場合、繰り返しデータベースを圧縮することは無意味です。  
-   圧縮操作では、データベース内のインデックスの断片化状態は保持されず、一般に、断片化の程度が大きくなります。 この理由からも、データベースを繰り返し圧縮することはお勧めできません。  
-   特別な要件がない限り、AUTO_SHRINK データベース オプションを ON に設定しないでください。  
  
## <a name="troubleshooting"></a>トラブルシューティング  
 [行のバージョン管理に基づく分離レベル](../../t-sql/statements/set-transaction-isolation-level-transact-sql.md)で実行されているトランザクションによって圧縮操作がブロックされる可能性があります。 たとえば、DBCC SHRINK DATABASE 操作を実行するときに、行のバージョン管理に基づく分離レベルでの大規模な削除操作が進行中の場合、圧縮操作は削除処理が完了してから実行され、ファイルが圧縮されます。 この場合、DBCC SHRINKFILE および DBCC SHRINKDATABASE 操作によって、最初の 1 時間は 5 分ごと、それ以降は 1 時間ごとに、情報メッセージ (SHRINKDATABASE は 5202、SHRINKFILE は 5203) が [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラー ログに出力されます。 たとえば、エラー ログに次のエラー メッセージが含まれているとします。  
  
```sql
DBCC SHRINKDATABASE for database ID 9 is waiting for the snapshot   
transaction with timestamp 15 and other snapshot transactions linked to   
timestamp 15 or with timestamps older than 109 to finish.  
```  
  
これは、圧縮操作が、109 より古いタイムスタンプが存在する、圧縮操作の完了された最後のトランザクションがスナップショット トランザクションによってブロックされていることを意味します。 また、[sys.dm_tran_active_snapshot_database_transactions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-tran-active-snapshot-database-transactions-transact-sql.md) 動的管理ビューの **transaction_sequence_num** 列または **first_snapshot_sequence_num** 列に、値 15 が含まれることも示しています。 このビューの **transaction_sequence_num** 列または **first_snapshot_sequence_num** 列のいずれかに、圧縮操作により完了した最後のトランザクション (109) より低い番号が含まれている場合は、それらのトランザクションが終了するまで圧縮操作は待機状態となります。
  
この問題を解決するために、次のいずれかの作業を実行できます。
-   圧縮操作をブロックしているトランザクションを終了します。  
-   圧縮操作を終了します。 完了済みの作業は保持されます。  
-   何もせず、ブロックしているトランザクションが完了するまで圧縮操作を待機状態にしておきます。  
  
## <a name="permissions"></a>アクセス許可  
 **sysadmin** 固定サーバー ロールまたは **db_owner** 固定データベース ロールのメンバーシップが必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-shrinking-a-database-and-specifying-a-percentage-of-free-space"></a>A. データベースを圧縮し、空き領域のパーセンテージを指定する  
 次の例では、`UserDB` ユーザー データベース内のデータ ファイルとログ ファイルのサイズを圧縮して、データベースの空き領域が 10% になるようにします。  
  
```sql  
DBCC SHRINKDATABASE (UserDB, 10);  
GO  
```  
  
### <a name="b-truncating-a-database"></a>B. データベースを切り捨てる  
 次の例では、`AdventureWorks` サンプル データベースのデータ ファイルとログ ファイルを、最後に割り当てられたエクステントまで圧縮します。  
  
```sql  
DBCC SHRINKDATABASE (AdventureWorks2012, TRUNCATEONLY);  
```  
  
## <a name="see-also"></a>参照  
[ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)  
[DBCC &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-transact-sql.md)  
[DBCC SHRINKFILE &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-shrinkfile-transact-sql.md)  
[データベースの圧縮](../../relational-databases/databases/shrink-a-database.md)
  
  
