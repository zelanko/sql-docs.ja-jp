---
title: "sp_enum_proxy_for_subsystem (TRANSACT-SQL) |Microsoft ドキュメント"
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
- sp_enum_proxy_for_subsystem_TSQL
- sp_enum_proxy_for_subsystem
dev_langs: TSQL
helpviewer_keywords: sp_enum_proxy_for_subsystems
ms.assetid: 580cc3be-1068-4a96-8d15-78ca3a5bb719
caps.latest.revision: "27"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0b708d467cf246a221d14802abb839c96de85ffe
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2017
---
# <a name="spenumproxyforsubsystem-transact-sql"></a>sp_enum_proxy_for_subsystem (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント プロキシがサブシステムにアクセスするための権限を一覧表示します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_enum_proxy_for_subsystem  
    [ @proxy_id = ] proxy_id,  
    [ @proxy_name = ] 'proxy_name',  
    [ @subsystem_id = ] subsystem_id,  
    [ @subsystem_name = ] 'subsystem_name'  
```  
  
## <a name="arguments"></a>引数  
 [  **@proxy_id**  =] *proxy_id*  
 情報を一覧表示するプロキシの識別番号を指定します。 *Proxy_id*は**int**、既定値は NULL です。 いずれか、 *id*または*proxy_name*指定することがあります。  
  
 [  **@proxy_name**  =] **'***proxy_name***'**  
 情報を一覧表示するプロキシの名前を指定します。 *Proxy_name*は**sysname**、既定値は NULL です。 いずれか、 *id*または*proxy_name*指定することがあります。  
  
 [  **@subsystem_id**  =] *subsystem_id*  
 情報を一覧表示するサブシステムの識別番号を指定します。 *Subsystem_id*は**int**、既定値は NULL です。 いずれか、 *subsystem_id*または*subsystem_name*指定することがあります。  
  
 [  **@subsystem_name**  =] **'***subsystem_name***'**  
 情報を一覧表示するサブシステムの名前を指定します。 *Subsystem_name*は**sysname**、既定値は NULL です。 いずれか、 *subsystem_id*または*subsystem_name*指定することがあります。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**subsystem_id**|**int**|サブシステムの識別番号|  
|**subsystem_name**|**sysname**|サブシステムの名前です。|  
|**proxy_id**|**int**|プロキシの識別番号|  
|**proxy_name**|**sysname**|プロキシの名前|  
  
## <a name="remarks"></a>解説  
 パラメーターが指定されていないときに**sp_enum_proxy_for_subsystem**各サブシステムのインスタンスのすべてのプロキシに関する情報を表示します。  
  
 プロキシ id またはプロキシ名を指定した場合、 **sp_enum_proxy_for_subsystem**にプロキシが一覧のサブシステムにアクセスします。 サブシステム id またはサブシステム名を指定した場合、 **sp_enum_proxy_for_subsystem**そのサブシステムにアクセスできるプロキシが一覧表示します。  
  
 プロキシ情報とサブシステム情報の両方を指定した場合、結果セットでは、指定のプロキシが指定のサブシステムにアクセスできる場合に 1 行のデータが返されます。  
  
 このストアド プロシージャにある**msdb**です。  
  
## <a name="permissions"></a>Permissions  
 メンバーにこのプロシージャの既定の実行のアクセス許可、 **sysadmin**固定サーバー ロール。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-listing-all-associations"></a>A. すべての関連付けを一覧表示する  
 次の例では、現在のインスタンスに対し、プロキシとサブシステムの間に確立されているすべての権限を一覧表示します。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_enum_proxy_for_subsystem ;  
GO  
```  
  
### <a name="b-determining-if-a-proxy-has-access-to-a-specific-subsystem"></a>B. プロキシが特定のサブシステムにアクセスできるかどうかを確認する  
 場合、次の例は、行を返しますプロキシ`Catalog application proxy`へのアクセスを持つ、`ActiveScripting`サブシステムです。 それ以外の場合は空の結果セットが返されます。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_enum_proxy_for_subsystem  
    @subsystem_name = 'ActiveScripting',  
    @proxy_name = 'Catalog application proxy' ;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [sp_grant_proxy_to_subsystem &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-grant-proxy-to-subsystem-transact-sql.md)  
  
  
