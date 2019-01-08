---
title: sp_helpdistpublisher (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helpdistpublisher_TSQL
- sp_helpdistpublisher
helpviewer_keywords:
- sp_helpdistpublisher
ms.assetid: f207c22d-8fb2-4756-8a9d-6c51d6cd3470
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 85a6eaf76497b1fa763047a255cdb7784316541e
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2018
ms.locfileid: "52802744"
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
 プロパティが返されるパブリッシャーです。 *パブリッシャー*は**sysname**、既定値は **%** します。  
  
 [  **@check_user=** ] *check_user*  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|パブリッシャーの名前。|  
|**distribution_db**|**sysname**|指定されたパブリッシャーのディストリビューション データベースです。|  
|**security_mode**|**int**|キュー更新サブスクリプションのパブリッシャーへの接続、または [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 以外のパブリッシャーとの接続のため、レプリケーション エージェントで使用されるセキュリティ モードです。<br /><br /> **0**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証<br /><br /> **1** = Windows 認証|  
|**login**|**sysname**|キュー更新サブスクリプションのパブリッシャーへの接続、または [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 以外のパブリッシャーとの接続のため、レプリケーション エージェントで使用されるログイン名です。|  
|**password**|**nvarchar (524)**|単純な暗号化形式で返されるパスワードです。 パスワードは NULL ですユーザー以外の**sysadmin**します。|  
|**アクティブ**|**bit**|リモート パブリッシャーがディストリビューターとしてローカル サーバーを使用しているかどうかを示します。<br /><br /> **0** = いいえ<br /><br /> **1** = はい|  
|**working_directory**|**nvarchar (255)**|作業ディレクトリの名前です。|  
|**信頼されています。**|**bit**|パブリッシャーがディストリビューターに接続するときにパスワードが必要かどうかを示します。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]と以降のバージョンでこのを常に返します**0**、つまり、パスワードが必要であります。|  
|**thirdparty_flag**|**bit**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] またはサード パーティのアプリケーションによってパブリケーションが有効にされるかどうかを示します。<br /><br /> **0** = [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]oracle、または Oracle Gateway Publisher です。<br /><br /> **1** = パブリッシャーと統合されている[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]サード パーティ製アプリケーションを使用します。|  
|**publisher_type**|**sysname**|パブリッシャーの種類次のいずれかを指定できます。<br /><br /> **MSSQLSERVER**<br /><br /> **ORACLE**<br /><br /> **ORACLE GATEWAY**|  
|**publisher_data_source**|**nvarchar (4000)**|パブリッシャーでの OLE DB データ ソースの名前です。|  
|**storage_connection_string**|**nvarchar (4000)**|作業ディレクトリのストレージ アクセス キーとディストリビューターまたはパブリッシャー側の Azure SQL データベース。|  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>コメント  
 **sp_helpdistpublisher**はあらゆる種類のレプリケーションで使用します。  
  
 **sp_helpdistpublisher**パブリッシャー ログインには表示されませんか結果のパスワードを設定以外**sysadmin**ログインします。  
  
## <a name="permissions"></a>アクセス許可  
 メンバー、 **sysadmin**固定サーバー ロールが実行**sp_helpdistpublisher**の任意のパブリッシャーをディストリビューターとしてローカル サーバーを使用します。 メンバー、 **db_owner**固定データベース ロール、または**replmonitor**ディストリビューション データベースでロール実行**sp_helpdistpublisher**を使用しているパブリッシャーのディストリビューション データベースです。 指定したパブリケーションのパブリケーション アクセスのユーザーを一覧表示*パブリッシャー*実行**sp_helpdistpublisher**します。 場合*パブリッシャー*が指定されていない、ユーザーへのアクセス権を持っているすべてのパブリッシャーに対して情報が返されます。  
  
## <a name="see-also"></a>参照  
 [View and Modify Distributor and Publisher Properties (ディストリビューターとパブリッシャーのプロパティの表示および変更)](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [sp_adddistpublisher &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql.md)   
 [sp_changedistpublisher (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-changedistpublisher-transact-sql.md)   
 [sp_dropdistpublisher &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropdistpublisher-transact-sql.md)  
  
  
