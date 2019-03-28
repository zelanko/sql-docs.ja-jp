---
title: sp_dropdistpublisher (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_dropdistpublisher
- sp_dropdistpublisher_TSQL
helpviewer_keywords:
- sp_dropdistpublisher
ms.assetid: c0bdd3de-3be0-455c-898a-98d4660e7ce3
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 8acc73e057ff8b91987406e74a28563fecfc9278
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2019
ms.locfileid: "58526454"
---
# <a name="spdropdistpublisher-transact-sql"></a>sp_dropdistpublisher (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ディストリビューション パブリッシャーを削除します。 このストアド プロシージャは、ディストリビューターのすべてのデータベースで実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_dropdistpublisher [ @publisher = ] 'publisher'  
    [ , [ @no_checks = ] no_checks ]  
    [ , [ @ignore_distributor = ] ignore_distributor ]  
```  
  
## <a name="arguments"></a>引数  
`[ @publisher = ] 'publisher'` 削除するパブリッシャーです。 *パブリッシャー* は **sysname** 、既定値はありません。  
  
`[ @no_checks = ] no_checks` 指定するかどうか**sp_dropdistpublisher**パブリッシャーがディストリビューターとしてサーバーをアンインストールしたことを確認します。 *no_checks*は**ビット**、既定値は**0**します。  
  
 場合**0**レプリケーションでは、リモート パブリッシャーがディストリビューターとしてローカル サーバーをアンインストールしたことが確認されます。 パブリッシャーがローカルの場合は、レプリケーションでは、ローカル サーバーに残っているパブリケーションまたはディストリビューション オブジェクトがないことが確認されます。  
  
 場合**1**、リモート パブリッシャーに到達できない場合でも、ディストリビューション パブリッシャーに関連付けられているすべてのレプリケーション オブジェクトが削除されます。 レプリケーションを使用してこれを行うリモート パブリッシャーをアンインストールする必要があります[sp_dropdistributor](../../relational-databases/system-stored-procedures/sp-dropdistributor-transact-sql.md)で**@ignore_distributor**  =  **1**します。  
  
`[ @ignore_distributor = ] ignore_distributor` パブリッシャーが削除されるときに、ディストリビューターでディストリビューション オブジェクトを残すかどうかを指定します。 *ignore_distributor*は**ビット**これらの値のいずれかを指定できます。  
  
 **1**に属するディストリビューション オブジェクトが =、*パブリッシャー*がディストリビューターに残ります。  
  
 **0**ディストリビューション オブジェクトが =、*パブリッシャー*がクリーンアップ、ディストリビューター側でします。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>コメント  
 **sp_dropdistpublisher**はあらゆる種類のレプリケーションで使用します。  
  
 パブリッシャーを削除できない場合は、Oracle パブリッシャーを削除するときに**sp_dropdistpublisher**返しますエラーとパブリッシャーのディストリビューター オブジェクトが削除されます。  
  
## <a name="example"></a>例  
 [!code-sql[HowTo#sp_DropDistPub](../../relational-databases/replication/codesnippet/tsql/sp-dropdistpublisher-tra_1.sql)]  
  
## <a name="permissions"></a>アクセス許可  
 メンバーのみ、 **sysadmin**固定サーバー ロールが実行できる**sp_dropdistpublisher**します。  
  
## <a name="see-also"></a>参照  
 [パブリッシングおよびディストリビューションの無効化](../../relational-databases/replication/disable-publishing-and-distribution.md)   
 [sp_adddistpublisher &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql.md)   
 [sp_changedistpublisher (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-changedistpublisher-transact-sql.md)   
 [sp_helpdistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpdistpublisher-transact-sql.md)   
 [レプリケーション ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
