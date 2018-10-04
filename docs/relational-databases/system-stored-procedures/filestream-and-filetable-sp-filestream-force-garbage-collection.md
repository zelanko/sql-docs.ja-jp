---
title: sp_filestream_force_garbage_collection (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 07/22/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_filestream_force_garbage_collection
- sp_filestream_force_garbage_collection_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- FILESTREAM [SQL Server]
- sp_filestream_force_garbage_collection
ms.assetid: 9d1efde6-8fa4-42ac-80e5-37456ffebd0b
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 350c007c8a0153f2dfd0f84d596110b3dea29500
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47733420"
---
# <a name="spfilestreamforcegarbagecollection-transact-sql"></a>sp_filestream_force_garbage_collection (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  FILESTREAM ガベージ コレクターを強制的に実行して、不要な FILESTREAM ファイルを削除します。  
  
 FILESTREAM コンテナーは、ガベージ コレクターによってコンテナー内の削除済みファイルがすべてクリーンアップされるまで削除できません。 FILESTREAM ガベージ コレクターは自動的に実行されます。 ただし、ガベージ コレクターの前にコンテナーを削除するが実行する必要がある場合は、sp_filestream_force_garbage_collection を使用するには、ガベージ コレクターを手動で実行します。  
  
  
## <a name="syntax"></a>構文  
  
```  
sp_filestream_force_garbage_collection  
    [ @dbname = ]  'database_name',  
    [ @filename = ] 'logical_file_name' ]  
```  
  
## <a name="arguments"></a>引数  
 **@dbname** = *database_name***'**  
 ガベージ コレクターを実行するデータベースの名前を示します。  
  
> [!NOTE]  
>  *dbname*は**sysname**します。 指定しない場合、指定すると、現在のデータベースが想定されます。  
  
 **@filename** = *logical_file_name*  
 ガベージ コレクターを実行する FILESTREAM コンテナーの論理名を指定します。 **@filename** 省略可能です。 論理ファイル名が指定されていない場合、ガベージ コレクターは、指定されたデータベース内のすべての FILESTREAM コンテナーをクリーンアップします。  
  
## <a name="return-code-values"></a>リターン コードの値  
  
|||  
|-|-|  
|値|Description|  
|0|操作に成功しました。|  
|1|操作に失敗しました|  
  
## <a name="result-sets"></a>結果セット  
  
|値|説明|  
|-----------|-----------------|  
|*file_name*|FILESTREAM コンテナー名を示します。|  
|*num_collected_items*|このコンテナー内の、ガベージ コレクションが実行 (削除) された FILESTREAM アイテム (ファイルまたはディレクトリ) の数を示します。|  
|*num_marked_for_collection_items*|このコンテナー内の、ガベージ コレクションの対象としてマークされた FILESTREAM アイテム (ファイルまたはディレクトリ) の数を示します。 これらの項目は、まだ削除されていないが、削除、ガベージ コレクション フェーズを次の対象となる場合があります。|  
|*num_unprocessed_items*|この FILESTREAM コンテナー内の、ガベージ コレクションで処理されなかった対象となる FILESTREAM アイテム (ファイルまたはディレクトリ) の数を示します。 アイテムは次のようなさまざまな理由で処理されないことがあります。<br /><br /> ログ バックアップまたはチェックポイントが作成されていないため、ファイルにピンを設定する必要がある。<br /><br /> ファイルが完全復旧モデルまたは一括ログ復旧モデルに含まれている。<br /><br /> 実行時間の長いアクティブなトランザクションが存在している。<br /><br /> レプリケーション ログ リーダー ジョブが実行されません。 ホワイト ペーパーを参照してください。 [SQL Server 2008 の FILESTREAM ストレージ](http://go.microsoft.com/fwlink/?LinkId=209156)詳細についてはします。|  
|*last_collected_xact_seqno*|指定した FILESTREAM コンテナー内の、ガベージ コレクションが実行されたファイルに対応する最後のログ シーケンス番号 (LSN) を返します。|  
  
## <a name="remarks"></a>コメント  
 要求されたデータベース (および FILESTREAM コンテナー) で FILESTREAM ガベージ コレクターのタスクを完了まで明示的に実行します。 不要になったファイルは、ガベージ コレクション プロセスによって削除されます。 この操作の完了に要する時間は、そのデータベースまたはコンテナー内の FILESTREAM データのサイズと、FILESTREAM データに対して最近実行された DML 操作の量によって異なります。 この操作はデータベースがオンラインのときに実行できますが、ガベージ コレクション プロセスによってさまざまな I/O 操作が行われるため、実行中にデータベースのパフォーマンスに影響を与える可能性があります。  
  
> [!NOTE]  
>  この操作は必要な場合と通常業務時間外にのみ実行することをお勧めします。  
  
異なるコンテナーやデータベースに対してのみ、このストアド プロシージャの呼び出しを複数同時に実行できます。  

2 段階の操作のためには、基になる Filestream ファイルを実際に削除するには、2 回ストアド プロシージャを実行する必要があります。  

ガベージ コレクション (GC) は、ログの切り捨てに依存します。 そのため、ファイルは完全復旧モデルを使用してデータベースで最近削除された場合は GC ed、トランザクション ログの一部のログ バックアップが取得され、ログ部分が非アクティブとマークした後のみです。 単純復旧モデルを使用して、データベースに対するログの切り捨ての発生後に、`CHECKPOINT`がデータベースに対して発行されています。  


## <a name="permissions"></a>アクセス許可  
 db_owner データベース ロールのメンバーシップが必要です。  
  
## <a name="examples"></a>使用例  
 次の例で FILESTREAM コンテナーに対してガベージ コレクターの実行、`FSDB`データベース。  
  
### <a name="a-specifying-no-container"></a>A. コンテナーを指定しない  
  
```sql  
USE FSDB;  
GO  
EXEC sp_filestream_force_garbage_collection @dbname = N'FSDB';  
```  
  
### <a name="b-specifying-a-container"></a>B. コンテナーを指定する  
  
```sql  
USE FSDB;  
GO  
EXEC sp_filestream_force_garbage_collection @dbname = N'FSDB',
    @filename = N'FSContainer';  
```  
  
## <a name="see-also"></a>参照  
[Filestream](../../relational-databases/blob/filestream-sql-server.md)
<br>[Filetable](../../relational-databases/blob/filetables-sql-server.md)
<br>[Filestream および FileTable の動的管理ビュー (Transact-SQL)](../system-dynamic-management-views/filestream-and-filetable-dynamic-management-views-transact-sql.md)
<br>[Filestream および FileTable のカタログ ビュー (Transact-SQL)](../system-catalog-views/filestream-and-filetable-catalog-views-transact-sql.md)
<br>[sp_kill_filestream_non_transacted_handles (TRANSACT-SQL)](filestream-and-filetable-sp-kill-filestream-non-transacted-handles.md)
  
  
