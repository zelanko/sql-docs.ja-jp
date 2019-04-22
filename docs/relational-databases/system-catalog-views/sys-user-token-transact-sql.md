---
title: sys.user_token (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.user_token
- user_token
- sys.user_token_TSQL
- user_token_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- logins [SQL Server], security tokens
- sys.user_token catalog view
- user tokens [SQL Server]
- tokens [SQL Server]
- user_token catalog view
ms.assetid: be018103-5e57-43a4-9160-9bf420892aa7
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: a120fe3802235ff0d5548693d9bf7f4638ef5e42
ms.sourcegitcommit: 323d2ea9cb812c688cfb7918ab651cce3246c296
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59506489"
---
# <a name="sysusertoken-transact-sql"></a>sys.user_token (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  ユーザー トークンの一部であるデータベース プリンシパルごとに 1 つの行を返します[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**principal_id**|**int**|プリンシパルの ID です。 値はデータベース内で一意です。|  
|**sid**|**varbinary(85)**|プリンシパルがデータベースの外部で定義されている場合、プリンシパルのセキュリティ識別子。 たとえば、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログイン、Windows ログイン、Windows グループ ログイン、証明書にマップされるログインなどです。それ以外の場合、この値は NULL になります。|  
|**name**|**nvarchar (128)**|プリンシパルの名前。 値はデータベース内で一意です。|  
|**type**|**nvarchar (128)**|プリンシパルの種類の説明です。 すべての型にマップされます**sid**します。 値は次のいずれかになります。<br /><br /> SQL USER<br /><br /> WINDOWS ログイン<br /><br /> WINDOWS GROUP<br /><br /> ROLE<br /><br /> APPLICATION ROLE<br /><br /> DATABASE ROLE<br /><br /> USER MAPPED TO CERTIFICATE<br /><br /> 非対称キーにマップされているユーザー<br /><br /> CERTIFICATE<br /><br /> ASYMMETRIC KEY|  
|**usage**|**nvarchar (128)**|GRANT または DENY 権限の評価にプリンシパルが参加するかどうか、または認証子としての役割を果たすかどうかを示します。<br /><br /> この値には、次のいずれかを指定できます。<br /><br /> 許可または拒否<br /><br /> 拒否のみ<br /><br /> AUTHENTICATOR|  
  
## <a name="see-also"></a>参照  
 [sys.login_token &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-login-token-transact-sql.md)   
 [sys.server_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md)   
 [sys.database_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)   
 [プリンシパル &#40;データベース エンジン&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  
