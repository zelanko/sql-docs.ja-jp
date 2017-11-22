---
title: "sp_help_category (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/09/2016
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
- sp_help_category
- sp_help_category_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_help_category
ms.assetid: 8cad1dcc-b43e-43bd-bea0-cb0055c84169
caps.latest.revision: "18"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: efec4c1ef04ef95e74ef13479b5f51cfe2d84bdb
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
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
 [  **@class=**] **'***クラス***'**  
 要求する情報のクラスを指定します。 *クラス*は**varchar (8)**、既定値は**ジョブ**です。 *クラス*これらの値のいずれかになります。  
  
|値|Description|  
|-----------|-----------------|  
|**ジョブ**|ジョブ カテゴリに関する情報|  
|**アラートを生成します。**|警告カテゴリに関する情報|  
|**演算子**|オペレーター カテゴリに関する情報|  
  
 [  **@type=** ] **'***型***'**  
 要求する情報に関するカテゴリの種類を指定します。 *型*は**varchar (12)**、既定値は NULL、これらの値のいずれかを指定できます。  
  
|値|Description|  
|-----------|-----------------|  
|**地元の**|ローカル ジョブ カテゴリです。|  
|**複数のサーバー**|マルチ サーバー ジョブ カテゴリです。|  
|**NONE**|以外のクラスのカテゴリ**ジョブ**です。|  
  
 [  **@name=** ] **'***名前***'**  
 要求する情報に関するカテゴリの名前を指定します。 *名前*は**sysname**、既定値は NULL です。  
  
 [  **@suffix=** ]*サフィックス*  
 指定するかどうか、 **category_type**結果セット内の列が ID と名前。 *サフィックス*は**ビット**、既定値は**0**します。 **1**を示しています、 **category_type** 、名、および**0** ID として表示  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="result-sets"></a>結果セット  
 ときに **@suffix** は**0**、 **sp_help_category**次の結果セットを返します。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**category_id**|**int**|カテゴリ ID。|  
|**category_type**|**tinyint**|カテゴリの種類です。<br /><br /> **1** = ローカル<br /><br /> **2** = マルチ サーバー<br /><br /> **3** = なし|  
|**name**|**sysname**|カテゴリ名。|  
  
 ときに **@suffix** は**1**、 **sp_help_category**次の結果セットを返します。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**category_id**|**int**|カテゴリ ID。|  
|**category_type**|**sysname**|カテゴリの種類。 いずれかの**ローカル**、 **MULTI-SERVER**、または**NONE**|  
|**name**|**sysname**|カテゴリ名。|  
  
## <a name="remarks"></a>解説  
 **sp_help_category**から実行する必要があります、 **msdb**データベース。  
  
 パラメーターを指定しない場合、結果セットではすべてのジョブ カテゴリに関する情報が提供されます。  
  
## <a name="permissions"></a>Permissions  
 既定では、このストアド プロシージャを実行できるのは、 **sysadmin** 固定サーバー ロールのメンバーです。 他のユーザーには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] msdb **データベースの次のいずれかの** エージェント固定データベース ロールが許可されている必要があります。  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 これらのロールの権限の詳細については、「 [SQL Server エージェントの固定データベース ロール](http://msdn.microsoft.com/library/719ce56b-d6b2-414a-88a8-f43b725ebc79)」を参照してください。  
  
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
  
### <a name="b-returning-alert-information"></a>B. 警告情報を返す  
 次の例では、レプリケーション警告カテゴリに関する情報を返します。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_category  
    @class = N'ALERT',  
    @name = N'Replication' ;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [sp_add_category &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-add-category-transact-sql.md)   
 [sp_delete_category &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-delete-category-transact-sql.md)   
 [sp_update_category &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-update-category-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
