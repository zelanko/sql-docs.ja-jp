---
title: "sp_changesubscription (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 10/28/2015
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
f1_keywords:
- changesubscription
- sp_changesubscription
- changesubscription_TSQL
- sp_changesubscription_TSQL
helpviewer_keywords: sp_changesubscription
ms.assetid: f9d91fe3-47cf-4915-b6bf-14c9c3d8a029
caps.latest.revision: "40"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5e2a49e9b60927d1838205a5ae594c01ee4a1ffb
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="spchangesubscription-transact-sql"></a>sp_changesubscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  キュー更新トランザクション レプリケーションに関係する、スナップショットのプロパティまたはトランザクションのプッシュ サブスクリプションやプル サブスクリプションのプロパティを変更します。 その他のすべての種類のプル サブスクリプションのプロパティを変更するには、次のように使用します。 [sp_change_subscription_properties (& a) #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-change-subscription-properties-transact-sql.md). **sp_changesubscription**はパブリッシャーのパブリケーション データベースで実行します。  
  
> [!IMPORTANT]  
>  リモート ディストリビューターを使用するパブリッシャーを構成する場合は、 *job_login* および *job_password*を含むすべてのパラメーターに指定された値がディストリビューターにプレーン テキストとして送信されます。 このストアド プロシージャを実行する前に、パブリッシャーとリモート ディストリビューターの間の接続を暗号化する必要があります。 詳細については、「[データベース エンジンへの暗号化接続の有効化 &#40;SQL Server 構成マネージャー&#41;](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md)」を参照してください。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_changesubscription [ @publication = ] 'publication'  
        , [ @article = ] 'article'  
        , [ @subscriber = ] 'subscriber'  
        , [ @destination_db = ] 'destination_db'  
        , [ @property = ] 'property'  
        , [ @value = ] 'value'  
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>引数  
 [  **@publication** =] **'***パブリケーション***'**  
 変更するパブリケーションの名前を指定します。 *パブリケーション*は**sysname**、既定値はありません  
  
 [  **@article**  =] **'***記事***'**  
 変更するアーティクルの名前を指定します。 *記事*は**sysname**、既定値はありません。  
  
 [  **@subscriber**  =] **'***サブスクライバー***'**  
 サブスクライバーの名前です。 *サブスクライバー*は**sysname**、既定値はありません。  
  
 [  **@destination_db**  =] **'***destination_db***'**  
 サブスクリプション データベースの名前です。 *destination_db*は**sysname**、既定値はありません。  
  
 [  **@property=**] **'***プロパティ***'**  
 指定したサブスクリプションの変更対象となるプロパティを指定します。 *プロパティ*は**nvarchar (30)**テーブル内の値のいずれかを指定できます。  
  
 [  **@value=**] **'***値***'**  
 指定された新しい値は、*プロパティ*です。 *値*は**nvarchar (4000)**テーブル内の値のいずれかを指定できます。  
  
|プロパティ|値|Description|  
|--------------|-----------|-----------------|  
|**distrib_job_login**||エージェントを実行する [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows アカウントのログイン。|  
|**distrib_job_password**||エージェントを実行する Windows アカウントのパスワード。|  
|**対応する、**||OLE DB プロバイダーに接続するときに使用されるカタログ。 このプロパティはに対してのみ有効以外[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]サブスクライバーです。|  
|**subscriber_datasource**||OLE DB プロバイダーで認識されるデータ ソースの名前。 *このプロパティはに対してのみ有効以外*[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] *サブスクライバーです。*|  
|**subscriber_location**||OLE DB プロバイダーで認識されるデータベースの場所。 *このプロパティはに対してのみ有効以外*[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] *サブスクライバーです。*|  
|**subscriber_login**||サブスクライバーでのログイン名。|  
|**subscriber_password**||指定したログインに対する複雑なパスワード。|  
|**subscriber_security_mode**|**1**|サブスクライバーに接続するときに Windows 認証を使用。|  
||**0**|使用して[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]サブスクライバーに接続するときに認証します。|  
|**subscriber_provider**||一意なプログラム識別子 (PROGID) を OLE DB provider for 以外の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データ ソースを登録します。 *このプロパティはに対してのみ有効以外*[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] *サブスクライバーです。*|  
|**subscriber_providerstring**||データ ソースを識別する、OLE DB プロバイダー固有の接続文字列。 *このプロパティはに対してのみ有効以外*[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] *サブスクライバーです。*|  
|**subscriptionstreams**||変更のバッチをサブスクライバーに並列的に適用するために、ディストリビューション エージェントごとに許可される接続の数。 値の範囲**1**に**64**はサポートされて[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーです。 このプロパティを指定する必要があります**0**の非[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]サブスクライバー、Oracle パブリッシャー、またはピア ツー ピア サブスクリプションです。|  
|**subscriber_type**|**1**|ODBC データ ソース サーバー|  
||**3**|OLE DB プロバイダー|  
|**メモリ最適化**|**bit**|サブスクリプションがメモリ最適化テーブルをサポートしていることを示します。 *memory_optimized*は**ビット**場所 1 が true (サブスクリプションでは、メモリ最適化テーブルをサポートします)、します。|  
  
 [  **@publisher =** ] **'***パブリッシャー***'**  
 指定以外[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーです。 *パブリッシャー*は**sysname**、既定値は NULL です。  
  
> [!NOTE]  
>  *パブリッシャー*を指定しないで、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーです。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_changesubscription**は、スナップショットおよびトランザクション レプリケーションで使用します。  
  
 **sp_changesubscription**プッシュ サブスクリプションのプロパティを変更またはプル サブスクリプションに関連するキュー更新トランザクション レプリケーションにのみ使用できます。 その他のすべての種類のプル サブスクリプションのプロパティを変更するには、次のように使用します。 [sp_change_subscription_properties (& a) #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-change-subscription-properties-transact-sql.md).  
  
 エージェントのログインまたはパスワードを変更した後、変更を有効にするには、エージェントを停止して再起動する必要があります。  
  
## <a name="permissions"></a>Permissions  
 メンバーにのみ、 **sysadmin**固定サーバー ロールまたは**db_owner**固定データベース ロールが実行できる**sp_changesubscription**です。  
  
## <a name="see-also"></a>参照  
 [sp_addsubscription &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md)   
 [sp_dropsubscription &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql.md)  
  
  
