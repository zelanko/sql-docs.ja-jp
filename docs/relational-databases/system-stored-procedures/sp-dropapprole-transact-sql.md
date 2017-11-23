---
title: "sp_dropapprole (TRANSACT-SQL) |Microsoft ドキュメント"
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
- sp_dropapprole_TSQL
- sp_dropapprole
dev_langs: TSQL
helpviewer_keywords: sp_dropapprole
ms.assetid: ea1aefe6-8f7d-46e9-a3cb-7b037b393e73
caps.latest.revision: "28"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 021ca160d6fc89d8cc9609eacdfcd127f5d56e27
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="spdropapprole-transact-sql"></a>sp_dropapprole (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  アプリケーション ロールを現在のデータベースから削除します。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]使用して[DROP APPLICATION ROLE](../../t-sql/statements/drop-application-role-transact-sql.md)代わりにします。  
  
||  
|-|  
|**適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [現在のバージョン](http://go.microsoft.com/fwlink/p/?LinkId=299658)まで)。|  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_dropapprole [@rolename = ] 'role'  
```  
  
## <a name="arguments"></a>引数  
 [  **@rolename =** ] **'***ロール***'**  
 アプリケーション ロールを削除します。 *ロール*は、 **sysname**、既定値はありません。 *ロール*現在のデータベースに存在する必要があります。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_dropapprole**アプリケーション ロールを削除するのみ使用できます。 ロールがセキュリティ保護可能なリソースを所有している場合、そのロールを削除することはできません。 セキュリティ保護可能なリソースを所有しているアプリケーション ロールを削除するには、先にセキュリティ保護可能なリソースの所有権を譲渡するか削除する必要があります。  
  
 **sp_dropapprole**ユーザー定義のトランザクション内で実行することはできません。  
  
## <a name="permissions"></a>Permissions  
 データベースに対する ALTER ANY APPLICATION ROLE 権限が必要です。  
  
## <a name="examples"></a>使用例  
 次の例では、削除、`SalesApp`現在のデータベースからアプリケーション ロールです。  
  
```  
EXEC sp_dropapprole 'SalesApp';  
```  
  
## <a name="see-also"></a>参照  
 [セキュリティのストアド プロシージャと #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sp_addapprole &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-addapprole-transact-sql.md)   
 [DROP APPLICATION ROLE &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-application-role-transact-sql.md)   
 [sp_changeobjectowner &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-changeobjectowner-transact-sql.md)   
 [sp_setapprole と #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-setapprole-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
