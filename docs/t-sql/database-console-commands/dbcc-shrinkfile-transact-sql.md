---
title: DBCC SHRINKFILE (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 11/14/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- SHRINKFILE
- DBCC_SHRINKFILE_TSQL
- DBCC SHRINKFILE
- SHRINKFILE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- data shrinking [SQL Server]
- TRUNCATEONLY option
- shrinking files
- NOTRUNCATE option
- shrinking databases
- decreasing database size
- file shrinking [SQL Server]
- database shrinking [SQL Server]
- logs [SQL Server], shrinking
- reducing database size
- DBCC SHRINKFILE statement
ms.assetid: e02b2318-bee9-4d84-a61f-2fddcf268c9f
caps.latest.revision: 87
author: uc-msft
ms.author: umajay
manager: craigg
ms.openlocfilehash: a771f30b82a81fa05ea65409bce9a132cbb42dad
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38040040"
---
# <a name="dbcc-shrinkfile-transact-sql"></a>DBCC SHRINKFILE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

現在のデータベース用の、指定したデータ ファイルまたはログ ファイルのサイズを圧縮します。または、指定したファイルのデータを同じファイル グループ内の別のファイルに移動してファイルを空にし、ファイルをデータベースから削除できるようにします。 ファイルを圧縮すると、ファイルの作成時に指定したサイズよりも小さなサイズにできます。 実行すると、最小ファイル サイズは新しい値にリセットされます。
  
![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>構文  
  
```sql
  
DBCC SHRINKFILE   
(  
    { file_name | file_id }   
    { [ , EMPTYFILE ]   
    | [ [ , target_size ] [ , { NOTRUNCATE | TRUNCATEONLY } ] ]  
    }  
)  
[ WITH NO_INFOMSGS ]  
```  
  
## <a name="arguments"></a>引数  
*file_name*  
圧縮するファイルの論理名を指定します。
  
*file_id*  
圧縮するファイルの識別 (ID) 番号を指定します。 ファイル ID を取得するには、システム関数 [FILE_IDEX](../../t-sql/functions/file-idex-transact-sql.md) を使用するか、現在のデータベースで [sys.database_files](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md) カタログ ビューに対してクエリを実行します。
  
*target_size*  
ファイルのサイズを MB 単位で表す整数値を指定します。 この値を指定しない場合、DBCC SHRINKFILE では既定のファイル サイズまでサイズが圧縮されます。 既定のサイズは、ファイル作成時に指定されたサイズです。
  
> [!NOTE]  
>  DBCC SHRINKFILE *target_size* を使用して、空のファイルの既定のサイズを小さくすることができます。 たとえば、5 MB のファイルを作成してから、ファイルがまだ空のうちに 3 MB に圧縮した場合、既定のファイル サイズは 3 MB に設定されます。 これは、データが含まれたことがない空のファイルにのみ該当します。  
  
このオプションは、FILESTREAM ファイル グループ コンテナーではサポートされていません。  
*target_size* を指定した場合、DBCC SHRINKFILE では、指定されたサイズまでファイルの圧縮が試行されます。 解放されたファイル内の使用ページは、保持されるファイル部分の空き領域に移されます。 たとえば、10 MB のデータ ファイルの場合、*target_size* を 8 にして DBCC SHRINKFILE 操作を実行すると、ファイルの末尾 2 MB にあるすべての使用ページがファイルの先頭 8 MB にある未割り当てのページに再割り当てされます。 DBCC SHRINKFILE では、ファイル内に格納されているデータのサイズ以下に、ファイルを圧縮することはできません。 たとえば、10 MB のデータ ファイルのうち 7 MB が使用されている場合、*target_size* を 6 にして DBCC SHRINKFILE ステートメントを実行しても、ファイルは 7 MB にまでしか圧縮できず、6 MB にはなりません。
  
EMPTYFILE  
指定したファイルから、**同じファイル グループ**内の他のファイルにすべてのデータを移動します。 つまり、EmptyFile は、指定したファイルから、同じファイル グループ内の他のファイルにデータを移動します。 ファイルが読み取り専用としてマークされていなくても、Emptyfile により、このファイルには新しいデータが追加されなくなります。このファイルは [ALTER DATABASE](../../t-sql/statements/alter-database-transact-sql.md) ステートメントを使用して削除することができます。 [ALTER DATABASE](../../t-sql/statements/alter-database-transact-sql.md) ステートメントを使用してファイル サイズが変更されると、読み取り専用フラグがリセットされ、データを追加することができます。

FILESTREAM ファイル グループ コンテナーでは、FILESTREAM ガベージ コレクターが実行され、EMPTYFILE によって他のコンテナーにコピーされた不要なすべてのファイル グループ コンテナー ファイルが削除された後でなければ、ALTER DATABASE を使用してファイルを削除できません。 詳細については、「[sp_filestream_force_garbage_collection &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/filestream-and-filetable-sp-filestream-force-garbage-collection.md)」を参照してください。
  
> [!NOTE]  
>  FILESTREAM コンテナーの削除については、「[ALTER DATABASE の File および Filegroup オプション &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-file-and-filegroup-options.md)」の対応するセクションを参照してください。  
  
NOTRUNCATE  
データ ファイル末尾の割り当て済みページをファイル先頭の未割り当てページに移動します。必要に応じて *target_percent* を指定することもできます。 ファイル末尾の空き領域はオペレーティング システムに返されず、ファイルの物理サイズは変わりません。 したがって、NOTRUNCATE を指定した場合は、ファイルが圧縮されていないように見えます。
NOTRUNCATE はデータ ファイルにのみ適用され、 ログ ファイルは影響を受けません。   このオプションは、FILESTREAM ファイル グループ コンテナーではサポートされていません。
  
TRUNCATEONLY  
ファイル末尾のすべての空き領域をオペレーティング システムに渡します。ただし、ファイル内でのページの移動は行われません。 データ ファイルは、最後に割り当てられたエクステントを限度として圧縮されます。
*target_size* は、TRUNCATEONLY と共に指定した場合、無視されます。  
TRUNCATEONLY オプションは、ログ内で情報を移動させませんが、非アクティブな VLF をログ ファイルの末尾から削除します。 このオプションは、FILESTREAM ファイル グループ コンテナーではサポートされていません。
  
WITH NO_INFOMSGS  
すべての情報メッセージを表示しないようにします。
  
## <a name="result-sets"></a>結果セット  
次の表では、結果セットの列について説明します。
  
|列名|[説明]|  
|---|---|
|**DbId**|[!INCLUDE[ssDE](../../includes/ssde-md.md)]で圧縮が試行されたファイルのデータベース識別番号。|  
|**FileId**|[!INCLUDE[ssDE](../../includes/ssde-md.md)]で圧縮が試行されたファイルのファイル識別番号。|  
|**CurrentSize**|ファイルが現在占有する 8 KB ページの数。|  
|**MinimumSize**|ファイルが占有できる 8 KB ページの最小数。 この値は、ファイルの最小サイズまたは最初に作成されたサイズと一致します。|  
|**UsedPages**|ファイルが現在使用している 8 KB ページの数。|  
|**EstimatedPages**|[!INCLUDE[ssDE](../../includes/ssde-md.md)]で推定されるファイル圧縮後の 8 KB ページの数。|  
  
## <a name="remarks"></a>Remarks  
DBCC SHRINKFILE は現在のデータベース内のファイルに適用されます。 現在のデータベースを変更する方法の詳細については、「[USE &#40;Transact-SQL&#41;](../../t-sql/language-elements/use-transact-sql.md)」を参照してください。
  
DBCC SHRINKFILE 操作は、プロセスのどの時点でも中断でき、中断時に完了していた作業は保持されます。 EMPTYFILE パラメーターがファイルで使用され、操作がキャンセルされた場合、さらにデータが追加されないように、ファイルがマークされることはありません。
  
DBCC SHRINKFILE 操作が失敗すると、エラーが発生します。
  
 圧縮されるデータベースは、シングル ユーザー モードになっている必要はありません。ファイルの圧縮中も、他のユーザーはそのデータベースで作業することができます。 システム データベースを圧縮するために、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスをシングル ユーザー モードで実行する必要はありません。  
  
## <a name="shrinking-a-log-file"></a>ログ ファイルの圧縮  
ログ ファイルの場合、[!INCLUDE[ssDE](../../includes/ssde-md.md)] では *target_size* を使用してログ全体の目標サイズが計算されるため、*target_size* は圧縮処理後のログ内の空き領域サイズになります。 計算の後、ログ全体の目標サイズは各ログ ファイルの目標サイズに変換されます。 DBCC SHRINKFILE では、各物理ログ ファイルの目標サイズへの圧縮がすぐに試行されます。 ただし、論理ログの一部が、目標サイズを超える仮想ログ内に存在する場合は、[!INCLUDE[ssDE](../../includes/ssde-md.md)]により、できるだけ多くの領域が解放され、情報メッセージが発行されます。 このメッセージには、ファイルの末尾で仮想ログから論理ログを移動するために行う必要のある操作が説明されています。 この操作を実行した後、DBCC SHRINKFILE を使って、残りの領域を解放できます。
  
ログ ファイルは仮想ログ ファイルの境界を越えて圧縮できないため、ログ ファイルを仮想ログ ファイルのサイズより小さく圧縮することはできません。これはログ ファイルが使用されていない場合でも同じです。 [!INCLUDE[ssDE](../../includes/ssde-md.md)]では、ログ ファイルの作成時または拡張時に仮想ログ ファイルのサイズが動的に選択されます。
  
## <a name="best-practices"></a>ベスト プラクティス  
ファイルを圧縮する場合は次のことを考慮してください。
-   圧縮操作は、テーブルの切り捨てやテーブルの削除操作など、大きな未使用領域を生成する操作の後に実行すると最も効果的です。  
-   ほとんどのデータベースでは、毎日の定期的操作で使用するための空き領域が必要です。 データベースを何度圧縮しても、データベースのサイズが大きくなってしまう場合は、通常の操作にそれだけの領域が必要であることを示しています。 このような場合、繰り返しデータベースを圧縮することは無意味です。  
-   圧縮操作では、データベース内のインデックスの断片化状態は保持されず、一般に、断片化の程度が大きくなります。 この理由からも、データベースを繰り返し圧縮することはお勧めできません。  
-   複数のファイルを同じデータベース内に、同時ではなく、順番に圧縮します。 システム テーブルでの競合が原因で、ブロックによる遅延が発生する可能性があります。  
  
## <a name="troubleshooting"></a>トラブルシューティング  
ここでは、DBCC SHRINKFILE コマンドを実行する場合に発生する可能性のある問題を診断し修正する方法について説明します。
  
### <a name="the-file-does-not-shrink"></a>ファイルが圧縮されない  
圧縮操作がエラーなしで実行されても、ファイルのサイズが変わらないように見える場合は、次のいずれかの操作を実行して、ファイルに削除可能な十分な空き領域があるかどうかを確認してください。
- 次のクエリを実行します。  
  
```sql
SELECT name ,size/128.0 - CAST(FILEPROPERTY(name, 'SpaceUsed') AS int)/128.0 AS AvailableSpaceInMB
FROM sys.database_files;
```

-   [DBCC SQLPERF](../../t-sql/database-console-commands/dbcc-sqlperf-transact-sql.md) コマンドを実行し、トランザクション ログで使用されている領域を返します。  
使用できる空き領域が不十分な場合、圧縮操作ではこれ以上ファイル サイズを減らすことはできません。
  
通常、圧縮されていないように見えるのはログ ファイルです。 これは多くの場合、ログ ファイルが切り捨てられなかった結果として起こります。 ログを切り捨てるには、データベース復旧モデルを SIMPLE に設定するか、ログをバックアップして再度 DBCC SHRINKFILE 操作を実行します。
  
### <a name="the-shrink-operation-is-blocked"></a>圧縮操作がブロックされる  
[行のバージョン管理に基づく分離レベル](../../t-sql/statements/set-transaction-isolation-level-transact-sql.md)で実行されているトランザクションによって圧縮操作がブロックされる可能性があります。 たとえば、DBCC SHRINK DATABASE 操作を実行するときに、行のバージョン管理に基づく分離レベルでの大規模な削除操作が進行中の場合、圧縮操作は削除処理が完了してから実行され、ファイルが圧縮されます。 この場合、DBCC SHRINKFILE および DBCC SHRINKDATABASE 操作によって、最初の 1 時間は 5 分ごと、それ以降は 1 時間ごとに、情報メッセージ (SHRINKDATABASE は 5202、SHRINKFILE は 5203) が SQL Server エラー ログに出力されます。 たとえば、エラー ログに次のエラー メッセージが含まれている場合は、このエラーが発生します。
  
```sql
DBCC SHRINKFILE for file ID 1 is waiting for the snapshot   
transaction with timestamp 15 and other snapshot transactions linked to   
timestamp 15 or with timestamps older than 109 to finish.  
```  
  
これは、圧縮操作が、109 より古いタイムスタンプが存在する、圧縮操作の完了された最後のトランザクションがスナップショット トランザクションによってブロックされていることを意味します。 また、[sys.dm_tran_active_snapshot_database_transactions](../../relational-databases/system-dynamic-management-views/sys-dm-tran-active-snapshot-database-transactions-transact-sql.md) 動的管理ビューの **transaction_sequence_num** 列または **first_snapshot_sequence_num** 列に、値 15 が含まれることも示しています。 このビューの **transaction_sequence_num** 列または **first_snapshot_sequence_num** 列のいずれかに、圧縮操作により完了した最後のトランザクション (109) より低い番号が含まれている場合は、それらのトランザクションが終了するまで圧縮操作は待機状態となります。
  
この問題を解決するには、次のいずれかの作業を実行します。
-   圧縮操作をブロックしているトランザクションを終了します。
-   圧縮操作を終了します。 圧縮操作を終了した場合、完了済みの作業は保持されます。  
-   何もせず、ブロックしているトランザクションが完了するまで圧縮操作を待機状態にしておきます。  
  
## <a name="permissions"></a>アクセス許可  
**sysadmin** 固定サーバー ロールまたは **db_owner** 固定データベース ロールのメンバーシップが必要です。
  
## <a name="examples"></a>使用例  
  
### <a name="a-shrinking-a-data-file-to-a-specified-target-size"></a>A. 指定した目標サイズにデータ ファイルを圧縮する  
次の例では、`UserDB` ユーザー データベース内の `DataFile1` というデータ ファイルのサイズを 7 MB に圧縮します。
  
```sql  
USE UserDB;  
GO  
DBCC SHRINKFILE (DataFile1, 7);  
GO  
```  
  
### <a name="b-shrinking-a-log-file-to-a-specified-target-size"></a>B. 指定した目標サイズにログ ファイルを圧縮する  
次の例では、`AdventureWorks` データベース内のログ ファイルを 1 MB に圧縮します。 DBCC SHRINKFILE コマンドを使用してファイルを圧縮するため、まずデータベース復旧モデルを SIMPLE に設定してファイルを切り捨てます。
  
```sql  
USE AdventureWorks2012;  
GO  
-- Truncate the log by changing the database recovery model to SIMPLE.  
ALTER DATABASE AdventureWorks2012  
SET RECOVERY SIMPLE;  
GO  
-- Shrink the truncated log file to 1 MB.  
DBCC SHRINKFILE (AdventureWorks2012_Log, 1);  
GO  
-- Reset the database recovery model.  
ALTER DATABASE AdventureWorks2012  
SET RECOVERY FULL;  
GO  
```  
  
### <a name="c-truncating-a-data-file"></a>C. データ ファイルを切り捨てる  
次の例では、`AdventureWorks` データベース内のプライマリ データ ファイルを切り捨てます。 `sys.database_files` カタログ ビューに対してクエリを実行し、データ ファイルの `file_id` を取得します。
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT file_id, name  
FROM sys.database_files;  
GO  
DBCC SHRINKFILE (1, TRUNCATEONLY);  
```  
  
### <a name="d-emptying-a-file"></a>D. ファイルを空にする  
次の例では、データベースから削除できるようファイルを空にします。 この例では、最初にデータ ファイルを作成します。ファイルにはデータが含まれていることが前提となっています。
  
```sql  
USE AdventureWorks2012;  
GO  
-- Create a data file and assume it contains data.  
ALTER DATABASE AdventureWorks2012   
ADD FILE (  
    NAME = Test1data,  
    FILENAME = 'C:\t1data.ndf',  
    SIZE = 5MB  
    );  
GO  
-- Empty the data file.  
DBCC SHRINKFILE (Test1data, EMPTYFILE);  
GO  
-- Remove the data file from the database.  
ALTER DATABASE AdventureWorks2012  
REMOVE FILE Test1data;  
GO  
```  
  
## <a name="see-also"></a>参照  
[ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)  
[DBCC &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-transact-sql.md)  
[DBCC SHRINKDATABASE &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-shrinkdatabase-transact-sql.md)  
[FILE_ID &#40;Transact-SQL&#41;](../../t-sql/functions/file-id-transact-sql.md)  
[sys.database_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)  
[ファイルの圧縮](../../relational-databases/databases/shrink-a-file.md)
  
  
