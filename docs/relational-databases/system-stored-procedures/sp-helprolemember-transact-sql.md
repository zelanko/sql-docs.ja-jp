---
title: "sp_helprolemember (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_helprolemember_TSQL
- sp_helprolemember
dev_langs: TSQL
helpviewer_keywords: sp_helprolemember
ms.assetid: 42797510-aa5d-4564-85ac-27418419af9c
caps.latest.revision: "26"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: afdfcf6f89a398f20f4281249662e5c7b52852d3
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="sphelprolemember-transact-sql"></a>sp_helprolemember (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  現在のデータベースに含まれるロールの直接的なメンバーに関する情報を返します。  
  
||  
|-|  
|**適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [現在のバージョン](http://go.microsoft.com/fwlink/p/?LinkId=299658)まで)。|  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_helprolemember [ [ @rolename = ] 'role' ]  
```  
  
## <a name="arguments"></a>引数  
 [  **@rolename =** ] **'** *ロール* **'**  
 現在のデータベースに含まれるロールの名前を指定します。 *ロール*は**sysname**、既定値は NULL です。 *ロール*現在のデータベースに存在する必要があります。 場合*ロール*が指定されていない、現在のデータベースから少なくとも 1 つのメンバーが含まれているすべてのロールが返されます。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**DbRole**|**sysname**|現在のデータベースに存在するロールの名前。|  
|**メンバー名**|**sysname**|メンバーの名前**DbRole です。**|  
|**MemberSID**|**varbinary (85)**|セキュリティ識別子**MemberName です。**|  
  
## <a name="remarks"></a>解説  
 データベースには、入れ子になったロールが含まれている場合**MemberName**ロールの名前を指定できます。 **sp_helprolemember**入れ子になったロールを介して取得されたメンバーシップは表示されません。 たとえば、Role1 のメンバーである User1 Role1、Role2 のメンバーである場合`EXEC sp_helprolemember 'Role2'`; は、Role1 が Role1 のメンバー以外を返します (この例では、User1)。 入れ子になったメンバーシップを返すを実行する必要があります**sp_helprolemember**入れ子になった各ロールの繰り返しです。  
  
 使用して**sp_helpsrvrolemember**固定サーバー ロールのメンバーを表示します。  
  
 使用して[IS_ROLEMEMBER (& a) #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/is-rolemember-transact-sql.md)を指定したユーザー ロールのメンバーシップを確認します。  
  
## <a name="permissions"></a>Permissions  
 ロール **public** のメンバーシップが必要です。  
  
## <a name="examples"></a>使用例  
 次の例では、ロール `Sales` のメンバーを表示します。  
  
```  
EXEC sp_helprolemember 'Sales';  
```  
  
## <a name="see-also"></a>参照  
 [セキュリティのストアド プロシージャと #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sp_addrolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md)   
 [sp_droprolemember &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-droprolemember-transact-sql.md)   
 [sp_helprole &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-helprole-transact-sql.md)   
 [sp_helpsrvrolemember &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-helpsrvrolemember-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
