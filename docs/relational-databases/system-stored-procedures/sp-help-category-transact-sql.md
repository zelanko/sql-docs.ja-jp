---
title: sp_help_category (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_category
- sp_help_category_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_category
ms.assetid: 8cad1dcc-b43e-43bd-bea0-cb0055c84169
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 69f65ee2e299197504c4bd970a835a28c2f89b21
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2019
ms.locfileid: "58534144"
---
# <a name="sphelpcategory-transact-sql"></a>sp_help_category (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ジョブ、警告、またはオペレーターについて、指定されたクラスの情報を提供します。  
   
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_help_category [ [ @class = ] 'class' ]   
     [ , [ @type = ] 'type' ]   
     [ , [ @name = ] 'name' ]   
     [ , [ @suffix = ] suffix ]   
```  
  
## <a name="arguments"></a>引数  
`[ @class = ] 'class'` に関する情報が要求されたクラスです。 *クラス*は**varchar (8)** の既定値を持つ**ジョブ**します。 *クラス*これらの値のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**JOB**|ジョブ カテゴリに関する情報を提供します。|  
|**アラートを生成します。**|警告カテゴリに関する情報を提供します。|  
|**演算子**|オペレーター カテゴリに関する情報|  
  
`[ @type = ] 'type'` 情報を要求する対象のカテゴリの種類。 *型*は**varchar (12)**、既定値は null の場合、これらの値のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**LOCAL**|ローカル ジョブ カテゴリ。|  
|**複数のサーバー**|マルチ サーバー ジョブ カテゴリ。|  
|**NONE**|以外のクラスのカテゴリ**ジョブ**します。|  
  
`[ @name = ] 'name'` 情報を要求する対象のカテゴリの名前。 *名前* は **sysname** 、既定値は NULL です。  
  
`[ @suffix = ] suffix` 指定するかどうか、 **category_type**結果セット内の列が ID と名前。 *サフィックス*は**ビット**、既定値は**0**します。 **1**を示しています、 **category_type** 、名前と、 **0** ID として表示します。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="result-sets"></a>結果セット  
 ときに**@suffix**は**0**、 **sp_help_category**次の結果セットを返します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**category_id**|**int**|カテゴリ ID。|  
|**category_type**|**tinyint**|カテゴリの種類:<br /><br /> **1** = ローカル<br /><br /> **2** = マルチ サーバー<br /><br /> **3** = なし|  
|**name**|**sysname**|カテゴリ名|  
  
 ときに**@suffix**は**1**、 **sp_help_category**次の結果セットを返します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**category_id**|**int**|カテゴリ ID。|  
|**category_type**|**sysname**|カテゴリの種類。 いずれかの**ローカル**、 **MULTI-SERVER**、または**NONE**|  
|**name**|**sysname**|カテゴリ名|  
  
## <a name="remarks"></a>コメント  
 **sp_help_category**から実行する必要があります、 **msdb**データベース。  
  
 パラメーターを指定しない場合、結果セットではすべてのジョブ カテゴリに関する情報が提供されます。  
  
## <a name="permissions"></a>アクセス許可  
 既定では、このストアド プロシージャを実行できるのは、 **sysadmin** 固定サーバー ロールのメンバーです。 他のユーザーには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] msdb **データベースの次のいずれかの** エージェント固定データベース ロールが許可されている必要があります。  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 これらのロールの権限の詳細については、「 [SQL Server エージェントの固定データベース ロール](../../ssms/agent/sql-server-agent-fixed-database-roles.md)」を参照してください。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-returning-local-job-information"></a>A. ローカル ジョブ情報を返す  
 次の例では、ローカルで管理されるジョブに関する情報を返します。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_category  
    @type = N'LOCAL' ;  
GO  
```  
  
### <a name="b-returning-alert-information"></a>B. アラートの情報を返す  
 次の例では、レプリケーションの警告カテゴリに関する情報を返します。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_category  
    @class = N'ALERT',  
    @name = N'Replication' ;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [sp_add_category &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-category-transact-sql.md)   
 [sp_delete_category &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-category-transact-sql.md)   
 [sp_update_category &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-category-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
