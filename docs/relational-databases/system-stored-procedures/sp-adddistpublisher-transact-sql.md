---
title: "sp_adddistpublisher (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_adddistpublisher
- sp_adddistpublisher_TSQL
helpviewer_keywords:
- sp_adddistpublisher
ms.assetid: 04e15011-a902-4074-b38c-3ec2fc73b838
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e29470258112326d4a8a3c17c0bb0cadfacbab3e
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="spadddistpublisher-transact-sql"></a>sp_adddistpublisher (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  指定されたディストリビューション データベースを使用するように、パブリッシャーを構成します。 このストアド プロシージャは、ディストリビューター側で任意のデータベースについて実行されます。 なお、ストアド プロシージャ[sp_adddistributor (& a) #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-adddistributor-transact-sql.md)と[sp_adddistributiondb (& a) #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-adddistributiondb-transact-sql.md)このストアド プロシージャを使用する前に実行されている必要があります。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_adddistpublisher [ @publisher= ] 'publisher'   
        , [ @distribution_db= ] 'distribution_db'   
    [ , [ @security_mode= ] security_mode ]   
    [ , [ @login= ] 'login' ]   
    [ , [ @password= ] 'password' ]   
    [ , [ @working_directory= ] 'working_directory' ]   
    [ , [ @trusted= ] 'trusted' ]   
    [ , [ @encrypted_password= ] encrypted_password ]   
    [ , [ @thirdparty_flag = ] thirdparty_flag ]  
    [ , [ @publisher_type = ] 'publisher_type' ]  
```  
  
## <a name="arguments"></a>引数  
 [  **@publisher=**] **'***パブリッシャー***'**  
 パブリッシャー名です。 *パブリッシャー*は**sysname**、既定値はありません。  
  
 [  **@distribution_db=**] **'***distribution_db***'**  
 ディストリビューション データベースの名前を指定します。 *distributor_db*は**sysname**、既定値はありません。 このパラメーターは、レプリケーション エージェントがパブリッシャーに接続するために使用します。  
  
 [  **@security_mode=**] *security_mode*  
 実装されているセキュリティ モードを指定します。 このパラメーターは、キュー更新サブスクリプションのパブリッシャーに接続する場合、または [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 以外のパブリッシャーを使用する場合に、レプリケーション エージェントのみによって使用されます。 *security_mode*は**int**、これらの値のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**0**|ディストリビューターの使用時のレプリケーション エージェント[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーへの接続を認証します。|  
|**1** (既定値)|ディストリビューター側のレプリケーション エージェントは Windows 認証を使用してパブリッシャーに接続します。|  
  
 [  **@login=**] **'***ログイン***'**  
 ログインを指定します。 このパラメーターは必要な場合*security_mode*は**0**します。 *ログイン*は**sysname**、既定値は NULL です。 このパラメーターは、レプリケーション エージェントがパブリッシャーに接続するために使用します。  
  
 [  **@password=**] **'***パスワード***'**]  
 パスワードです。 *パスワード*は**sysname**、既定値は NULL です。 このパラメーターは、レプリケーション エージェントがパブリッシャーに接続するために使用します。  
  
> [!IMPORTANT]  
>  空白のパスワードは使用しないでください。 強力なパスワードを使用してください。  
  
 [  **@working_directory=**] **'***working_directory***'**  
 パブリケーション用のデータ ファイルとスキーマ ファイルの格納に使用する作業ディレクトリの名前を指定します。 *working_directory*は**nvarchar (255)**、および既定値は ReplData フォルダーのこのインスタンスの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、たとえば ' C:\Program files \microsoft SQL server Server\MSSQL\MSSQ.1\ReplData です。 名前は UNC 形式で指定する必要があります。  
  
 [  **@trusted=**] **'***信頼***'**  
 このパラメーターは、非推奨であり、旧バージョンとの互換性のためにのみ提供されています。 *信頼された*は**nvarchar (5)**、これ以外に設定し、 **false**エラーが発生します。  
  
 [  **@encrypted_password=**] *encrypted_password*  
 設定*encrypted_password*は現在サポートされていません。 これを設定しようとしています。**ビット**パラメーターを**1** 、エラーが発生します。  
  
 [  **@thirdparty_flag =**] *thirdparty_flag*  
 パブリッシャーが[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 *thirdparty_flag*は**ビット**値は次のいずれかを指定できます。  
  
|値|Description|  
|-----------|-----------------|  
|**0** (既定値)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベースです。|  
|**1**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 以外のデータベース|  
  
 [  **@publisher_type** =] **'***publisher_type***'**  
 パブリッシャーがない場合に、パブリッシャーの種類を示す[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 *publisher_type* sysname は、次の値のいずれかになります。  
  
|値|Description|  
|-----------|-----------------|  
|**MSSQLSERVER**<br /><br /> (既定値)。|指定します、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーです。|  
|**ORACLE**|標準の Oracle パブリッシャーを指定します。|  
|**ORACLE GATEWAY**|Oracle ゲートウェイ パブリッシャーを指定します。|  
  
 Oracle パブリッシャーと Oracle ゲートウェイ パブリッシャーとの違いの詳細については、次を参照してください。 [Oracle パブリッシャーを構成する](../../relational-databases/replication/non-sql/configure-an-oracle-publisher.md)です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_adddistpublisher**はスナップショット レプリケーション、トランザクション レプリケーション、およびマージ レプリケーションで使用します。  
  
## <a name="example"></a>例  
 [!code-sql[HowTo#AddDistPub](../../relational-databases/replication/codesnippet/tsql/sp-adddistpublisher-tran_1.sql)]  
  
## <a name="permissions"></a>Permissions  
 メンバーにのみ、 **sysadmin**固定サーバー ロールが実行できる**sp_adddistpublisher**です。  
  
## <a name="see-also"></a>参照  
 [パブリッシングとディストリビューションの構成](../../relational-databases/replication/configure-publishing-and-distribution.md)   
 [sp_changedistpublisher (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-changedistpublisher-transact-sql.md)   
 [sp_dropdistpublisher &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-dropdistpublisher-transact-sql.md)   
 [sp_helpdistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpdistpublisher-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [ディストリビューションの構成](../../relational-databases/replication/configure-distribution.md)  
  
  
