---
title: xp_enumgroups (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- xp_enumgroups_TSQL
- xp_enumgroups
dev_langs:
- TSQL
helpviewer_keywords:
- xp_enumgroups
ms.assetid: 0bd3ed36-e260-469c-a5ff-b033fb9ea59d
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 885e29f8abbeb185017bc2472566e41596a56900
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "68116768"
---
# <a name="xp_enumgroups-transact-sql"></a>xp_enumgroups (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ローカルの Microsoft Windows グループの一覧、または指定された Windows ドメインで定義されているグローバルグループの一覧が表示されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
xp_enumgroups [ 'domain_name' ]  
```  
  
## <a name="arguments"></a>引数  
 **'** *domain_name* **'**  
 グローバル グループの一覧を列挙する Windows ドメインの名前を指定します。 *domain_name*は**sysname**,、既定値は NULL です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**group**|**sysname**|Windows グループの名前|  
|**関する**|**sysname**|Windows によって提供される Windows グループの説明|  
  
## <a name="remarks"></a>Remarks  
 *Domain_name*が、の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスが実行されている Windows ベースのコンピューターの名前である場合、またはドメイン名が指定されていない場合**xp_enumgroups**は、を[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]実行しているコンピューターからローカルグループを列挙します。  
  
 **xp_enumgroups**の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスが Windows 98 で実行されている場合、xp_enumgroups は使用できません。  
  
## <a name="permissions"></a>アクセス許可  
 **Master**データベースの**db_owner**固定データベースロールのメンバーシップ、または**sysadmin**固定サーバーロールのメンバーシップが必要です。  
  
## <a name="examples"></a>使用例  
 次の例では、 `sales`ドメイン内のグループを一覧表示します。  
  
```  
EXEC xp_enumgroups 'sales';  
```  
  
## <a name="see-also"></a>参照  
 [sp_grantlogin &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-grantlogin-transact-sql.md)   
 [sp_revokelogin &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-revokelogin-transact-sql.md)   
 [システムストアドプロシージャ &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Transact-sql&#41;&#40;の一般的な拡張ストアドプロシージャ](../../relational-databases/system-stored-procedures/general-extended-stored-procedures-transact-sql.md)   
 [xp_loginconfig &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/xp-loginconfig-transact-sql.md)   
 [xp_logininfo &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/xp-logininfo-transact-sql.md)  
  
  
