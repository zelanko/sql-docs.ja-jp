---
title: sp_helpdistpublisher (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
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
- sp_helpdistpublisher_TSQL
- sp_helpdistpublisher
helpviewer_keywords:
- sp_helpdistpublisher
ms.assetid: f207c22d-8fb2-4756-8a9d-6c51d6cd3470
caps.latest.revision: 37
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ce3c9b89c29bb9e387819ddbc15996d6d072b979
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="sphelpdistpublisher-transact-sql"></a>sp_helpdistpublisher (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ディストリビューターを使用するパブリッシャーのプロパティを返します。 このストアド プロシージャは、ディストリビューター側で任意のデータベースについて実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_helpdistpublisher [ [ @publisher=] 'publisher']   
    [ , [ @check_user = ] check_user  
```  
  
## <a name="arguments"></a>引数  
 [  **@publisher=** ] **'***パブリッシャー***'**  
 プロパティが返されるパブリッシャーです。 *パブリッシャー*は**sysname**、既定値は **%**です。  
  
 [  **@check_user=** ] *check_user*  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|パブリッシャーの名前です。|  
|**distribution_db**|**sysname**|指定されたパブリッシャーのディストリビューション データベースです。|  
|**security_mode**|**int**|キュー更新サブスクリプションまたは以外のパブリッシャーへの接続にレプリケーション エージェントによって使用されるセキュリティ モード[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーです。<br /><br /> **0**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証<br /><br /> **1** = Windows 認証|  
|**login**|**sysname**|キュー更新サブスクリプションのパブリッシャーへの接続、または [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 以外のパブリッシャーとの接続のため、レプリケーション エージェントで使用されるログイン名です。|  
|**password**|**nvarchar (524)**|単純な暗号化形式で返されるパスワードです。 パスワードは NULL ユーザー以外の**sysadmin**です。|  
|**アクティブ**|**bit**|リモート パブリッシャーがディストリビューターとしてローカル サーバーを使用しているかどうかを示します。<br /><br /> **0** = いいえ<br /><br /> **1** = はい|  
|**working_directory**|**nvarchar (255)**|作業ディレクトリの名前です。|  
|**信頼されています。**|**bit**|パブリッシャーがディストリビューターに接続するときにパスワードが必要かどうかを示します。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]し、以降のバージョンでこのを常に返します**0**、つまり、パスワードが必要です。|  
|**thirdparty_flag**|**bit**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] またはサード パーティのアプリケーションによってパブリケーションが有効にされるかどうかを示します。<br /><br /> **0** = [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]oracle、または Oracle Gateway Publisher です。<br /><br /> **1** = パブリッシャーと統合されている[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]サード パーティ製アプリケーションを使用します。|  
|**publisher_type**|**sysname**|パブリッシャーの種類次のいずれかを指定できます。<br /><br /> **MSSQLSERVER**<br /><br /> **ORACLE**<br /><br /> **ORACLE GATEWAY**|  
|**publisher_data_source**|**nvarchar (4000)**|パブリッシャーでの OLE DB データ ソースの名前です。|  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_helpdistpublisher**はあらゆる種類のレプリケーションで使用します。  
  
 **sp_helpdistpublisher**パブリッシャー ログインは表示されませんかの結果のパスワードを設定ではない**sysadmin**ログインします。  
  
## <a name="permissions"></a>権限  
 メンバー、 **sysadmin**固定サーバー ロールを実行**sp_helpdistpublisher**の任意のパブリッシャーをディストリビューターとしてローカル サーバーを使用します。 メンバー、 **db_owner**固定データベース ロールまたは**replmonitor**ディストリビューション データベースでロール実行**sp_helpdistpublisher**を使用している任意のパブリッシャーディストリビューション データベースです。 指定したパブリケーションのパブリケーション アクセスのユーザーを一覧表示*パブリッシャー*実行**sp_helpdistpublisher**です。 場合*パブリッシャー*が指定されていない、ユーザーがアクセスする権限を持っているすべてのパブリッシャーに対して情報が返されます。  
  
## <a name="see-also"></a>参照  
 [View and Modify Distributor and Publisher Properties (ディストリビューターとパブリッシャーのプロパティの表示および変更)](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [sp_adddistpublisher &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql.md)   
 [sp_changedistpublisher (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-changedistpublisher-transact-sql.md)   
 [sp_dropdistpublisher &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropdistpublisher-transact-sql.md)  
  
  
