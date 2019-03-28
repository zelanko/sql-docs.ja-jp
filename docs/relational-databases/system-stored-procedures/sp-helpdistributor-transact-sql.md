---
title: sp_helpdistributor (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helpdistributor_TSQL
- sp_helpdistributor
helpviewer_keywords:
- sp_helpdistributor
ms.assetid: 37b0983e-3b69-4f0f-977e-20efce0a0b97
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: c86f2b8ba6b9cc7223fa9fa16794ee69aa9cf46e
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2019
ms.locfileid: "58533264"
---
# <a name="sphelpdistributor-transact-sql"></a>sp_helpdistributor (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ディストリビューター、ディストリビューション データベース、作業ディレクトリに関する情報を表示し、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エージェント ユーザー アカウント。 このストアド プロシージャは、パブリッシャー、パブリケーション データベースまたは任意のデータベースに対して実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_helpdistributor [ [ @distributor= ] 'distributor' OUTPUT ]  
    [ , [ @distribdb= ] 'distribdb' OUTPUT ]  
    [ , [ @directory= ] 'directory' OUTPUT ]  
    [ , [ @account= ] 'account' OUTPUT ]  
    [ , [ @min_distretention= ] min_distretention OUTPUT ]  
    [ , [ @max_distretention= ] max_distretention OUTPUT ]  
    [ , [ @history_retention= ] history_retention OUTPUT ]  
    [ , [ @history_cleanupagent= ] 'history_cleanupagent' OUTPUT ]  
    [ , [ @distrib_cleanupagent = ] 'distrib_cleanupagent' OUTPUT ]  
    [ , [ @publisher = ] 'publisher' ]   
    [ , [ @local = ] 'local' ]  
    [ , [ @rpcsrvname= ] 'rpcsrvname' OUTPUT ]  
    [ , [ @publisher_type = ] 'publisher_type' OUTPUT ]  
```  
  
## <a name="arguments"></a>引数  
`[ @distributor = ] 'distributor' OUTPUT` ディストリビューターの名前です。 ディストリビューターは**sysname**、既定値は**%**、これは、値だけを結果セットを返します。  
  
`[ @distribdb = ] 'distribdb' OUTPUT` ディストリビューション データベースの名前です。 *distribdb*は**sysname**、既定値は**%**、これは、値だけを結果セットを返します。  
  
`[ @directory = ] 'directory' OUTPUT` 作業ディレクトリです。 *ディレクトリ*は**nvarchar (255)**、既定値は**%**、これは、値だけを結果セットを返します。  
  
`[ @account = ] 'account' OUTPUT` [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows ユーザー アカウント。 *アカウント*は**nvarchar (255)**、既定値は**%**、これは、値だけを結果セットを返します。  
  
`[ @min_distretention = ] _min_distretentionOUTPUT` ディストリビューションの最小保有期間を時間単位です。 *min_distretention*は**int**、既定値は **-1**します。  
  
`[ @max_distretention = ] _max_distretentionOUTPUT` 最大ディストリビューション保有期間の時間です。 *max_distretention*は**int**、既定値は **-1**します。  
  
`[ @history_retention = ] _history_retentionOUTPUT` 時間の履歴の保有期間です。 *history_retention*は**int**、既定値は **-1**します。  
  
`[ @history_cleanupagent = ] 'history_cleanupagent' OUTPUT` 履歴クリーンアップ エージェントの名前です。 *history_cleanupagent*は**nvarchar (100)**、既定値は**%**、これは、値だけを結果セットを返します。  
  
`[ @distrib_cleanupagent = ] 'distrib_cleanupagent' OUTPUT` ディストリビューション クリーンアップ エージェントの名前です。 *distrib_cleanupagent*は**nvarchar (100)**、既定値は**%**、これは、値だけを結果セットを返します。  
  
`[ @publisher = ] 'publisher'` パブリッシャーの名前です。 *パブリッシャー*は**sysname**、既定値は NULL です。  
  
`[ @local = ] 'local'` あるかどうか[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ローカル サーバーの値を取得する必要があります。 *ローカル*は**nvarchar (5)**、既定値は NULL です。  
  
`[ @rpcsrvname = ] 'rpcsrvname' OUTPUT` リモート プロシージャ呼び出しを発行するサーバーの名前です。 *rpcsrvname*は**sysname**、既定値は**%**、これは、値だけを結果セットを返します。  
  
`[ @publisher_type = ] 'publisher_type' OUTPUT` 発行元のパブリッシャーの種類です。 *publisher_type*は**sysname**、既定値は**%**、これは、値だけを結果セットを返します。  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**ディストリビューター**|**sysname**|ディストリビューターの名前。|  
|**ディストリビューション データベース**|**sysname**|ディストリビューション データベースの名前です。|  
|**directory**|**nvarchar (255)**|作業ディレクトリの名前です。|  
|**account**|**nvarchar (255)**|Windows ユーザー アカウントの名前です。|  
|**min 配布 retention**|**int**|ディストリビューションの最小保有期間。|  
|**max 配布 retention**|**int**|最大ディストリビューション保有期間。|  
|**履歴の保有期間**|**int**|履歴の保有期間。|  
|**履歴クリーンアップ エージェント**|**nvarchar(100)**|履歴クリーンアップ エージェントの名前です。|  
|**ディストリビューション クリーンアップ エージェント**|**nvarchar(100)**|ディストリビューション クリーンアップ エージェントの名前です。|  
|**rpc サーバー名**|**sysname**|リモートまたはローカルのディストリビューターの名前です。|  
|**rpc login name**|**sysname**|リモート ディストリビューターに対するリモート プロシージャ呼び出しで使用するログインです。|  
|**パブリッシャーの種類**|**sysname**|パブリッシャーの種類次のいずれかを指定できます。<br /><br /> **MSSQLSERVER**<br /><br /> **ORACLE**<br /><br /> **ORACLE GATEWAY**|  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>コメント  
 **sp_helpdistributor**はあらゆる種類のレプリケーションで使用します。  
  
 実行するときに 1 つまたは複数の出力パラメーターが指定されている場合**sp_helpdistributor**、終了時に値を割り当てられているすべての出力パラメーターを NULL に設定され、結果セットは返されません。 出力パラメーターが指定されていない場合、結果セットが返されます。  
  
## <a name="permissions"></a>アクセス許可  
 次の結果セットの列または出力パラメーターがのメンバーに返される、 **sysadmin** 、パブリッシャーの固定サーバー ロールおよび**db_owner**パブリケーション データベースの固定データベース ロール。  
  
|結果セット列|出力パラメーター|  
|-----------------------|----------------------|  
|account|**@account**|  
|min 配布 retention|**@min_distretention**|  
|max 配布 retention|**@max_distretention**|  
|history retention|**@history_retention**|  
|history cleanup agent|**@history_cleanupagent**|  
|ディストリビューション クリーンアップ エージェント (distribution cleanup agent)|**@distrib_cleanupagent**|  
|rpc ログイン名|なし|  
  
 次の結果セット列は、ディストリビューターのパブリケーション用のパブリケーション アクセス リストのユーザーに返されます。  
  
-   directory  
  
 次の結果セット列は、すべてのユーザーに返されます。  
  
|結果セット列|出力パラメーター|  
|-----------------------|----------------------|  
|ディストリビューター (distributor)|**@distributor**|  
|ディストリビューション データベース (distribution database)|**@distribdb**|  
|rpc server name|**@rpcsrvname**|  
|publisher type|**@publisher_type**|  
  
## <a name="see-also"></a>参照  
 [View and Modify Distributor and Publisher Properties (ディストリビューターとパブリッシャーのプロパティの表示および変更)](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [sp_adddistpublisher &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql.md)   
 [sp_dropdistpublisher &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropdistpublisher-transact-sql.md)  
  
  
