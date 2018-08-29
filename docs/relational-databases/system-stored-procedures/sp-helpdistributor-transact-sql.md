---
title: sp_helpdistributor (TRANSACT-SQL) |Microsoft Docs
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
- sp_helpdistributor_TSQL
- sp_helpdistributor
helpviewer_keywords:
- sp_helpdistributor
ms.assetid: 37b0983e-3b69-4f0f-977e-20efce0a0b97
caps.latest.revision: 32
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d0b7e22c946626c10d08781e00886083d0991d01
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43022581"
---
# <a name="sphelpdistributor-transact-sql"></a>sp_helpdistributor (Transact-SQL)
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
 [  **@distributor=**] **'***ディストリビューター***'** 出力  
 ディストリビューターの名前です。 ディストリビューターは**sysname**、既定値は**%**、これは、値だけを結果セットを返します。  
  
 [  **@distribdb=**] **'***distribdb***'** 出力  
 ディストリビューション データベースの名前を指定します。 *distribdb*は**sysname**、既定値は**%**、これは、値だけを結果セットを返します。  
  
 [  **@directory=**] **'***ディレクトリ***'** 出力  
 作業ディレクトリです。 *ディレクトリ*は**nvarchar (255)**、既定値は**%**、これは、値だけを結果セットを返します。  
  
 [  **@account=**] **'***アカウント***' 出力**  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows ユーザー アカウントです。 *アカウント*は**nvarchar (255)**、既定値は**%**、これは、値だけを結果セットを返します。  
  
 [  **@min_distretention=**] *min_distretention * * * 出力**  
 ディストリビューションの最小保有期間を時間単位で示します。 *min_distretention*は**int**、既定値は **-1**します。  
  
 [  **@max_distretention=**] *max_distretention * * * 出力**  
 ディストリビューションの最大保有期間を時間単位で示します。 *max_distretention*は**int**、既定値は **-1**します。  
  
 [  **@history_retention=**] *history_retention * * * 出力**  
 履歴の保有期間を時間単位で示します。 *history_retention*は**int**、既定値は **-1**します。  
  
 [  **@history_cleanupagent=**] **'***history_cleanupagent***' 出力**  
 履歴クリーンアップ エージェントの名前です。 *history_cleanupagent*は**nvarchar (100)**、既定値は**%**、これは、値だけを結果セットを返します。  
  
 [  **@distrib_cleanupagent =**] **'***distrib_cleanupagent***' 出力**  
 ディストリビューション クリーンアップ エージェントの名前です。 *distrib_cleanupagent*は**nvarchar (100)**、既定値は**%**、これは、値だけを結果セットを返します。  
  
 [ **@publisher=**] **'***publisher***'**  
 パブリッシャーの名前です。 *パブリッシャー*は**sysname**、既定値は NULL です。  
  
 [  **@local=**] **'***ローカル***'**  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] がローカル サーバーの値を取得するかどうかを示します。 *ローカル*は**nvarchar (5)**、既定値は NULL です。  
  
 [  **@rpcsrvname=**] **'***rpcsrvname***' 出力**  
 リモート プロシージャ コールを実行するサーバーの名前です。 *rpcsrvname*は**sysname**、既定値は**%**、これは、値だけを結果セットを返します。  
  
 [ **@publisher_type**=] **'***publisher_type***' 出力**  
 パブリッシャーの種類です。 *publisher_type*は**sysname**、既定値は**%**、これは、値だけを結果セットを返します。  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**ディストリビューター**|**sysname**|ディストリビューターの名前。|  
|**ディストリビューション データベース**|**sysname**|ディストリビューション データベースの名前です。|  
|**ディレクトリ**|**nvarchar (255)**|作業ディレクトリの名前です。|  
|**アカウント**|**nvarchar (255)**|Windows ユーザー アカウントの名前です。|  
|**min 配布 retention**|**int**|ディストリビューションの最短保持期間です。|  
|**max 配布 retention**|**int**|ディストリビューションの最長保持期間です。|  
|**履歴の保有期間**|**int**|履歴の保有期間です。|  
|**履歴クリーンアップ エージェント**|**nvarchar(100)**|履歴後処理エージェントの名前。|  
|**ディストリビューション クリーンアップ エージェント**|**nvarchar(100)**|ディストリビューション後処理エージェントの名前。|  
|**rpc サーバー名**|**sysname**|リモート ディストリビューターまたはローカル ディストリビューターの名前です。|  
|**rpc ログイン名**|**sysname**|リモート ディストリビューターに対するリモート プロシージャ呼び出しで使用するログインです。|  
|**パブリッシャーの種類**|**sysname**|パブリッシャーの種類次のいずれかを指定できます。<br /><br /> **MSSQLSERVER**<br /><br /> **ORACLE**<br /><br /> **ORACLE GATEWAY**|  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>コメント  
 **sp_helpdistributor**はあらゆる種類のレプリケーションで使用します。  
  
 実行するときに 1 つまたは複数の出力パラメーターが指定されている場合**sp_helpdistributor**、終了時に値を割り当てられているすべての出力パラメーターを NULL に設定され、結果セットは返されません。 出力パラメーターを指定しない場合、結果セットが返されます。  
  
## <a name="permissions"></a>アクセス許可  
 次の結果セットの列または出力パラメーターがのメンバーに返される、 **sysadmin** 、パブリッシャーの固定サーバー ロールおよび**db_owner**パブリケーション データベースの固定データベース ロール。  
  
|結果セット列|出力パラメーター|  
|-----------------------|----------------------|  
|account|**@account**|  
|min distrib retention|**@min_distretention**|  
|max distrib retention|**@max_distretention**|  
|history retention|**@history_retention**|  
|history cleanup agent|**@history_cleanupagent**|  
|ディストリビューション クリーンアップ エージェント (distribution cleanup agent)|**@distrib_cleanupagent**|  
|rpc login name|なし|  
  
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
  
  
