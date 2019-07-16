---
title: sp_MSchange_logreader_agent_properties (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_MSchange_logreader_agent_properties_TSQL
- sp_MSchange_logreader_agent_properties
helpviewer_keywords:
- sp_MSchange_logreader_agent_properties
ms.assetid: 925df9d3-a041-4046-8e17-c47f40edb86d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7a9a493d7f8dc5b4305638eb1ac5ffdcb6d0858a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67905203"
---
# <a name="spmschangelogreaderagentproperties-transact-sql"></a>sp_MSchange_logreader_agent_properties (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  実行されるログ リーダー エージェント ジョブのプロパティを変更、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]またはそれ以降のバージョンのディストリビューター。 このストアド プロシージャがパブリッシャーのインスタンス上の実行時にプロパティを変更する使用[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]します。 このストアド プロシージャは、ディストリビューター側でディストリビューション データベースについて実行されます。  
  
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
`[ @publisher = ] 'publisher'` パブリッシャーの名前です。 *パブリッシャー* は **sysname** 、既定値はありません。  
  
`[ @publisher_db = ] 'publisher_db'` パブリケーション データベースの名前です。 *publisher_db* は **sysname** 、既定値はありません。  
  
`[ @publisher_security_mode = ] publisher_security_mode` パブリッシャーに接続するときに、エージェントによって使用されるセキュリティ モード。 *publisher_security_mode*は**smallint**、既定値はありません。  
  
 **0**指定[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証します。  
  
 **1** Windows 認証を指定します。  
  
`[ @publisher_login = ] 'publisher_login'` パブリッシャーに接続するときに、ログインが使用されます。 *publisher_login*は**sysname**、既定値はありません。 *publisher_login*場合に指定する必要があります*publisher_security_mode*は**0**します。 場合*publisher_login* null と*publisher_security_mode*は**1**で指定した Windows アカウント*job_login*使用されますときに、パブリッシャーに接続します。  
  
`[ @publisher_password = ] 'publisher_password'` パブリッシャーに接続するときに、パスワードが使用されます。 *publisher_password*は**sysname**、既定値はありません。  
  
`[ @job_login = ] 'job_login'` エージェントを実行する Windows アカウントのログインです。 *job_login*は**nvarchar (257)** 、既定値はありません。 *これ以外は変更できません*[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] *パブリッシャーです。*  
  
`[ @job_password = ] 'job_password'` エージェントを実行する Windows アカウントのパスワードです。 *job_password* は **sysname** 、既定値はありません。  
  
`[ @publisher_type = ] 'publisher_type'` パブリッシャーがのインスタンスで実行されていない場合、パブリッシャーの種類を指定[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。 *publisher_type*は**sysname**値は次のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**MSSQLSERVER**|指定します、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーです。|  
|**ORACLE**|標準の Oracle パブリッシャーを指定します。|  
|**ORACLE GATEWAY**|Oracle ゲートウェイ パブリッシャーを指定します。|  
  
 Oracle パブリッシャーと Oracle ゲートウェイ パブリッシャーとの違いの詳細については、次を参照してください。 [Oracle 公開の概要](../../relational-databases/replication/non-sql/oracle-publishing-overview.md)します。  
  
## <a name="remarks"></a>コメント  
 **sp_MSchange_logreader_agent_properties**はトランザクション レプリケーションで使用します。  
  
 実行するときに、すべてのパラメーターを指定する必要があります**sp_MSchange_logreader_agent_properties**します。 実行[sp_helplogreader_agent &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-helplogreader-agent-transact-sql.md)をログ リーダー エージェント ジョブの現在のプロパティを返します。  
  
 エージェントのログインまたはパスワードを変更した後、変更を有効にするには、エージェントを停止して再起動する必要があります。  
  
 インスタンスで、パブリッシャーを実行するときに[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]以降のバージョンを使用する必要がありますまたは[sp_changelogreader_agent](../../relational-databases/system-stored-procedures/sp-changelogreader-agent-transact-sql.md)ログ リーダー エージェントのプロパティを変更します。  
  
## <a name="permissions"></a>アクセス許可  
 メンバーのみ、 **sysadmin** 、ディストリビューター側の固定サーバー ロールが実行できる**sp_MSchange_logreader_agent_properties**します。  
  
## <a name="see-also"></a>参照  
 [sp_addlogreader_agent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql.md)  
  
  
