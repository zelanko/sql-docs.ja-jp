---
title: "sp_dropdistpublisher (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
f1_keywords:
- sp_dropdistpublisher
- sp_dropdistpublisher_TSQL
helpviewer_keywords: sp_dropdistpublisher
ms.assetid: c0bdd3de-3be0-455c-898a-98d4660e7ce3
caps.latest.revision: "29"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8060e5788004b743e58e0d0d424dcc0910459573
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="spdropdistpublisher-transact-sql"></a>sp_dropdistpublisher (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ディストリビューション パブリッシャーを削除します。 このストアド プロシージャは、ディストリビューター側で任意のデータベースについて実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_dropdistpublisher [ @publisher = ] 'publisher'  
    [ , [ @no_checks = ] no_checks ]  
    [ , [ @ignore_distributor = ] ignore_distributor ]  
```  
  
## <a name="arguments"></a>引数  
 [  **@publisher=** ] **'***パブリッシャー***'**  
 削除するパブリッシャーを指定します。 *パブリッシャー*は**sysname**、既定値はありません。  
  
 [  **@no_checks=** ] *no_checks*  
 指定するかどうか**sp_dropdistpublisher**パブリッシャーがディストリビューターとしてサーバーをアンインストールしたことを確認します。 *no_checks*は**ビット**、既定値は**0**します。  
  
 場合**0**レプリケーションでは、リモート パブリッシャーがディストリビューターとしてローカル サーバーをアンインストールしたことを確認します。 パブリッシャーがローカルの場合、レプリケーションでは、ローカル サーバーにパブリケーションまたはディストリビューション オブジェクトが残っていないことが確認されます。  
  
 場合**1**、リモート パブリッシャーに到達できない場合でも、ディストリビューション パブリッシャーに関連付けられているすべてのレプリケーション オブジェクトは削除されます。 レプリケーションを使用してこれを行うリモート パブリッシャーをアンインストールする必要があります[sp_dropdistributor](../../relational-databases/system-stored-procedures/sp-dropdistributor-transact-sql.md)で **@ignore_distributor**   =  **1**です。  
  
 [  **@ignore_distributor=** ] *ignore_distributor*  
 パブリッシャーが削除されるとき、ディストリビューターにディストリビューション オブジェクトを残すかどうかを指定します。 *ignore_distributor*は**ビット**これらの値のいずれかを指定できます。  
  
 **1**に属するディストリビューション オブジェクトが =、*パブリッシャー*がディストリビューターに残ります。  
  
 **0**ディストリビューション オブジェクトが =、*パブリッシャー*は、クリーンアップ、ディストリビューター側でします。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_dropdistpublisher**はあらゆる種類のレプリケーションで使用します。  
  
 パブリッシャーを削除できない場合は、Oracle パブリッシャーを削除するときに**sp_dropdistpublisher**エラーと、パブリッシャーのディストリビューター オブジェクトが削除されて返されます。  
  
## <a name="example"></a>例  
 [!code-sql[HowTo#sp_DropDistPub](../../relational-databases/replication/codesnippet/tsql/sp-dropdistpublisher-tra_1.sql)]  
  
## <a name="permissions"></a>Permissions  
 メンバーにのみ、 **sysadmin**固定サーバー ロールが実行できる**sp_dropdistpublisher**です。  
  
## <a name="see-also"></a>参照  
 [パブリッシングおよびディストリビューションの無効化](../../relational-databases/replication/disable-publishing-and-distribution.md)   
 [sp_adddistpublisher &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql.md)   
 [sp_changedistpublisher (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-changedistpublisher-transact-sql.md)   
 [sp_helpdistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpdistpublisher-transact-sql.md)   
 [レプリケーション ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
