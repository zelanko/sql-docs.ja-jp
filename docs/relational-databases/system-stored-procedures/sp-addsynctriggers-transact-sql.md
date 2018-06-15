---
title: sp_addsynctriggers (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_addsynctriggers_TSQL
- sp_addsynctriggers
helpviewer_keywords:
- sp_addsynctriggers
ms.assetid: e37d0c3b-19bf-4719-9535-96ba361372b3
caps.latest.revision: 29
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 711126c199480bd1d8ef836b9b587f51db8e4552
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32992199"
---
# <a name="spaddsynctriggers-transact-sql"></a>sp_addsynctriggers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  すべての種類の更新可能なサブスクリプション (即時更新、キュー更新、およびフェールオーバーとしてキュー更新を使用する即時更新) と共に使用できるトリガーを、サブスクライバー側で作成します。 このストアド プロシージャは、サブスクライバー側でサブスクリプション データベースについて実行されます。  
  
> [!IMPORTANT]  
>  [Sp_script_synctran_commands](../../relational-databases/system-stored-procedures/sp-script-synctran-commands-transact-sql.md)の代わりにプロシージャを使用する必要があります**sp_addsynctrigger**です。 [sp_script_synctran_commands](../../relational-databases/system-stored-procedures/sp-script-synctran-commands-transact-sql.md)を含むスクリプトを生成、 **sp_addsynctrigger**呼び出しです。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_addsynctriggers [ @sub_table = ] 'sub_table'  
        , [ @sub_table_owner = ] 'sub_table_owner'  
        , [ @publisher = ] 'publisher'  
        , [ @publisher_db = ] 'publisher_db'  
        , [ @publication = ] 'publication'   
        , [ @ins_proc = ] 'ins_proc'   
        , [ @upd_proc = ] 'upd_proc'   
        , [ @del_proc = ] 'del_proc'   
        , [ @cftproc = ] 'cftproc'  
        , [ @proc_owner = ] 'proc_owner'  
    [ , [ @identity_col = ] 'identity_col' ]  
    [ , [ @ts_col = ] 'timestamp_col' ]  
    [ , [ @filter_clause = ] 'filter_clause' ]   
        , [ @primary_key_bitmap = ] 'primary_key_bitmap'  
    [ , [ @identity_support = ] identity_support ]  
    [ , [ @independent_agent = ] independent_agent ]  
        , [ @distributor = ] 'distributor'   
    [ , [ @pubversion = ] pubversion  
```  
  
## <a name="arguments"></a>引数  
 [  **@sub_table=**] **'***sub_table***'**  
 サブスクライバー テーブルの名前を指定します。 *sub_table*は**sysname**、既定値はありません。  
  
 [  **@sub_table_owner=**] **'***sub_table_owner***'**  
 サブスクライバー テーブルの所有者の名前を指定します。 *sub_table_owner*は**sysname**、既定値はありません。  
  
 [ **@publisher=**] **'***publisher***'**  
 パブリッシャー サーバーの名前を指定します。 *パブリッシャー*は**sysname**、既定値はありません。  
  
 [ **@publisher_db=**] **'***publisher_db***'**  
 パブリッシャー データベースの名前です。 *publisher_db*は**sysname**、既定値はありません。 NULL の場合は、現在のデータベースが使用されます。  
  
 [ **@publication=**] **'***publication***'**  
 パブリケーションの名前です。 *パブリケーション*は**sysname**、既定値はありません。  
  
 [  **@ins_proc=**] **'***ins_proc***'**  
 パブリッシャー側での同期トランザクション挿入をサポートするストアド プロシージャの名前を指定します。 *ins_proc*は**sysname**、既定値はありません。  
  
 [  **@upd_proc=**] **'***upd_proc***'**  
 パブリッシャー側での同期トランザクション更新をサポートするストアド プロシージャの名前を指定します。 *ins_proc*は**sysname**、既定値はありません。  
  
 [  **@del_proc=**] **'***del_proc***'**  
 パブリッシャー側での同期トランザクション削除をサポートするストアド プロシージャの名前を指定します。 *ins_proc*は**sysname**、既定値はありません。  
  
 [  **@cftproc =** ] **'***cftproc***'**  
 キュー更新が許可されているパブリケーションで使用される自動生成プロシージャの名前を指定します。 *cftproc*は**sysname**、既定値はありません。 即時更新が許可されているパブリケーションの場合、この値は NULL です。 このパラメーターは、キュー更新 (キュー更新、およびフェールオーバーとしてキュー更新を使用する即時更新) が許可されているパブリケーションに適用されます。  
  
 [  **@proc_owner =** ] **'***proc_owner***'**  
 更新パブリケーション (キュー更新パブリケーションおよび即時更新パブリケーション) 用のすべての自動生成ストアド プロシージャの作成時に使用された、パブリッシャーのユーザー アカウントを指定します。 *proc_owner*は**sysname**既定値はありません。  
  
 [  **@identity_col=**] **'***identity_col***'**  
 パブリッシャーでの ID 列の名前を指定します。 *identity_col*は**sysname**、既定値は NULL です。  
  
 [  **@ts_col=**] **'***timestamp_col***'**  
 名前を指定、**タイムスタンプ**パブリッシャーの列です。 *timestamp_col*は**sysname**、既定値は NULL です。  
  
 [  **@filter_clause=**] **'***filter_clause***'**  
 行フィルターを定義する制限句 (WHERE) を指定します。 制限句を入力する場合は、WHERE キーワードを省略します。 *filter_clause*は**nvarchar (4000)**、既定値は NULL です。  
  
 [  **@primary_key_bitmap =**] **'***primary_key_bitmap***'**  
 テーブル内の主キー列のビットマップを指定します。 *primary_key_bitmap*は**varbinary (4000)**、既定値はありません。  
  
 [  **@identity_support =** ] *identity_support*  
 キュー更新を使用するときの自動 ID 範囲処理を有効または無効にします。 *identity_support*は、**ビット**、既定値は**0**します。 **0**の id がないことを意味の範囲のサポート、 **1**自動 id 範囲処理を有効にします。  
  
 [  **@independent_agent =** ] *independent_agent*  
 このパブリケーションに対して単独のディストリビューション エージェント (独立エージェント) があるか、パブリケーション データベースとサブスクリプション データベースの 1 つのペアにつき 1 つのディストリビューション エージェント (共有エージェント) があるかを示します。 この値には、パブリッシャーで定義されているパブリケーションの independent_agent プロパティの値が反映されます。 *independent_agent*は bit で、既定値は**0**します。 場合**0**エージェントが共有エージェントです。 場合**1**エージェントが独立したエージェントです。  
  
 [  **@distributor =** ] **'***ディストリビューター***'**  
 ディストリビューターの名前です。 *ディストリビューター*は**sysname**、既定値はありません。  
  
 [ **@pubversion**=] *pubversion*  
 パブリッシャーのバージョンを指定します。 *pubversion*は**int**、既定値は 1 です。 **1**パブリッシャーのバージョンであることを意味[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] Service Pack 2 以前です。**2**パブリッシャーであることを意味[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]Service Pack 3 (SP3) 以降。 *pubversion*に明示的に設定する必要があります**2**パブリッシャーのバージョンがいつ[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]SP3 またはそれ以降。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_addsynctriggers**は、ディストリビューション エージェントによってサブスクリプションの初期化の一部として使用します。 このストアド プロシージャは、ユーザーが頻繁に実行するものではありません。ただし、同期なしサブスクリプションを手動で設定する場合に利用できるストアド プロシージャです。  
  
## <a name="permissions"></a>権限  
 メンバーにのみ、 **sysadmin**固定サーバー ロールまたは**db_owner**固定データベース ロールが実行できる**sp_addsynctriggers**です。  
  
## <a name="see-also"></a>参照  
 [Updatable Subscriptions for Transactional Replication](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)   
 [sp_script_synctran_commands &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-script-synctran-commands-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
