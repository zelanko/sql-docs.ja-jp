---
title: xp_enumgroups (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- xp_enumgroups_TSQL
- xp_enumgroups
dev_langs:
- TSQL
helpviewer_keywords:
- xp_enumgroups
ms.assetid: 0bd3ed36-e260-469c-a5ff-b033fb9ea59d
caps.latest.revision: 23
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8c36dc60e01a42d94b279193216b2d861c9dda95
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="xpenumgroups-transact-sql"></a>xp_enumgroups (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Microsoft Windows のローカル グループの一覧、または指定した Windows ドメインで定義されるグローバル グループの一覧を提供します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
xp_enumgroups [ 'domain_name' ]  
```  
  
## <a name="arguments"></a>引数  
 **'** *domain_name* **'**  
 グローバル グループの一覧を列挙する Windows ドメインの名前を指定します。 *domain_name*は**sysname**、既定値は NULL です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**グループ**|**sysname**|Windows グループの名前|  
|**comment**|**sysname**|Windows で提供される Windows グループの説明。|  
  
## <a name="remarks"></a>解説  
 場合*domain_name* Windows ベースのコンピューターの名前を指定するのインスタンス[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]で実行されているか、ドメイン名を指定すると、 **xp_enumgroups**コンピューターからローカル グループを列挙実行している[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  
  
 **xp_enumgroups**場合のインスタンスは使用できません[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]が Windows 98 で実行されています。  
  
## <a name="permissions"></a>権限  
 メンバーシップが必要、 **db_owner**の固定データベース ロール、**マスター**データベース、またはメンバーシップ、 **sysadmin**固定サーバー ロール。  
  
## <a name="examples"></a>使用例  
 次の例のグループを一覧表示、`sales`ドメイン。  
  
```  
EXEC xp_enumgroups 'sales';  
```  
  
## <a name="see-also"></a>参照  
 [sp_grantlogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-grantlogin-transact-sql.md)   
 [sp_revokelogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-revokelogin-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [汎用拡張ストアド プロシージャ&#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/general-extended-stored-procedures-transact-sql.md)   
 [xp_loginconfig &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/xp-loginconfig-transact-sql.md)   
 [xp_logininfo &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/xp-logininfo-transact-sql.md)  
  
  
