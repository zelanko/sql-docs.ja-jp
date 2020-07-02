---
title: xp_revokelogin (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- xp_revokelogin
- xp_revokelogin_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- xp_revokelogin
ms.assetid: b3fa7678-dba4-4537-be94-5ae63ca11f81
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 9aee06246a9ca7922e62aef5d2a20aa7b67be347
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85755533"
---
# <a name="xp_revokelogin-transact-sql"></a>xp_revokelogin (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Windows グループまたはユーザーからへのアクセスを取り消し [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]代わりに[DROP LOGIN](../../t-sql/statements/drop-login-transact-sql.md)を使用してください。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
xp_revokelogin {[@loginame=] 'login'}  
```  
  
## <a name="arguments"></a>引数  
`[ @loginame = ] 'login'`アクセスを取り消す Windows ユーザーまたはグループの名前を指定します。 *ログイン*には、 **[ADVWKS\sylvester1]** などのドメイン名を含める必要があります。 *login*は**sysname**,、既定値はありません。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="remarks"></a>解説  
 代わりに DROP LOGIN を使用してください。  
  
## <a name="permissions"></a>アクセス許可  
 サーバーに対する ALTER ANY LOGIN 権限が必要です。  
  
## <a name="see-also"></a>関連項目  
 [sp_denylogin &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-denylogin-transact-sql.md)   
 [sp_grantlogin &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-grantlogin-transact-sql.md)   
 [sp_revokelogin &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-revokelogin-transact-sql.md)   
 [システムストアドプロシージャ &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Transact-sql&#41;&#40;の一般的な拡張ストアドプロシージャ](../../relational-databases/system-stored-procedures/general-extended-stored-procedures-transact-sql.md)   
 [xp_loginconfig &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/xp-loginconfig-transact-sql.md)   
 [xp_logininfo &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/xp-logininfo-transact-sql.md)  
  
  
