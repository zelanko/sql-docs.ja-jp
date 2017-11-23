---
title: "sp_MSchange_logreader_agent_properties (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
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
- sp_MSchange_logreader_agent_properties_TSQL
- sp_MSchange_logreader_agent_properties
helpviewer_keywords: sp_MSchange_logreader_agent_properties
ms.assetid: 925df9d3-a041-4046-8e17-c47f40edb86d
caps.latest.revision: "17"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ea342cad83b587382ca9e25141facd613263a20e
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="spmschangelogreaderagentproperties-transact-sql"></a>sp_MSchange_logreader_agent_properties (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  実行されるログ リーダー エージェント ジョブのプロパティを変更、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]またはそれ以降のバージョンのディストリビューター。 プロパティを変更するパブリッシャーのインスタンス上の実行時にこのストアド プロシージャを使用[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]です。 このストアド プロシージャは、ディストリビューター側でディストリビューション データベースについて実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_MSchange_logreader_agent_properties [ @publisher = ] 'publisher'  
        , [ @publisher_db = ] 'publisher_db'  
        , [ @publisher_security_mode = ] publisher_security_mode  
        , [ @publisher_login = ] 'publisher_login'  
        , [ @publisher_password = ] 'publisher_password'   
        , [ @job_login = ] 'job_login'  
        , [ @job_password = ] 'job_password'  
        , [ @publisher_type = ] 'publisher_type'  
```  
  
## <a name="arguments"></a>引数  
 [  **@publisher**  =] **'***パブリッシャー***'**  
 パブリッシャーの名前です。 *パブリッシャー*は**sysname**、既定値はありません。  
  
 [  **@publisher_db=** ] **'***publisher_db***'**  
 パブリケーション データベースの名前です。 *publisher_db*は**sysname**、既定値はありません。  
  
 [  **@publisher_security_mode** =] *publisher_security_mode*  
 パブリッシャーへの接続時にエージェントが使用するセキュリティ モードを指定します。 *publisher_security_mode*は**smallint**、既定値はありません。  
  
 **0**指定[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証します。  
  
 **1** Windows 認証を指定します。  
  
 [  **@publisher_login** =] **'***publisher_login***'**  
 パブリッシャーへの接続時に使用するログインを指定します。 *publisher_login*は**sysname**、既定値はありません。 *publisher_login*場合に指定する必要があります*publisher_security_mode*は**0**します。 場合*publisher_login* null と*publisher_security_mode*は**1**で指定した Windows アカウント*job_login*使用されますパブリッシャーへの接続時に  
  
 [  **@publisher_password** =] **'***publisher_password***'**  
 パブリッシャーへの接続時に使用するパスワードを指定します。 *publisher_password*は**sysname**、既定値はありません。  
  
 [  **@job_login** =] **'***job_login***'**  
 エージェントを実行する Windows アカウント用のログインを指定します。 *job_login*は**nvarchar (257)**、既定値はありません。 *これ以外は変更できません*[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] *パブリッシャーです。*  
  
 [  **@job_password** =] **'***job_password***'**  
 エージェントを実行する Windows アカウント用のパスワードを指定します。 *job_password*は**sysname**、既定値はありません。  
  
 [  **@publisher_type** =] **'***publisher_type***'**  
 パブリッシャーが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスで実行されていないときのパブリッシャーの種類を指定します。 *publisher_type*は**sysname**値は次のいずれかを指定できます。  
  
|値|Description|  
|-----------|-----------------|  
|**MSSQLSERVER**|指定します、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーです。|  
|**ORACLE**|標準の Oracle パブリッシャーを指定します。|  
|**ORACLE GATEWAY**|Oracle ゲートウェイ パブリッシャーを指定します。|  
  
 Oracle パブリッシャーと Oracle ゲートウェイ パブリッシャーとの違いの詳細については、次を参照してください。 [Oracle 公開の概要](../../relational-databases/replication/non-sql/oracle-publishing-overview.md)です。  
  
## <a name="remarks"></a>解説  
 **sp_MSchange_logreader_agent_properties**トランザクション レプリケーションで使用します。  
  
 実行する際は、すべてのパラメーターを指定する必要があります**sp_MSchange_logreader_agent_properties**です。 実行[sp_helplogreader_agent (& a) #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-helplogreader-agent-transact-sql.md)をログ リーダー エージェント ジョブの現在のプロパティを返します。  
  
 エージェントのログインまたはパスワードを変更した後、変更を有効にするには、エージェントを停止して再起動する必要があります。  
  
 インスタンスで、パブリッシャーを実行するときに[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]以降のバージョンを使用する必要ありますまたは[sp_changelogreader_agent](../../relational-databases/system-stored-procedures/sp-changelogreader-agent-transact-sql.md)ログ リーダー エージェントのプロパティを変更します。  
  
## <a name="permissions"></a>Permissions  
 メンバーにのみ、 **sysadmin** 、ディストリビューター側の固定サーバー ロールが実行できる**sp_MSchange_logreader_agent_properties**です。  
  
## <a name="see-also"></a>参照  
 [sp_addlogreader_agent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql.md)  
  
  
