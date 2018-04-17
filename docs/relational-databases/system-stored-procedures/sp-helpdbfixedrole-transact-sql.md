---
title: sp_helpdbfixedrole (TRANSACT-SQL) |Microsoft ドキュメント
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
- sp_helpdbfixedrole
- sp_helpdbfixedrole_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helpdbfixedrole
ms.assetid: ad87e9a0-b901-4e37-9950-aa517d680fc3
caps.latest.revision: 24
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b9af0e927d21123d01d68da514f479d599cebd6d
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="sphelpdbfixedrole-transact-sql"></a>sp_helpdbfixedrole (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  固定データベース ロールの一覧を返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_helpdbfixedrole [ [ @rolename = ] 'role' ]   
```  
  
## <a name="arguments"></a>引数  
 [  **@rolename =** ] **'***ロール***'**  
 固定データベース ロールの名前を指定します。 *ロール*は**sysname**、既定値は NULL です。 場合*ロール*が指定すると、そのロールに関する情報のみが返されます。 それ以外の場合、リストとすべての固定データベース ロールの説明が返されます。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**DbFixedRole**|**sysname**|固定データベース ロールの名前です。|  
|**Description**|**nvarchar (70)**|説明**DbFixedRole です。**|  
  
## <a name="remarks"></a>解説  
 次の表に示すように、固定データベース ロールはデータベース レベルで定義され、特定のデータベース レベルの管理操作を実行する権限が与えられています。 固定データベース ロールは、追加または削除できません。 固定データベース ロールに許可されている権限は変更できません。  
  
|固定データベース ロール|Description|  
|-------------------------|-----------------|  
|**db_owner**|データベース所有者|  
|**db_accessadmin**|データベース アクセス管理者|  
|**db_securityadmin**|データベース セキュリティ管理者|  
|**db_ddladmin**|データベース DDL 管理者|  
|**db_backupoperator**|データベース バックアップ オペレーター|  
|**db_datareader**|データベース データ リーダー|  
|**db_datawriter**|データベース データ ライター|  
|**db_denydatareader**|データベース否定データ リーダー|  
|**db_denydatawriter**|データベース否定データ ライター|  
  
 次の表は、データベース ロールを変更するときに使用するストアド プロシージャです。  
  
|ストアド プロシージャ|操作|  
|----------------------|------------|  
|**sp_addrolemember**|固定データベース ロールにデータベース ユーザーを追加します。|  
|**sp_helprole**|固定データベース ロールのメンバーの一覧を表示します。|  
|**sp_droprolemember**|固定データベース ロールからメンバーを削除します。|  
  
## <a name="permissions"></a>権限  
 ロール **public** のメンバーシップが必要です。  
  
 返される情報は、メタデータへのアクセスに関する制限の対象となります。 プリンシパルに権限がないエンティティは表示されません。 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="examples"></a>使用例  
 次の例では、すべての固定データベース ロールの一覧を表示します。  
  
```  
EXEC sp_helpdbfixedrole;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [セキュリティ ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sp_addrolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md)   
 [sp_dbfixedrolepermission &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dbfixedrolepermission-transact-sql.md)   
 [sp_droprolemember & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-droprolemember-transact-sql.md)   
 [sp_helprole &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helprole-transact-sql.md)   
 [sp_helprolemember &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helprolemember-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
