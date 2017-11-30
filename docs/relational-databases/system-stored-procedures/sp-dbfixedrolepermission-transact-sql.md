---
title: "sp_dbfixedrolepermission (TRANSACT-SQL) |Microsoft ドキュメント"
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
- sp_dbfixedrolepermission
- sp_dbfixedrolepermission_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_dbfixedrolepermission
ms.assetid: b8c30191-f532-49cd-83f3-c271f63ce572
caps.latest.revision: "31"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1feabc780f7ec5029bd6c5dd431e21903709ad4c
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2017
---
# <a name="spdbfixedrolepermission-transact-sql"></a>sp_dbfixedrolepermission (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  固定データベース ロールの権限を表示します。 **sp_dbfixedrolepermission**正しい情報が返されます[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]です。 出力がで実装された権限階層への変更を反映していない[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]です。 詳細については、次を参照してください。[アクセス許可 &#40;データベース エンジン&#41;](../../relational-databases/security/permissions-database-engine.md)です。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_dbfixedrolepermission [ [ @rolename = ] 'role' ]  
```  
  
## <a name="arguments"></a>引数  
 [  **@rolename =** ] **'***ロール***'**  
 有効な [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 固定データベール ロールの名前を指定します。 *ロール*は**sysname**、既定値は NULL です。 場合*ロール*が指定されていない、すべての固定データベース ロールのアクセス許可が表示されます。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**DbFixedRole**|**sysname**|固定データベース ロールの名前。|  
|**権限**|**nvarchar (70)**|関連付けられた権限**DbFixedRole**|  
  
## <a name="remarks"></a>解説  
 固定データベース ロールの一覧を表示するには実行**sp_helpdbfixedrole**です。 次の表は、固定データベース ロールを示しています。  
  
|固定データベース ロール|Description|  
|-------------------------|-----------------|  
|**db_owner**|データベース所有者|  
|**db_accessadmin**|データベース アクセス管理者|  
|**db_securityadmin**|データベース セキュリティ管理者|  
|**db_ddladmin**|データベース データ定義言語 (DDL) 管理者|  
|**db_backupoperator**|データベース バックアップ オペレーター|  
|**db_datareader**|データベース データ リーダー|  
|**db_datawriter**|データベース データ ライター|  
|**db_denydatareader**|データベース否定データ リーダー|  
|**db_denydatawriter**|データベース否定データ ライター|  
  
 メンバー、 **db_owner**固定データベース ロールの他のすべての固定データベース ロールのアクセス許可があります。 固定サーバー ロールのアクセス許可を表示するには、実行**sp_srvrolepermission**です。  
  
 結果セットが含まれています、[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントを実行して、データベース ロールのメンバーによって、実行できるその他の特別な操作です。  
  
## <a name="permissions"></a>Permissions  
 ロール **public** のメンバーシップが必要です。  
  
## <a name="examples"></a>使用例  
 次のクエリでは、固定データベース ロールを指定せず、すべての固定データベース ロールに対する権限を返します。  
  
```  
EXEC sp_dbfixedrolepermission;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [セキュリティのストアド プロシージャと #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sp_addrolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md)   
 [sp_droprolemember &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-droprolemember-transact-sql.md)   
 [sp_helpdbfixedrole &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-helpdbfixedrole-transact-sql.md)   
 [sp_srvrolepermission &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-srvrolepermission-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
