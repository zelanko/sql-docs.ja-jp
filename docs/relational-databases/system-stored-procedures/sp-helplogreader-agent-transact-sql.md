---
description: sp_helplogreader_agent (Transact-sql)
title: sp_helplogreader_agent (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helplogreader_agent
- sp_helplogreader_agent_TSQL
helpviewer_keywords:
- sp_helplogreader_agent
ms.assetid: ff837209-e2b3-481a-a48f-8530bfe53d97
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 4a5830f73e58925e3935fe554d7467b0582b2b28
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88481194"
---
# <a name="sp_helplogreader_agent-transact-sql"></a>sp_helplogreader_agent (Transact-sql)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  パブリケーションデータベースのログリーダーエージェントジョブのプロパティを返します。 このストアドプロシージャは、パブリッシャー側でパブリケーションデータベースに対して実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_helplogreader_agent [ [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>引数  
`[ @publisher = ] 'publisher'` パブリッシャーの名前を指定します。 *publisher* は **sysname**で、既定値は NULL です。  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**id**|**int**|エージェントの ID。|  
|**name**|**nvarchar (100)**|エージェントの名前。|  
|**publisher_security_mode**|**smallint**|パブリッシャーに接続するときにエージェントによって使用されるセキュリティモード。次のいずれかになります。<br /><br /> **0**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証<br /><br /> **1** = Windows 認証。|  
|**publisher_login**|**sysname**|パブリッシャーに接続するときに使用されるログインです。|  
|**publisher_password**|**nvarchar (524)**|セキュリティ上の理由から、の値 **\*\*\*\*\*\*\*\*\*\*** は常に返されます。|  
|**job_id**|**uniqueidentifier**|エージェントジョブの一意の ID。|  
|**job_login**|**nvarchar(512)**|ログリーダーエージェントを実行する Windows アカウントを指定します。このアカウントは、*ドメイン* \\ *ユーザー名*の形式で返されます。|  
|**job_password**|**sysname**|セキュリティ上の理由から、の値 **\*\*\*\*\*\*\*\*\*\*** は常に返されます。|  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または **1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_helplogreader_agent** は、トランザクションレプリケーションで使用します。  
  
## <a name="permissions"></a>アクセス許可  
 **Sp_helplogreader_agent**を実行できるのは、パブリッシャー側の**sysadmin**固定サーバーロールのメンバー、またはパブリケーションデータベースの**db_owner**固定データベースロールのメンバーだけです。  
  
## <a name="see-also"></a>参照  
 [レプリケーションのセキュリティ設定の表示および変更](../../relational-databases/replication/security/view-and-modify-replication-security-settings.md)   
 [sp_addlogreader_agent &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql.md)   
 [sp_changelogreader_agent &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-changelogreader-agent-transact-sql.md)  
  
  
