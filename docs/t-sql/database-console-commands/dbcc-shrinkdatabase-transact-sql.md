---
title: "DBCC SHRINKDATABASE (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/17/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
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
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c7f6e9fa3feea20bfeb82037cb9358370c67aaa0
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="dbcc-shrinkdatabase-transact-sql"></a>DBCC SHRINKDATABASE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

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
 ファイル末尾の割り当て済みページをファイル先頭の未割り当てページに移動することにより、データ ファイルのデータを圧縮します。 *target_percent*は省略可能です。  
  
 ファイル末尾の空き領域はオペレーティング システムに返されず、ファイルの物理サイズは変わりません。 したがって、NOTRUNCATE を指定した場合は、データベースが圧縮されていないように見えます。  
  
 NOTRUNCATE はデータ ファイルにのみ適用され、 ログ ファイルは影響を受けません。  
  
 TRUNCATEONLY  
 ファイル末尾のすべての空き領域をオペレーティング システムに渡します。ただし、ファイル内でのページの移動は行われません。 データ ファイルは、最後に割り当てられたエクステントを限度として圧縮されます。 *target_percent* TRUNCATEONLY と共に指定した場合は無視されます。  
  
 TRUNCATEONLY はログ ファイルに影響します。 データ ファイルのみを切り捨てるには、DBCC SHRINKFILE を使用します。  
  
 WITH NO_INFOMSGS  
 重大度レベル 0 から 10 のすべての情報メッセージを表示しないようにします。  
  
## <a name="result-sets"></a>結果セット  
次の表では、結果セットの列について説明します。
  
|列名|Description|  
|-----------------|-----------------|  
|**DbId**|[!INCLUDE[ssDE](../../includes/ssde-md.md)]で圧縮が試行されたファイルのデータベース識別番号。|  
|**FileId**|[!INCLUDE[ssDE](../../includes/ssde-md.md)]で圧縮が試行されたファイルのファイル識別番号。|  
|**現在**|ファイルが現在占有する 8 KB ページの数。|  
|**MinimumSize**|ファイルが占有できる 8 KB ページの最小数。 この値は、ファイルの最小サイズまたは最初に作成されたサイズと一致します。|  
|**UsedPages**|ファイルが現在使用している 8 KB ページの数。|  
|**EstimatedPages**|[!INCLUDE[ssDE](../../includes/ssde-md.md)]で推定されるファイル圧縮後の 8 KB ページの数。|  
  
>[!NOTE]
> [!INCLUDE[ssDE](../../includes/ssde-md.md)]では圧縮されないファイルの行は表示されません。  
  
## <a name="remarks"></a>解説  
特定のデータベースに関するすべてのデータとログ ファイルを圧縮するには、DBCC SHRINKDATABASE コマンドを実行します。 1 つのデータを圧縮または特定のデータベースでの時刻にログ ファイルは、実行、 [DBCC SHRINKFILE](../../t-sql/database-console-commands/dbcc-shrinkfile-transact-sql.md)コマンド。
  
データベースの現在の空き (未割り当て) 領域量を表示するには実行[sp_spaceused](../../relational-databases/system-stored-procedures/sp-spaceused-transact-sql.md)です。
  
DBCC SHRINKDATABASE 操作は、プロセスのどの時点でも中断でき、中断時に完了していた作業は保持されます。
  
データベースは、そのデータベースの最小サイズより小さくすることはできません。 最小サイズは、データベースの最初の作成時に指定したサイズ、または DBCC SHRINKFILE や ALTER DATABASE のファイル サイズ変更操作によって最後に明示的に設定されたサイズのどちらかになります。 たとえば、最初の作成時にサイズを 10 MB に指定したデータベースが 100 MB まで拡張した場合は、データベース内のすべてのデータを削除したとしても、縮小できる限界は 10 MB までです。
  
NOTRUNCATE オプションも TRUNCATEONLY オプションも指定しないで DBCC SHRINKDATABASE を実行した場合は、NOTRUNCATE を指定して DBCC SHRINKDATABASE 操作を実行した後に、TRUNCATEONLY を指定して DBCC SHRINKDATABASE 操作を実行した場合と同じ結果になります。
  
圧縮されるデータベースは、シングル ユーザー モードになっていなくてもかまいません。データベースを圧縮している最中でも、他のユーザーがそのデータベースで作業することができます。 システム データベースの場合も同様です。
  
データベースのバックアップ中、データベースを圧縮することはできません。 逆に、データベースの圧縮操作の進行中、データベースをバックアップすることはできません。
  
## <a name="how-dbcc-shrinkdatabase-works"></a>DBCC SHRINKDATABASE の動作  
DBCC SHRINKDATABASE では、データ ファイルはファイルごとに圧縮されますが、ログ ファイルはすべてが 1 つの連続的なログ プールに存在するものとして圧縮されます。 ファイルは常に末尾から圧縮されます。
  
という名前のデータベース**mydb**データ ファイルと 2 つのログ ファイルを使用します。 データとログ ファイルはそれぞれ 10 MB と、データ ファイルには、6 MB データにはが含まれています。
  
この場合、それぞれのファイルについて、[!INCLUDE[ssDE](../../includes/ssde-md.md)]では目標サイズが計算されます。 これはファイルの圧縮後のサイズです。 DBCC SHRINKDATABASE がで指定されている場合*target_percent*、[!INCLUDE[ssDE](../../includes/ssde-md.md)]する目標サイズが計算、 *target_percent*圧縮後のファイルで空き領域の量。 指定する場合など、 *target_percent*圧縮の対象の 25 **mydb**、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 8 mb (6 MB のデータおよび 2 MB の空き領域) にデータ ファイルの目標サイズを計算します。 したがって、[!INCLUDE[ssDE](../../includes/ssde-md.md)]にデータ ファイルの先頭 8 MB にある空き領域、データ ファイルの末尾 2 MB にあるすべてのデータを移動し、ファイルを圧縮します。
  
データ ファイルを前提としています**mydb** 7 MB データにはが含まれています。 指定する、 *target_percent* 30 のでは、30 の空き領域の割合を圧縮するのには、このデータ ファイル。 ただしを指定する、 *target_percent* 40 が圧縮されないデータ ファイルのため、[!INCLUDE[ssDE](../../includes/ssde-md.md)]データが現在占有よりも小さいサイズには、ファイルは圧縮されません。 考えることができますもこの問題の別の方法: 40% が空き領域を必要し、完全なデータ ファイルの 70% (10 MB 中の 7 MB) が 100% を超える。 空き領域のパーセンテージが必要なことと、データ ファイルを占有する現在の割合が 100% (10%) をすべてため*target_size* 30 では、データ ファイルは圧縮されませんよりも大きいです。
  
ログ ファイルの場合、[!INCLUDE[ssDE](../../includes/ssde-md.md)]を使用して*target_percent*ログ全体の目標サイズを計算するため、 *target_percent*圧縮操作後に、ログの空き領域の量は、します。 計算の後、ログ全体の目標サイズは各ログ ファイルの目標サイズに変換されます。
  
DBCC SHRINKDATABASE では、各物理ログ ファイルの目標サイズへの圧縮がすぐに試行されます。 ログ ファイルの目標サイズを超える仮想ログ内に論理ログの部分がない場合は、ログ ファイルは目標サイズまで正常に切り捨てられ、DBCC SHRINKDATABASE はメッセージなしで終了します。 ただし、論理ログの一部が、目標サイズを超える仮想ログに存在する場合、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 、できるだけ多くの領域を解放し、情報メッセージを発行します。 このメッセージには、ファイルの末尾で仮想ログから論理ログを移動するために行う必要のある操作が説明されています。 この操作を実行した後、DBCC SHRINKDATABASE を使って、残りの領域を解放できます。
  
ログ ファイルは仮想ログ ファイルの境界を越えて圧縮できないため、ログ ファイルを仮想ログ ファイルのサイズより小さく圧縮することはできません。これはログ ファイルが使用されていない場合でも同じです。 仮想ログ ファイルのサイズが動的に選択した、[!INCLUDE[ssDE](../../includes/ssde-md.md)]ログ ファイルが作成または拡張します。
  
## <a name="best-practices"></a>ベスト プラクティス  
データベースを圧縮する場合は次のことを考慮してください。
-   圧縮操作は、テーブルの切り捨てやテーブルの削除操作など、大きな未使用領域を生成する操作の後に実行すると最も効果的です。  
-   ほとんどのデータベースでは、毎日の定期的操作で使用するための空き領域が必要です。 データベースを何度圧縮しても、データベースのサイズが大きくなってしまう場合は、通常の操作にそれだけの領域が必要であることを示しています。 このような場合、繰り返しデータベースを圧縮することは無意味です。  
-   圧縮操作では、データベース内のインデックスの断片化状態は保持されず、一般に、断片化の程度が大きくなります。 この理由からも、データベースを繰り返し圧縮することはお勧めできません。  
-   特別な要件がない限り、AUTO_SHRINK データベース オプションを ON に設定しないでください。  
  
## <a name="troubleshooting"></a>トラブルシューティング  
 圧縮操作で実行されているトランザクションによってブロックされるまでに可能であれば、[行のバージョン管理に基づく分離レベル](../../t-sql/statements/set-transaction-isolation-level-transact-sql.md)です。 たとえば、DBCC SHRINK DATABASE 操作を実行するときに、行のバージョン管理に基づく分離レベルでの大規模な削除操作が進行中の場合、圧縮操作は削除処理が完了してから実行され、ファイルが圧縮されます。 この場合、DBCC SHRINKFILE および DBCC SHRINKDATABASE 操作の出力に情報メッセージ (SHRINKDATABASE は 5202、SHRINKFILE は 5203)、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エラー ログの最初の 1 時間に 5 分ごととし、1 時間ごとにします。 たとえば、エラー ログに次のエラー メッセージが含まれているとします。  
  
```sql
DBCC SHRINKDATABASE for database ID 9 is waiting for the snapshot   
transaction with timestamp 15 and other snapshot transactions linked to   
timestamp 15 or with timestamps older than 109 to finish.  
```  
  
これは、圧縮操作が、109 より古いタイムスタンプが存在する、圧縮操作の完了された最後のトランザクションがスナップショット トランザクションによってブロックされていることを意味します。 示して、 **transaction_sequence_num**、または**first_snapshot_sequence_num**内の列、 [sys.dm_tran_active_snapshot_database_transactions & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-tran-active-snapshot-database-transactions-transact-sql.md)動的管理ビューには、値 15 が含まれています。 どちらの場合、 **transaction_sequence_num**、または**first_snapshot_sequence_num** (109) の圧縮操作が完了した最後のトランザクションより小さいビュー内の列が含まれています、圧縮操作はそれらのトランザクションを完了するまで待機します。
  
問題を解決するのには、次のタスクのいずれかの操作を行います。
-   圧縮操作をブロックしているトランザクションを終了します。  
-   圧縮操作を終了します。 完了済みの作業は保持されます。  
-   何もせず、ブロックしているトランザクションが完了するまで圧縮操作を待機状態にしておきます。  
  
## <a name="permissions"></a>Permissions  
 **sysadmin** 固定サーバー ロールまたは **db_owner** 固定データベース ロールのメンバーシップが必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-shrinking-a-database-and-specifying-a-percentage-of-free-space"></a>A. データベースを圧縮し、空き領域のパーセンテージを指定する  
 次の例では、`UserDB` ユーザー データベース内のデータ ファイルとログ ファイルのサイズを圧縮して、データベースの空き領域が 10% になるようにします。  
  
```sql  
DBCC SHRINKDATABASE (UserDB, 10);  
GO  
```  
  
### <a name="b-truncating-a-database"></a>B. データベースを切り捨てる  
 次の例でのデータとログ ファイルの圧縮、`AdventureWorks`最後に割り当てられたエクステントにサンプル データベース。  
  
```sql  
DBCC SHRINKDATABASE (AdventureWorks2012, TRUNCATEONLY);  
```  
  
## <a name="see-also"></a>参照  
[ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)  
[DBCC &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-transact-sql.md)  
[DBCC SHRINKFILE &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-shrinkfile-transact-sql.md)  
[データベースの圧縮](../../relational-databases/databases/shrink-a-database.md)
  
  

