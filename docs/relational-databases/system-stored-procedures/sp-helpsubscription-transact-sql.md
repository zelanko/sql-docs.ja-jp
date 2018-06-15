---
title: sp_helpsubscription (TRANSACT-SQL) |Microsoft ドキュメント
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
f1_keywords:
- sp_helpsubscription_TSQL
- sp_helpsubscription
helpviewer_keywords:
- sp_helpsubscription
ms.assetid: ff96bcbf-e2b9-4da8-8515-d80d4ce86c16
caps.latest.revision: 22
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 0634a1b6cd117b82d31324e58590d9217f402528
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "33003351"
---
# <a name="sphelpsubscription-transact-sql"></a>sp_helpsubscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  特定のパブリケーション、アーティクル、サブスクライバー、またはサブスクリプションの集合に関連付けられたサブスクリプション情報を一覧表示します。 このストアド プロシージャは、パブリッシャーのパブリケーション データベースで実行します。  
  
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
 [ **@publication =** ] **'***publication***'**  
 関連付けられているパブリケーションの名前を指定します。 *パブリケーション*は**sysname**、既定値は**%**、このサーバーのすべてのサブスクリプション情報が返されます。  
  
 [  **@article=** ] **'***記事***'**  
 アーティクルの名前を指定します。 *記事*は**sysname**、既定値は**%**、選択したパブリケーションとサブスクライバーに関するすべてのサブスクリプション情報が返されます。 場合**すべて**パブリケーションの完全なサブスクリプションの 1 つのエントリが返されます。  
  
 [  **@subscriber=** ] **'***サブスクライバー***'**  
 サブスクリプション情報を取得するサブスクライバーの名前を指定します。 *サブスクライバー*は**sysname**、既定値は**%**、選択したパブリケーションとアーティクルのすべてのサブスクリプション情報が返されます。  
  
 [  **@destination_db=** ] **'***destination_db***'**  
 対象データベース名を指定します。 *destination_db*は**sysname**、既定値は **%** です。  
  
 [  **@found=** ] **'***見つかった***'** 出力  
 行を返すことを示すフラグです。 *見つかった*は**int**と出力パラメーター、既定値は 23456 です。  
  
 **1**パブリケーションが見つかったことを示します。  
  
 **0**パブリケーションが見つからないことを示します。  
  
 [ **@publisher**=] **'***パブリッシャー***'**  
 パブリッシャーの名前です。 *パブリッシャー*は**sysname**、および既定値は、現在のサーバーの名前。  
  
> [!NOTE]  
>  *パブリッシャー*は指定しないで、Oracle パブリッシャーの場合を除く。  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**サブスクライバー**|**sysname**|サブスクライバーの名前です。|  
|**パブリケーション**|**sysname**|パブリケーションの名前です。|  
|**article**|**sysname**|アーティクルの名前。|  
|**転送先データベース**|**sysname**|レプリケートされたデータの格納先のデータベースの名前。|  
|**サブスクリプションの状態**|**tinyint**|サブスクリプションの状態:<br /><br /> **0** = 非アクティブ<br /><br /> **1** = サブスクライブ<br /><br /> **2** = アクティブ|  
|**同期の種類**|**tinyint**|サブスクリプションの同期の種類。<br /><br /> **1**自動を =<br /><br /> **2** = なし|  
|**サブスクリプションの種類**|**int**|サブスクリプションの種類。<br /><br /> **0**プッシュを =<br /><br /> **1**プルを =<br /><br /> **2** = 匿名|  
|**完全なサブスクリプション**|**bit**|サブスクリプションがパブリケーション内のすべてのアーティクルを対象としているかどうかを示します。<br /><br /> **0** = いいえ<br /><br /> **1** = はい|  
|**サブスクリプション名**|**nvarchar (255)**|サブスクリプションの名前。|  
|**更新モード**|**int**|**0** = 読み取り専用<br /><br /> **1** = 即時更新サブスクリプション|  
|**ディストリビューション ジョブの id**|**binary(16)**|ディストリビューション エージェントのジョブ ID。|  
|**loopback_detection**|**bit**|ディストリビューション エージェントが、サブスクライバーで発生したトランザクションをサブスクライバーに戻すかどうかを示します。<br /><br /> **0** = 戻す。<br /><br /> **1** = は送信しません。<br /><br /> 双方向トランザクション レプリケーションで使用されます。 詳細については、「 [双方向トランザクション レプリケーション](../../relational-databases/replication/transactional/bidirectional-transactional-replication.md)」を参照してください。|  
|**offload_enabled**|**bit**|レプリケーション エージェントのオフロードするために、サブスクライバーで実行する設定されているかどうかを指定します。<br /><br /> 場合**0**エージェントがパブリッシャーで実行します。<br /><br /> 場合**1**サブスクライバーでエージェントを実行します。|  
|**offload_server**|**sysname**|エージェントをリモートから起動するときに使用できるサーバーの名前。 NULL の場合、現在の offload_server に一覧表示[MSdistribution_agents](../../relational-databases/system-tables/msdistribution-agents-transact-sql.md)テーブルを使用します。|  
|**dts_package_name**|**sysname**|データ変換サービス (DTS) パッケージの名前。|  
|**dts_package_location**|**int**|DTS パッケージがサブスクリプションに割り当てられている場合の、DTS パッケージの場所。 パッケージの値がある場合**0** 、パッケージの場所を指定します、**ディストリビューター**です。 値**1**を指定します、**サブスクライバー**です。|  
|**subscriber_security_mode**|**smallint**|セキュリティ モードをサブスクライバーで、ここで**1** Windows 認証を意味と**0**意味[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証します。|  
|**subscriber_login**|**sysname**|サブスクライバーのログイン名です。|  
|**subscriber_password**||実際のサブスクライバー パスワードは返されません。 によって、結果がマスクされており、"**\*\*\*\*\*\***"文字列。|  
|**job_login**|**sysname**|ディストリビューション エージェントが実行される Windows アカウントの名前。|  
|**job_password**||実際のジョブ パスワードは返されません。 によって、結果がマスクされており、"**\*\*\*\*\*\***"文字列。|  
|**distrib_agent_name**|**nvarchar(100)**|サブスクリプションと同期するエージェント ジョブの名前。|  
|**subscriber_type**|**tinyint**|サブスクライバーの種類。次のいずれかになります。<br /><br /> **0** = SQL Server サブスクライバー<br /><br /> **1** = ODBC データ ソース サーバー<br /><br /> **2** = Microsoft JET データベース (非推奨)<br /><br /> **3** OLE DB プロバイダーを =|  
|**subscriber_provider**|**sysname**|SQL Server 以外のデータ ソース用の OLE DB プロバイダーを登録するときに使用される、一意なプログラム識別子 (PROGID)。|  
|**subscriber_datasource**|**nvarchar (4000)**|OLE DB プロバイダーで認識されるデータ ソースの名前。|  
|**subscriber_providerstring**|**nvarchar (4000)**|データ ソースを識別する、OLE DB プロバイダー固有の接続文字列。|  
|**subscriber_location**|**nvarchar (4000)**|OLE DB プロバイダーで認識されるデータベースの場所|  
|**対応する、**|**sysname**|OLE DB プロバイダーに接続するときに使用されるカタログ。|  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_helpsubscription**は、スナップショットおよびトランザクション レプリケーションで使用します。  
  
## <a name="permissions"></a>権限  
 アクセス許可は既定の実行、**パブリック**ロール。 ユーザーに返されるのは、ユーザーが自分で作成したサブスクリプションの情報だけです。 メンバーにすべてのサブスクリプションに関する情報が返されます、 **sysadmin**のメンバーまたはパブリッシャーの固定サーバー ロール、 **db_owner**パブリケーション データベースの固定データベース ロール。  
  
## <a name="see-also"></a>参照  
 [sp_addsubscription &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md)   
 [sp_changesubstatus &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changesubstatus-transact-sql.md)   
 [sp_dropsubscription &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
