---
title: sp_enum_proxy_for_subsystem (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_enum_proxy_for_subsystem_TSQL
- sp_enum_proxy_for_subsystem
dev_langs:
- TSQL
helpviewer_keywords:
- sp_enum_proxy_for_subsystems
ms.assetid: 580cc3be-1068-4a96-8d15-78ca3a5bb719
ms.author: vanto
manager: craigg
ms.openlocfilehash: 53ab72a592ca0d99bf9e19d68a886de8c1e091db
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43030858"
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
 [ **@proxy_id** =] *proxy_id*  
 情報を一覧表示するプロキシの識別番号を指定します。 *Proxy_id*は**int**、既定値は NULL です。 いずれか、 *id*または*proxy_name*指定することがあります。  
  
 [ **@proxy_name** =] **'***proxy_name***'**  
 情報を一覧表示するプロキシの名前を指定します。 *Proxy_name*は**sysname**、既定値は NULL です。 いずれか、 *id*または*proxy_name*指定することがあります。  
  
 [ **@subsystem_id** =] *subsystem_id*  
 情報を一覧表示するサブシステムの識別番号を指定します。 *Subsystem_id*は**int**、既定値は NULL です。 いずれか、 *subsystem_id*または*subsystem_name*指定することがあります。  
  
 [ **@subsystem_name** =] **'***subsystem_name***'**  
 情報を一覧表示するサブシステムの名前を指定します。 *Subsystem_name*は**sysname**、既定値は NULL です。 いずれか、 *subsystem_id*または*subsystem_name*指定することがあります。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**subsystem_id**|**int**|サブシステムの識別番号|  
|**subsystem_name**|**sysname**|サブシステムの名前です。|  
|**proxy_id**|**int**|プロキシの識別番号|  
|**proxy_name**|**sysname**|プロキシの名前|  
  
## <a name="remarks"></a>コメント  
 パラメーターが指定されていないときに**sp_enum_proxy_for_subsystem**各サブシステムのインスタンス内のすべてのプロキシに関する情報を一覧表示します。  
  
 プロキシ id またはプロキシ名を指定する、 **sp_enum_proxy_for_subsystem**へのアクセスをプロキシ リスト サブシステム。 サブシステム id またはサブシステム名を指定する、 **sp_enum_proxy_for_subsystem**そのサブシステムにアクセスできるプロキシが一覧表示されます。  
  
 プロキシ情報とサブシステム情報の両方を指定した場合、結果セットでは、指定のプロキシが指定のサブシステムにアクセスできる場合に 1 行のデータが返されます。  
  
 このストアド プロシージャにある**msdb**します。  
  
## <a name="permissions"></a>アクセス許可  
 このプロシージャの既定のメンバーへのアクセス許可を実行、 **sysadmin**固定サーバー ロール。  
  
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
 場合、次の例は、行を返しますプロキシ`Catalog application proxy`にアクセスする、`ActiveScripting`サブシステム。 それ以外の場合は空の結果セットが返されます。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_enum_proxy_for_subsystem  
    @subsystem_name = 'ActiveScripting',  
    @proxy_name = 'Catalog application proxy' ;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [sp_grant_proxy_to_subsystem &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-grant-proxy-to-subsystem-transact-sql.md)  
  
  
