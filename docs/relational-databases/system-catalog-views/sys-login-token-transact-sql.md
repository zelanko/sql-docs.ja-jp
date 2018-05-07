---
title: sys.login_token (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- login_token_TSQL
- sys.login_token_TSQL
- sys.login_token
- login_token
dev_langs:
- TSQL
helpviewer_keywords:
- sys.login_token catalog view
- logins [SQL Server], security tokens
- tokens [SQL Server]
ms.assetid: 86e06938-9d0a-44e5-99e2-55c8ef5f2f84
caps.latest.revision: 28
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 8ffa2027c83f8aebfb64a936b70cbee527526a51
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="syslogintoken-transact-sql"></a>sys.login_token (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ログイン トークンの一部であるサーバー プリンシパルすべてに 1 行を返します。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**principal_id**|**int**|プリンシパルの ID です。 この値は、サーバー内で一意です。|  
|**sid**|**varbinary(85)**|プリンシパルのセキュリティ識別子です。 これは、Windows プリンシパル場合**sid** Windows SID を = です。 ログインが、証明書にマップされている場合**sid**証明書から GUID を = です。|  
|**name**|**nvarchar(128)**|プリンシパルの名前。 この値は、サーバー内で一意です。|  
|**type**|**nvarchar(128)**|プリンシパルの種類の説明。 すべての型にマップされます**sid**です。 値は、次のいずれかです。<br /><br /> SQL LOGIN<br /><br /> WINDOWS LOGIN<br /><br /> WINDOWS GROUP<br /><br /> SERVER ROLE<br /><br /> LOGIN MAPPED TO CERTIFICATE<br /><br /> LOGIN MAPPED TO ASYMMETRIC KEY<br /><br /> CERTIFICATE<br /><br /> ASYMMETRIC KEY|  
|**使用状況**|**nvarchar(128)**|GRANT または DENY 権限の評価にプリンシパルが参加するかどうか、または認証子としての役割を果たすかどうかを示します。<br /><br /> この値は次のいずれかになります。<br /><br /> GRANT OR DENY<br /><br /> DENY ONLY<br /><br /> AUTHENTICATOR|  
  
## <a name="see-also"></a>参照  
 [sys.user_token &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-user-token-transact-sql.md)   
 [sys.server_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md)   
 [sys.database_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)   
 [プリンシパル &#40;データベース エンジン&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  
