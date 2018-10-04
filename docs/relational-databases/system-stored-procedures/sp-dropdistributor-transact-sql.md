---
title: sp_dropdistributor (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- sp_dropdistributor
- sp_dropdistributor_TSQL
helpviewer_keywords:
- sp_dropdistributor
ms.assetid: 0644032f-5ff0-4718-8dde-321bc9967a03
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 8dc9ea8dfbe20ddae5e67607da545e1abe1bcbec
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47700510"
---
# <a name="spdropdistributor-transact-sql"></a>sp_dropdistributor (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ディストリビューターをアンインストールします。 このストアド プロシージャは、ディストリビューター側でディストリビューション データベースを除くすべてのデータベースについて実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_dropdistributor [ [ @no_checks= ] no_checks ]   
    [ , [ @ignore_distributor= ] ignore_distributor ]  
```  
  
## <a name="arguments"></a>引数  
 [  **@no_checks=**] *no_checks*  
 ディストリビューターを削除する前に、従属オブジェクトを確認するかどうかを指定します。 *no_checks*は**ビット**、既定値は 0。  
  
 場合**0**、 **sp_dropdistributor**ディストリビューター以外のすべてのパブリッシングおよびディストリビューション オブジェクトが破棄されたことを確認します。  
  
 場合**1**、 **sp_dropdistributor**ディストリビューターをアンインストールする前にすべてのパブリッシングおよびディストリビューション オブジェクトを削除します。  
  
 [  **@ignore_distributor=**] *ignore_distributor*  
 ディストリビューターに接続せずに、このストアド プロシージャを実行するかどうかを指定します。 *ignore_distributor*は**ビット**、既定値は**0**します。  
  
 場合**0**、 **sp_dropdistributor**ディストリビューターに接続して、すべてのレプリケーション オブジェクトを削除します。 場合**sp_dropdistributor**は、ストアド プロシージャは失敗、ディストリビューターに接続できません。  
  
 場合**1**ディストリビューターに接続が確立されませんし、レプリケーション オブジェクトは削除されません。 これが使用されるのは、ディストリビューターがアンインストールされているか、完全にオフラインになっている場合です。 ディストリビューターでのパブリッシャーに関連するオブジェクトは、後でディストリビューターが再インストールされるまで削除されません。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>コメント  
 **sp_dropdistributor**はあらゆる種類のレプリケーションで使用します。  
  
 サーバーで、その他のパブリッシャーまたはディストリビューション オブジェクトが存在しない場合**sp_dropdistributor**失敗しない限り、 **@no_checks**に設定されている**1**します。  
  
 実行して、ディストリビューション データベースを削除した後、このストアド プロシージャを実行する必要があります**sp_dropdistributiondb**します。  
  
## <a name="example"></a>例  
 [!code-sql[HowTo#sp_DropDistPub](../../relational-databases/replication/codesnippet/tsql/sp-dropdistributor-trans_1.sql)]  
  
## <a name="permissions"></a>アクセス許可  
 メンバーのみ、 **sysadmin**固定サーバー ロールが実行できる**sp_dropdistributor**します。  
  
## <a name="see-also"></a>参照  
 [パブリッシングおよびディストリビューションの無効化](../../relational-databases/replication/disable-publishing-and-distribution.md)   
 [sp_adddistributor &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-adddistributor-transact-sql.md)   
 [sp_changedistributor_property &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changedistributor-property-transact-sql.md)   
 [sp_helpdistributor &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpdistributor-transact-sql.md)   
 [レプリケーション ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
