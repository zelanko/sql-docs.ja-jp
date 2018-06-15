---
title: sp_validatelogins (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_validatelogins
- sp_validatelogins_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_validatelogins
ms.assetid: 6ac52e21-e20d-469b-ad40-5aa091e06b61
caps.latest.revision: 25
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: f8bfcefdd3b43e8a52fce6514583a47ed6aa4119
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33252930"
---
# <a name="spvalidatelogins-transact-sql"></a>sp_validatelogins (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Windows ユーザーおよびグループにマップされているに関する情報をレポート[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]プリンシパルは、Windows 環境でが不要に存在します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_validatelogins  
```  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**SID**|**varbinary(85)**|Windows ユーザーまたはグループの Windows セキュリティ識別子 (SID)。|  
|**NT ログイン**|**sysname**|Windows ユーザーまたはグループの名前。|  
  
## <a name="remarks"></a>解説  
 孤立したサーバー レベルのプリンシパルがデータベース ユーザーを所有している場合、孤立したサーバー プリンシパルを削除するには、先にデータベース ユーザーを削除する必要があります。 データベース ユーザーを削除する使用[DROP USER](../../t-sql/statements/drop-user-transact-sql.md)です。 サーバー レベルのプリンシパルがデータベースのセキュリティ保護可能なリソースを所有している場合は、そのリソースの所有権を譲渡するか、リソースを削除する必要があります。 データベースの保護可能なリソースの所有権を譲渡するを使用して[ALTER AUTHORIZATION](../../t-sql/statements/alter-authorization-transact-sql.md)です。  
  
 Windows ユーザーおよびグループが存在しないことへのマッピングを削除する使用[DROP LOGIN](../../t-sql/statements/drop-login-transact-sql.md)です。  
  
## <a name="permissions"></a>権限  
 メンバーシップが必要、 **sysadmin**または**securityadmin**固定サーバー ロール。  
  
## <a name="examples"></a>使用例  
 次の例は、Windows ユーザーおよびグループが存在しなくなったのにのインスタンスへのアクセスが許可されていることが表示されます。[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  
  
```  
EXEC sp_validatelogins;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [セキュリティ ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [DROP USER & #40;TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-user-transact-sql.md)   
 [DROP LOGIN & #40;TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-login-transact-sql.md)   
 [ALTER AUTHORIZATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-authorization-transact-sql.md)  
  
  
