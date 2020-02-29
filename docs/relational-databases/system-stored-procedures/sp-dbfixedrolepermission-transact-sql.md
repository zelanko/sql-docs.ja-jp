---
title: sp_dbfixedrolepermission (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_dbfixedrolepermission
- sp_dbfixedrolepermission_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_dbfixedrolepermission
ms.assetid: b8c30191-f532-49cd-83f3-c271f63ce572
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2a51fcc7108c7f6af6237d77cbad73c87ed7c6e6
ms.sourcegitcommit: 2d4067fc7f2157d10a526dcaa5d67948581ee49e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2020
ms.locfileid: "78180117"
---
# <a name="sp_dbfixedrolepermission-transact-sql"></a>sp_dbfixedrolepermission (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  固定データベース ロールの権限を表示します。 **sp_dbfixedrolepermission**では、に[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]正しい情報が返されます。 出力には、に[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]実装された権限階層への変更は反映されません。 詳細については、「[データベースレベルのロール](../../relational-databases/security/authentication-access/database-level-roles.md#fixed-database-roles)」を参照してください。これには、固定データベースロールの一覧と、それに対応する権限が表示されます。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_dbfixedrolepermission [ [ @rolename = ] 'role' ]  
```  
  
## <a name="arguments"></a>引数  
`[ @rolename = ] 'role'`有効な[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]固定データベースロールの名前を指定します。 *role*の部分は**sysname**で、既定値は NULL です。 *Role*が指定されていない場合は、すべての固定データベースロールの権限が表示されます。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|**DbFixedRole**|**sysname**|固定データベース ロールの名前。|  
|**権限**|**nvarchar (70)**|**Dbfixedrole**に関連付けられている権限|  
  
## <a name="remarks"></a>解説  
 固定データベースロールの一覧を表示するには、 **sp_helpdbfixedrole**を実行します。 次の表は、固定データベースロールを示しています。  
  
|固定データベースロール|説明|  
|-------------------------|-----------------|  
|**db_owner**|データベース所有者|  
|**db_accessadmin**|データベース アクセス管理者|  
|**db_securityadmin**|データベースセキュリティ管理者|  
|**db_ddladmin**|データベース データ定義言語 (DDL) 管理者|  
|**db_backupoperator**|データベースバックアップオペレーター|  
|**db_datareader**|データベースデータリーダー|  
|**db_datawriter**|データベースデータライター|  
|**db_denydatareader**|データベース否定データ リーダー|  
|**db_denydatawriter**|データベース拒否データライター|  
  
 **Db_owner**固定データベースロールのメンバーは、他のすべての固定データベースロールの権限を持っています。 固定サーバーロールの権限を表示するには、 **sp_srvrolepermission**を実行します。  
  
 結果セットには、 [!INCLUDE[tsql](../../includes/tsql-md.md)]実行可能なステートメントと、データベースロールのメンバーによって実行可能なその他の特別な操作が含まれます。  
  
## <a name="permissions"></a>アクセス許可  
 **Public**ロールのメンバーシップが必要です。  
  
## <a name="examples"></a>例  
 次のクエリでは、固定データベースロールが指定されていないため、すべての固定データベースロールの権限が返されます。  
  
```  
EXEC sp_dbfixedrolepermission;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [セキュリティストアドプロシージャ &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sp_addrolemember &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md)   
 [sp_droprolemember &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-droprolemember-transact-sql.md)   
 [sp_helpdbfixedrole &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-helpdbfixedrole-transact-sql.md)   
 [sp_srvrolepermission &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-srvrolepermission-transact-sql.md)   
 [システムストアドプロシージャ &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
