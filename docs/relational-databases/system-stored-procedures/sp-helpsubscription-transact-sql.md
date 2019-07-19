---
title: sp_helpsubscription (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helpsubscription_TSQL
- sp_helpsubscription
helpviewer_keywords:
- sp_helpsubscription
ms.assetid: ff96bcbf-e2b9-4da8-8515-d80d4ce86c16
author: stevestein
ms.author: sstein
ms.openlocfilehash: dd33fc16d399cc6d628eb4b3e80af98efca4ecc8
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68048351"
---
# <a name="sphelpsubscription-transact-sql"></a>sp_helpsubscription (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  特定のパブリケーション、アーティクル、サブスクライバー、またはセットのサブスクリプションに関連付けられているサブスクリプション情報を一覧表示します。 このストアド プロシージャは、パブリッシャー、パブリケーション データベースに対して実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_helpsubscription [ [ @publication = ] 'publication' ]   
    [ , [ @article = ] 'article' ]  
    [ , [ @subscriber = ] 'subscriber' ]  
    [ , [ @destination_db = ] 'destination_db' ]   
    [ , [ @found=] found OUTPUT ]  
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>引数  
`[ @publication = ] 'publication'` 関連付けられているパブリケーションの名前です。 *パブリケーション*は**sysname**、既定値は **%** 、このサーバーのすべてのサブスクリプション情報が返されます。  
  
`[ @article = ] 'article'` アーティクルの名前です。 *記事*は**sysname**、既定値は **%** 、選択したパブリケーションとサブスクライバーに関するすべてのサブスクリプション情報が返されます。 場合**すべて**パブリケーションの完全版のサブスクリプションの 1 つのエントリが返されます。  
  
`[ @subscriber = ] 'subscriber'` サブスクリプション情報を取得するサブスクライバーの名前です。 *サブスクライバー*は**sysname**、既定値は **%** 、選択したパブリケーションとアーティクルに関するすべてのサブスクリプション情報が返されます。  
  
`[ @destination_db = ] 'destination_db'` 転送先データベースの名前です。 *destination_db*は**sysname**、既定値は **%** します。  
  
`[ @found = ] 'found'OUTPUT` 行を返すことを示すフラグ。 *見つかった*は**int**は出力パラメーターで、既定値は 23456 です。  
  
 **1**パブリケーションが見つかったことを示します。  
  
 **0**パブリケーションが見つからないことを示します。  
  
`[ @publisher = ] 'publisher'` パブリッシャーの名前です。 *パブリッシャー*は**sysname**、および既定値は、現在のサーバーの名前。  
  
> [!NOTE]  
>  *パブリッシャー* Oracle パブリッシャーの場合を除き、指定するされません。  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**サブスクライバー**|**sysname**|サブスクライバーの名前。|  
|**パブリケーション**|**sysname**|パブリケーションの名前。|  
|**article**|**sysname**|アーティクルの名前。|  
|**転送先データベース**|**sysname**|レプリケートされたデータの格納先のデータベースの名前。|  
|**サブスクリプションの状態**|**tinyint**|サブスクリプションの状態:<br /><br /> **0** = 非アクティブ<br /><br /> **1** = サブスクライブ<br /><br /> **2** = アクティブ|  
|**同期の種類**|**tinyint**|サブスクリプションの同期の種類:<br /><br /> **1** = 自動<br /><br /> **2** = なし|  
|**サブスクリプションの種類**|**int**|サブスクリプションの種類。<br /><br /> **0**プッシュを =<br /><br /> **1** = プル<br /><br /> **2** = 匿名|  
|**完全なサブスクリプション**|**bit**|サブスクリプションがパブリケーション内のすべてのアーティクルを対象としているかどうかを示します。<br /><br /> **0** = いいえ<br /><br /> **1** = はい|  
|**サブスクリプション名**|**nvarchar (255)**|サブスクリプションの名前。|  
|**更新モード**|**int**|**0** = 読み取り専用<br /><br /> **1** = 即時更新サブスクリプション|  
|**ディストリビューション ジョブ id**|**binary(16)**|ディストリビューション エージェントのジョブ ID。|  
|**loopback_detection**|**bit**|ディストリビューション エージェントが、サブスクライバーで発生したトランザクションをサブスクライバーに戻すかどうかを示します。<br /><br /> **0** = 戻す。<br /><br /> **1** = は送信しません。<br /><br /> 双方向トランザクション レプリケーションで使用されます。 詳細については、「 [Bidirectional Transactional Replication](../../relational-databases/replication/transactional/bidirectional-transactional-replication.md)」を参照してください。|  
|**offload_enabled**|**bit**|レプリケーション エージェントのオフロードするために、サブスクライバーで実行設定されているかどうかを指定します。<br /><br /> 場合**0**エージェントがパブリッシャーで実行します。<br /><br /> 場合**1**サブスクライバーでエージェントを実行します。|  
|**offload_server**|**sysname**|リモート エージェントのアクティブ化を有効になっているサーバーの名前。 NULL の場合、現在の offload_server に一覧表示[MSdistribution_agents](../../relational-databases/system-tables/msdistribution-agents-transact-sql.md)テーブルが使用されます。|  
|**dts_package_name**|**sysname**|データ変換サービス (DTS) パッケージの名前を指定します。|  
|**dts_package_location**|**int**|1 つは、サブスクリプションに割り当てられている場合、DTS パッケージの場所です。 パッケージの値がある場合**0**でパッケージの場所を指定します、**ディストリビューター**します。 値**1**を指定します、**サブスクライバー**します。|  
|**subscriber_security_mode**|**smallint**|セキュリティ モードをサブスクライバーで、場所**1** Windows 認証では、ことを意味と**0**意味[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証します。|  
|**subscriber_login**|**sysname**|サブスクライバーのログイン名です。|  
|**@subscriber_password**||実際のサブスクライバー パスワードは返されません。 によってマスクされる結果は、" **&#42;&#42;&#42;&#42;&#42;&#42;** "文字列。|  
|**job_login**|**sysname**|ディストリビューション エージェントを実行する Windows アカウントの名前。|  
|**job_password**||実際のジョブ パスワードは返されません。 によってマスクされる結果は、" **&#42;&#42;&#42;&#42;&#42;&#42;** "文字列。|  
|**distrib_agent_name**|**nvarchar(100)**|サブスクリプションを同期するエージェント ジョブの名前。|  
|**subscriber_type**|**tinyint**|サブスクライバーは、次のいずれかの種類です。<br /><br /> **0** = SQL Server サブスクライバー<br /><br /> **1** = ODBC データ ソース サーバー<br /><br /> **2** = Microsoft JET データベース (非推奨)<br /><br /> **3** = OLE DB プロバイダー|  
|**subscriber_provider**|**sysname**|一意なプログラム識別子 (PROGID)、SQL Server 以外のデータ ソースの OLE DB プロバイダーが登録されています。|  
|**subscriber_datasource**|**nvarchar (4000)**|OLE DB プロバイダーで認識されるデータ ソースの名前。|  
|**subscriber_providerstring**|**nvarchar (4000)**|データ ソースを識別する OLE DB プロバイダーに固有の接続文字列。|  
|**subscriber_location**|**nvarchar (4000)**|OLE DB プロバイダーで認識されるデータベースの場所|  
|**対応します。**|**sysname**|OLE DB プロバイダーに接続するときに使用されるカタログします。|  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>コメント  
 **sp_helpsubscription**スナップショットおよびトランザクション レプリケーションで使用されます。  
  
## <a name="permissions"></a>アクセス許可  
 アクセス許可は既定の実行、**パブリック**ロール。 ユーザーに返されるのは、ユーザーが自分で作成したサブスクリプションの情報だけです。 メンバーにすべてのサブスクリプションに関する情報が返されます、 **sysadmin**固定サーバー ロールのメンバー、または発行元、 **db_owner**パブリケーション データベースの固定データベース ロール。  
  
## <a name="see-also"></a>関連項目  
 [sp_addsubscription &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md)   
 [sp_changesubstatus &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changesubstatus-transact-sql.md)   
 [sp_dropsubscription &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
