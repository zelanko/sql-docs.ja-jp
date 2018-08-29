---
title: sp_validatelogins (TRANSACT-SQL) |Microsoft Docs
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
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: be184539a88e4a89fb841a26594a28eb0f2a2d33
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43029539"
---
# <a name="spvalidatelogins-transact-sql"></a>sp_validatelogins (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Windows ユーザーとグループにマップされているに関する情報をレポート[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]プリンシパルは、Windows 環境が不要に存在します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_validatelogins  
```  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**SID**|**varbinary(85)**|Windows ユーザーまたはグループの Windows セキュリティ識別子 (SID)。|  
|**NT ログイン**|**sysname**|Windows ユーザーまたはグループの名前。|  
  
## <a name="remarks"></a>コメント  
 孤立したサーバー レベルのプリンシパルがデータベース ユーザーを所有している場合、孤立したサーバー プリンシパルを削除するには、先にデータベース ユーザーを削除する必要があります。 データベース ユーザーを削除する使用[DROP USER](../../t-sql/statements/drop-user-transact-sql.md)します。 サーバー レベルのプリンシパルがデータベースのセキュリティ保護可能なリソースを所有している場合は、そのリソースの所有権を譲渡するか、リソースを削除する必要があります。 データベースのセキュリティ保護可能リソースの所有権を譲渡するには使用[ALTER AUTHORIZATION](../../t-sql/statements/alter-authorization-transact-sql.md)します。  
  
 Windows ユーザーおよびグループが存在しなくなったへのマッピングを削除する使用[DROP LOGIN](../../t-sql/statements/drop-login-transact-sql.md)します。  
  
## <a name="permissions"></a>アクセス許可  
 メンバーシップが必要です、 **sysadmin**または**securityadmin**固定サーバー ロール。  
  
## <a name="examples"></a>使用例  
 次の例は、Windows ユーザーとグループが存在しなくなったのにのインスタンスへのアクセスが許可されているが表示されます。[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。  
  
```  
EXEC sp_validatelogins;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [セキュリティ ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [DROP USER &#40;Transact-SQL&#41;](../../t-sql/statements/drop-user-transact-sql.md)   
 [DROP LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/drop-login-transact-sql.md)   
 [ALTER AUTHORIZATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-authorization-transact-sql.md)  
  
  
