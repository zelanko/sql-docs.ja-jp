---
title: sp_dropanonymousagent (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_dropanonymousagent
- sp_dropanonymousagent_TSQL
helpviewer_keywords:
- sp_dropanonymousagent
ms.assetid: 4cb96efa-9358-44a3-a8ee-a7e181bed089
ms.author: vanto
author: VanMSFT
ms.openlocfilehash: 7e82023ed750c77d87a2536debfb5fceb7321db4
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67911951"
---
# <a name="sp_dropanonymousagent-transact-sql"></a>sp_dropanonymousagent (Transact-sql)

[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ディストリビューター側のレプリケーション監視用の匿名エージェントをパブリッシャーから削除します。 このストアドプロシージャは、パブリッシャー側で任意のデータベースに対して実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
sp_dropanonymousagent [ @subid= ] sub_id    , [ @type= ] type  
```  
  
## <a name="arguments"></a>引数  
`[ @subid = ] sub_id`匿名サブスクリプションのグローバル識別子を示します。 *sub_id*は**uniqueidentifier**,、既定値はありません。 この識別子は**sp_helppullsubscription**を使用してサブスクライバーで取得できます。 返された結果セットの**subid**フィールドの値は、このグローバル識別子です。  
  
`[ @type = ] type`サブスクリプションの種類を示します。 *型*は**int**,、既定値はありません。 有効な値は**1**または**2**です。 スナップショットレプリケーションまたはディストリビューションエージェントを使用したトランザクションレプリケーションの場合は、 **1**を指定します。 マージエージェントを使用したマージレプリケーションの場合は、 **2**を指定します。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_dropanonymousagent**は、すべての種類のレプリケーションで使用されます。  
  
 このストアドプロシージャは、匿名サブスクリプションエージェントのみを削除するために使用され、既知のサブスクリプションを削除するためには使用できません。  
  
## <a name="permissions"></a>アクセス許可  
 **Sp_dropanonymousagent**を実行できるのは、ディストリビューションデータベースの**db_owner**固定データベースロールのメンバーだけです。  
  
## <a name="see-also"></a>参照  
 [レプリケーションストアドプロシージャ &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
